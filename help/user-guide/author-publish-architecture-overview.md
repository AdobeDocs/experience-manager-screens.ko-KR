---
title: 아키텍처 개요 작성 및 게시
seo-title: Author and Publish Architectural Overview
description: AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 콘텐츠는 AEM 작성자 인스턴스에 작성된 다음 여러 게시 인스턴스에 정방향 복제됩니다. 이 페이지를 따라 아키텍처 개요 작성 및 게시에 대해 자세히 알아보십시오.
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn more on author and publish architectural overview.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# 아키텍처 개요 작성 및 게시 {#author-and-publish-architectural-overview}

이 페이지에서는 다음 항목을 강조합니다.

* **게시 서버 소개**
* **아키텍처 개요**
* **등록 프로세스**

## 사전 요구 사항 {#prerequisites}

작성자 및 게시 서버를 시작하기 전에 다음 사항에 대한 사전 지식이 있어야 합니다.

* **AEM 토폴로지**
* **AEM Screens 프로젝트 만들기 및 관리**
* **장치 등록 프로세스**

>[!NOTE]
>
>이 AEM Screens 기능은 AEM 6.4 Screens 기능 팩 2를 설치한 경우에만 사용할 수 있습니다. 이 기능 팩에 액세스하려면 Adobe 지원에 문의하고 액세스를 요청해야 합니다. 권한이 있으면 패키지 공유에서 다운로드할 수 있습니다.

## 소개 {#introduction}

AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 콘텐츠는 AEM 작성자 인스턴스에 작성된 다음 여러 게시 인스턴스에 정방향 복제됩니다. 이제 AEM Screens 장치는 로드 밸런서를 통해 AEM 게시 팜에 연결할 수 있습니다. 여러 AEM 게시 인스턴스를 추가하여 게시 팜의 크기를 계속 조정할 수 있습니다.

*예*, AEM Screens 콘텐츠 작성자는 게시 팜과 상호 작용하도록 구성된 특정 장치용 작성 시스템에서 명령을 발행하거나 게시 팜과 상호 작용하도록 구성된 장치에 대한 정보를 가져오는 AEM Screens 콘텐츠 작성자입니다.

