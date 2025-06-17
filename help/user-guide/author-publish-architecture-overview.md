---
title: 아키텍처 개요 작성 및 게시
description: AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 콘텐츠는 AEM 작성자 인스턴스에서 작성된 다음 여러 게시 인스턴스에 정방향 복제됩니다.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# 아키텍처 개요 작성 및 게시 {#author-and-publish-architectural-overview}

이 페이지에서는 다음 항목을 강조합니다.

* **게시 서버 소개**
* **아키텍처 개요**
* **등록 프로세스**

## 사전 요구 사항 {#prerequisites}

작성자 서버 및 게시 서버를 시작하기 전에 다음 사항에 대한 사전 지식을 가지고 있어야 합니다.

* **AEM 토폴로지**
* **AEM Screens 프로젝트 만들기 및 관리**
* **장치 등록 프로세스**

>[!NOTE]
>
>이 AEM Screens 기능은 AEM 6.4 Screens 기능 팩 2를 설치한 경우에만 사용할 수 있습니다. 이 기능 팩에 액세스하려면 Adobe 지원에 문의하고 액세스를 요청하십시오. 권한이 있으면 패키지 공유에서 다운로드합니다.

## 소개 {#introduction}

AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 콘텐츠는 AEM 작성자 인스턴스에서 작성된 다음 여러 게시 인스턴스에 정방향 복제됩니다. 이제 AEM Screens의 장치는 로드 밸런서를 통해 AEM 게시 팜에 연결할 수 있습니다. 여러 AEM 게시 인스턴스를 추가하여 게시 팜의 크기를 계속 조정할 수 있습니다.

*예* AEM Screens 콘텐츠 작성자는 특정 장치의 작성 시스템에서 명령을 실행합니다. 해당 장치는 게시 팜과 상호 작용하도록 구성되어 있습니다. 또는 게시 팜과 상호 작용하도록 구성된 장치에 대한 정보를 얻는 AEM Screens 콘텐츠 작성자와 상호 작용합니다.