다음 다이어그램은 작성자 및 게시 환경을 보여 줍니다.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 건축 설계 {#architectural-design}

5가지 아키텍처 구성 요소가 있어 이 솔루션을 용이하게 합니다.

* ***콘텐츠 복제*** 작성자에서 게시로 장치 표시

* ***Reverse*** 게시에서(장치에서 수신) 작성자로 바이너리 콘텐츠 복제
* ***전송 중*** 특정 REST API를 통해 작성자에서 게시로의 명령
* ***메시징*** 게시 인스턴스 간에 장치 정보 업데이트 및 명령을 동기화합니다.
* ***폴링*** 게시 인스턴스의 작성자가 특정 REST API를 통해 장치 정보를 얻는 방법

### 컨텐츠 및 구성의 복제(전달)  {#replication-forward-of-content-and-configurations}

표준 복제 에이전트는 화면 채널 콘텐츠, 위치 구성 및 장치 구성을 복제하는 데 사용됩니다. 이를 통해 작성자는 채널 콘텐츠를 업데이트할 수 있으며 채널 업데이트를 게시하기 전에 선택적으로 일종의 승인 작업 과정을 거칠 수 있습니다. 게시 팜의 각 게시 인스턴스에 대해 복제 에이전트를 만들어야 합니다.

다음 다이어그램은 복제 프로세스를 보여 줍니다.

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>게시 팜의 각 게시 인스턴스에 대해 복제 에이전트를 만들어야 합니다.

### 화면 복제 에이전트 및 명령  {#screens-replication-agents-and-commands}

사용자 정의 화면 특정 복제 에이전트는 작성자 인스턴스에서 AEM Screens 장치로 명령을 전송하기 위해 만들어집니다. AEM Publish 인스턴스는 이러한 명령을 장치에 전달하는 중간 역할을 합니다.

이를 통해 작성자는 계속해서 디바이스를 관리할 수 있습니다. 예를 들어, 디바이스 업데이트를 전송하고 작성자 환경에서 스크린샷을 찍을 수 있습니다. AEM Screens 복제 에이전트에는 표준 복제 에이전트와 같은 사용자 지정 전송 구성이 있습니다.

### 게시 인스턴스 간 메시징  {#messaging-between-publish-instances}

대부분의 경우 명령은 한 번만 장치에 전송됩니다. 그러나 부하 분산 게시 아키텍처에서는 디바이스가 연결 중인 게시 인스턴스를 알 수 없습니다.

따라서 작성자 인스턴스는 모든 게시 인스턴스로 메시지를 보냅니다. 단, 단일 메시지만 장치에 전달되어야 합니다. 올바른 메시징을 위해 게시 인스턴스 간에 일부 통신이 수행되어야 합니다. 이 작업은 다음을 사용하여 수행됩니다. *Apache ActiveMQ Artemis*. 각 게시 인스턴스는 Oak 기반 Sling 검색 서비스를 사용하여 느슨하게 연결된 토폴로지에 배치되며 각 게시 인스턴스가 통신하고 단일 메시지 큐를 만들 수 있도록 ActiveMQ가 구성됩니다. Screens 장치는 로드 밸런서를 통해 게시 팜을 폴링하고 큐 맨 위에서 명령을 선택합니다.

### 역방향 복제 {#reverse-replication}

대부분의 경우 명령 다음에 Screens 장치에서 작성자 인스턴스로 전달되는 일종의 응답이 필요합니다. 이 AEM을 달성하려면 ***역방향 복제*** 를 사용합니다.

* 표준 복제 에이전트 및 화면 복제 에이전트와 유사한 각 게시 인스턴스에 대해 역방향 복제 에이전트를 만듭니다.
* 워크플로우 런처 구성은 게시 인스턴스에서 수정된 노드를 수신하고, 그런 다음 게시 인스턴스의 보낼 편지함에 장치의 응답을 배치하는 워크플로우를 트리거합니다.
* 이 컨텍스트의 역방향 복제는 장치에서 제공하는 이진 데이터(예: 로그 파일 및 스크린샷)에만 사용됩니다. 이진이 아닌 데이터는 폴링을 통해 검색됩니다.
* AEM 작성자 인스턴스에서 폴링한 역방향 복제는 응답을 검색하여 작성자 인스턴스에 저장합니다.

### 게시 인스턴스 폴링  {#polling-of-publish-instances}

작성자 인스턴스는 하트비트를 가져오고 연결된 장치의 상태를 알 수 있도록 장치를 폴링할 수 있어야 합니다.

장치가 로드 밸런서를 ping하고 게시 인스턴스로 라우팅됩니다. 그런 다음 제공된 게시 API를 통해 게시 인스턴스에 의해 디바이스의 상태가 표시됩니다. **api/screens-dcc/devices/static** 모든 활성 장치 및 **api/screens-dcc/devices/&lt;device_id>/status.json** 단일 디바이스용

작성자 인스턴스는 모든 게시 인스턴스를 폴링하고 장치 상태 응답을 단일 상태로 병합합니다. 작성자에 대해 폴링하는 예약된 작업은 다음과 같습니다. `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` cron 표현식을 기반으로 를 구성할 수 있습니다.

## 등록 {#registration}

등록은 AEM 작성자 인스턴스에서 계속 시작됩니다. AEM Screens 장치가 작성자 인스턴스를 가리키고 등록이 완료되었습니다.

장치가 작성 환경에 등록되면 장치 구성 및 채널/예약 할당이 AEM 게시 인스턴스에 복제됩니다. 그런 다음 AEM 게시 팜 앞에 있는 로드 밸런서를 가리키도록 AEM Screens 장치 구성이 업데이트됩니다. Screens 장치가 게시 환경에 성공적으로 연결되면 작성자 환경에서 발생하는 명령을 계속 수신할 수 있으며 Screens 장치를 작성자 환경에 직접 연결할 필요가 없다는 것이 일회성 설정인 것입니다.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 다음 단계 {#the-next-steps}

AEM Screens의 작성자 및 게시 설정에 대한 아키텍처 설계를 이해하면 을 참조하십시오. [AEM Screens에 대한 작성자 및 게시 구성](author-and-publish.md) 을 참조하십시오.