다음 다이어그램은 작성 환경과 게시 환경을 모두 보여 줍니다.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 건축 설계 {#architectural-design}

이 솔루션을 지원하는 5가지 아키텍처 구성 요소는 다음과 같습니다.

* 장치에서 표시하기 위해 작성자의 콘텐츠를 ***복제***

* ***장치에서 받은 게시 환경의 이진 콘텐츠를 작성 환경에 복제하는***&#x200B;을(를) 취소합니다.
* 특정 REST API를 통해 작성자가 게시하도록 ***명령을 전송***&#x200B;합니다.
* 장치 정보 업데이트 및 명령을 동기화하기 위해 게시 인스턴스 간에 ***메시징***&#x200B;을(를) 합니다.
* 게시 인스턴스의 작성자가 특정 REST API를 통해 장치 정보를 가져오는 ***폴링***

### 컨텐츠 및 구성의 복제(전달) {#replication-forward-of-content-and-configurations}

표준 복제 에이전트는 AEM Screens 채널 콘텐츠, 위치 구성 및 장치 구성을 복제하는 데 사용됩니다. 이 기능을 사용하면 작성자가 채널의 콘텐츠를 업데이트하고 채널 업데이트를 게시하기 전에 선택적으로 몇 가지 승인 작업 과정을 거칠 수 있습니다. 게시 팜의 각 게시 인스턴스에 대해 복제 에이전트를 만들어야 합니다.

다음 다이어그램은 복제 프로세스를 보여 줍니다.

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>게시 팜의 각 게시 인스턴스에 대해 복제 에이전트를 만들어야 합니다.

### Screens 복제 에이전트 및 명령 {#screens-replication-agents-and-commands}

사용자 지정 Screens 특정 복제 에이전트는 작성자 인스턴스에서 AEM Screens 장치로 명령을 전송하기 위해 만들어집니다. AEM 게시 인스턴스는 이러한 명령을 장치에 전달하는 중간 역할을 합니다.

이 워크플로를 통해 작성자는 계속해서 장치를 관리하고, 장치 업데이트를 전송하고, 작성자 환경에서 스크린샷을 촬영할 수 있습니다. AEM Screens 복제 에이전트에는 표준 복제 에이전트와 같은 사용자 지정 전송 구성이 있습니다.

### 게시 인스턴스 간 메시징 {#messaging-between-publish-instances}

명령은 한 번만 장치에 보내도록 되어 있는 경우가 많습니다. 그러나 부하가 분산된 게시 아키텍처에서는 장치가 연결 중인 게시 인스턴스를 알 수 없습니다.

따라서 작성자 인스턴스는 모든 게시 인스턴스로 메시지를 보냅니다. 단, 단일 메시지만 장치에 전달되어야 합니다. 올바른 메시징을 위해 게시 인스턴스 간에 통신이 수행되어야 합니다. 이 통신은 *Apache ActiveMQ Artemis*&#x200B;을(를) 사용하여 수행됩니다. 각 게시 인스턴스는 Oak 기반 Sling 검색 서비스를 사용하여 느슨하게 연결된 토폴로지에 배치됩니다. ActiveMQ는 각 게시 인스턴스가 통신하고 단일 메시지 큐를 만들 수 있도록 구성되어 있습니다. AEM Screens 장치는 로드 밸런서를 통해 AEM 게시 팜을 폴링하고 큐 맨 위에서 명령을 선택합니다.

### 역방향 복제 {#reverse-replication}

종종 명령 다음에 Screens 디바이스에서 작성자 인스턴스로 전달되는 일종의 응답이 예상됩니다. 이 AEM을 달성하려면 ***역방향 복제***&#x200B;를 사용합니다.

* 표준 복제 에이전트 및 AEM Screens 복제 에이전트와 유사한 각 게시 인스턴스에 대해 역방향 복제 에이전트를 만듭니다.
* 워크플로우 런처 구성은 AEM 게시 인스턴스에서 수정된 노드를 수신하고, 그런 다음 워크플로우를 트리거하여 AEM 게시 인스턴스의 보낼 편지함에 장치의 응답을 배치합니다.
* 이 컨텍스트의 역방향 복제는 장치에서 제공하는 이진 데이터(예: 로그 파일 및 스크린샷)에만 사용됩니다. 이진이 아닌 데이터의 폴링을 검색합니다.
* AEM 작성자 인스턴스의 역방향 복제 폴은 응답을 검색하여 작성자 인스턴스에 저장합니다.

### 게시 인스턴스 폴링 {#polling-of-publish-instances}

작성자 인스턴스는 하트비트를 가져오려면 장치를 폴링하고 연결된 장치의 상태를 알 수 있어야 합니다.

장치가 로드 밸런서를 ping하고 게시 인스턴스로 라우팅됩니다. 그런 다음 모든 활성 장치의 경우 **api/screens-dcc/devices/static**, 단일 장치의 경우 **api/screens-dcc/devices/&lt;device_id>/status.json**&#x200B;에서 제공되는 게시 API를 통해 AEM 게시 인스턴스에 의해 장치의 상태가 표시됩니다.

작성자 인스턴스는 모든 게시 인스턴스를 폴링하고 장치 상태 응답을 단일 상태로 병합합니다. 작성자에게 폴링하는 예약된 작업은 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob`이며 cron 식을 기반으로 구성할 수 있습니다.

## 등록 {#registration}

등록은 AEM 작성자 인스턴스에서 계속 시작됩니다. AEM Screens 장치가 작성자 인스턴스를 가리키고 등록이 완료되었습니다.

장치가 AEM 작성 환경에 등록되면 장치 구성 및 채널/예약 할당이 AEM 게시 인스턴스에 복제됩니다. 그런 다음 AEM Screens 장치 구성이 AEM 게시 팜 앞의 로드 밸런서를 가리키도록 업데이트됩니다. 이 배열은 일회성 설정입니다. Screens 장치가 게시 환경에 성공적으로 연결되면 작성자 환경에서 발생하는 명령을 계속 수신할 수 있습니다. AEM Screens 장치를 AEM 작성 환경에 직접 연결할 필요가 없습니다.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 다음 단계 {#the-next-steps}

AEM Screens의 작성자 및 게시 설정에 대한 아키텍처 설계를 이해하면 [AEM Screens에 대한 작성자 및 게시 구성](author-and-publish.md)을 참조하십시오.
