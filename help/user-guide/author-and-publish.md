---
title: AEM Screens에서 작성자 및 게시 구성
seo-title: AEM Screens에서 작성자 및 게시 구성
description: AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 컨텐츠는 AEM 작성자 인스턴스에서 작성된 다음 여러 게시 인스턴스로 전달됩니다. AEM Screens에 대한 작성자 및 게시 구성 방법을 알려면 이 페이지를 따르십시오.
seo-description: AEM Screens 아키텍처는 기존의 AEM Sites 아키텍처와 유사합니다. 컨텐츠는 AEM 작성자 인스턴스에서 작성된 다음 여러 게시 인스턴스로 전달됩니다. AEM Screens에 대한 작성자 및 게시 구성 방법을 알려면 이 페이지를 따르십시오.
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# AEM Screens에서 작성자 및 게시 구성 {#configuring-author-and-publish-in-aem-screens}

이 페이지에서는 다음 주제를 다룹니다.

* **작성자 및 게시 인스턴스 구성**
* **게시 토폴로지 설정**
* **게시 관리:작성자에서 장치로 게시까지 컨텐츠 업데이트 제공**

## 전제 조건 {#prerequisites}

작성자 및 게시 서버를 시작하기 전에 다음 사항에 대한 사전 지식이 있어야 합니다.

* **AEM 토폴로지**
* **AEM Screens 프로젝트 만들기 및 관리**
* **장치 등록 프로세스**

>[!NOTE]
>
>이 AEM Screens 기능은 AEM 6.4 Screens 기능 팩 2를 설치한 경우에만 사용할 수 있습니다. 이 Feature Pack에 액세스하려면 Adobe 지원 센터에 연락하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.

## 작성자 및 게시 인스턴스 구성 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>작성 및 게시 아키텍처 개요와 AEM 작성자 인스턴스에서 컨텐츠를 제작한 다음 여러 게시 인스턴스로 전달하는 방법에 대한 자세한 내용은 [작성자 및 게시 아키텍처 개요를 참조하십시오](author-publish-architecture-overview.md).

다음 섹션에서는 작성자 및 게시 토폴로지에 복제 에이전트를 설정하는 방법에 대해 설명합니다.

작성자와 두 개의 게시 인스턴스를 호스팅하는 간단한 예를 설정할 수 있습니다.

* 작성자 —&gt; localhost:4502
* 게시 1(pub1) —&gt; localhost:4503
* 게시(pub2) —&gt; localhost:4504

## 작성자에 대한 복제 에이전트 설정 {#setting-replication-agents}

복제 에이전트를 만들려면 표준 복제 에이전트를 만드는 방법을 알아야 합니다.

화면에 필요한 복제 에이전트가 3개 있습니다.

1. **기본 복제 에이전트&#x200B;***(표준 복제 에이전트로&#x200B;***지정**)
1. **스크린 복제 에이전트**
1. **역복제 에이전트**

### 1단계:기본 복제 에이전트 만들기 {#step-creating-a-default-replication-agent}

기본 복제 에이전트를 만들려면 아래 절차를 따르십시오.

1. AEM 인스턴스 —&gt; 망치 아이콘 —&gt; 작업 **—&gt; 구성으로** 이동합니다 ****.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 왼쪽 **탐색** 트리에서 복제를 선택합니다.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 복제 **폴더에서 작성자의** 에이전트를 **선택하고** 새로 **만들기를 클릭하여** 새표준 복제 에이전트를 만듭니다.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 제목 및 **이름을** 입력하여 **복제 에이전트를** 만들고 만들기를 **클릭합니다**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 복제 에이전트를 마우스 오른쪽 버튼으로 클릭하고 **열기를** 클릭하여 설정을 편집합니다.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. [ **편집** ]을 클릭하여 [ **에이전트 설정** ] 대화 상자를 열어 세부 사항을 입력합니다.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. [전송] **탭으로** 이동하여 **URI**, **사용자** 및 **암호를**&#x200B;입력합니다.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >기존 기본 복제 에이전트를 복사하고 이름을 변경할 수도 있습니다.


#### 표준 복제 에이전트 만들기 {#creating-standard-replication-agents}

1. pub1에 대한 표준 복제 에이전트 만들기(기본 에이전트는 이미 구성되어야 함)(예: *https://&lt;hostname&gt;:4503/bin/receive?sling:authRequestLogin=1*)
1. pub2용 표준 복제 에이전트를 만듭니다. pub1용 rep 에이전트를 복사하고 전송 구성의 포트를 변경하여 pub2에 사용할 전송을 업데이트할 수 있습니다. (예: *https://&lt;hostname&gt;:4504/bin/receive?sling:authRequestLogin=1*)

#### 스크린 복제 에이전트 만들기 {#creating-screens-replication-agents}

1. pub1용 AEM Screens 복제 에이전트를 만듭니다. 기본적으로 포트 4503을 가리키는 스크린 복제 에이전트라는 이름이 있습니다. 이 기능을 활성화해야 합니다.
1. pub2용 AEM Screens 복제 에이전트를 만듭니다. pub1용 Screens 복제 에이전트를 복사하고 pub2의 경우 포트를 4504로 변경합니다.

#### 스크린 역방향 복제 에이전트 만들기 {#creating-screens-reverse-replication-agents}

1. pub1용 표준 역방향 복제 에이전트를 만듭니다.
1. pub2용 표준 역방향 복제 에이전트를 만듭니다. pub1용 역방향 rep 에이전트를 복사하고 전송 구성의 포트를 변경하여 pub2에 사용할 전송을 업데이트할 수 있습니다.

## 게시 토폴로지 설정 {#setting-up-publish-topology}

### 1단계:Apache Sling Oak 기반 검색 구성 {#step-configure-apache-sling-oak-based-discovery}

토폴로지의 모든 게시 인스턴스에 대해 Apache Sling Oak 기반 검색 설정

각 게시 인스턴스에 대해:

1. 다음으로 이동 `https://<host>:<port>/system/console/configMgr`
1. Apache **Sling Oak 기반 Discovery Service 구성을** 선택합니다.
1. 토폴로지 커넥터 URL 업데이트:모든 단락 시작 게시 인스턴스의 URL 추가(예: `https://localhost:4502/libs/sling/topology/connector`
1. 토폴로지 커넥터 화이트 리스트:partaking publish instances를 포함하는 IP 또는 서브넷에 적용
1. 로컬 **루프 자동 중지 활성화**

각 게시 인스턴스에 대해 구성이 동일해야 하며 자동 정지 로컬 루프는 무한 루프를 방지합니다.

#### 2단계:게시 토폴로지 확인 {#step-verify-publish-topology}

게시 인스턴스의 경우 로 이동합니다 `https://<host>:<port>/system/console/topology`. 토폴로지에 표시되는 각 게시 인스턴스가 표시됩니다.

#### 3단계:ActiveMQ 아르테미스 클러스터 설정 {#step-setup-activemq-artemis-cluster}

이 단계에서는 ActiveMQ Artemois 클러스터에 대한 암호화된 암호를 만들 수 있습니다.
토폴로지에 있는 모든 게시 인스턴스의 클러스터 사용자 및 암호는 동일해야 합니다. ActiveMQ Artems 구성의 암호를 암호화해야 합니다. 각 인스턴스에는 자체 암호화 키가 있으므로 Crypto Support를 사용하여 암호화된 암호 문자열을 만들어야 합니다. 그러면 암호화된 암호가 ActiveMQ용 OSGi 구성에서 사용됩니다.

각 게시 인스턴스에서:

1. OSGi 콘솔에서 MAIN —&gt; **Crypto 지원** ( **https://&lt;호스트** &gt;:&lt;포트&gt;/*system/console/crypto*)으로 이동합니다.
1. 일반 텍스트에 원하는 일반 텍스트 암호(모든 인스턴스에 대해 동일함)를 **입력합니다**
1. 보호를 **클릭합니다**.
1. 보호된 텍스트 값을 **메모장** 또는 텍스트 편집기에 복사합니다. 이 값은 ActiveMQ용 OSGi 구성에서 사용됩니다.

각 게시 인스턴스에는 기본적으로 고유한 암호화 키가 있으므로 각 pub 인스턴스에서 이 단계를 수행하고 다음 구성에 대한 고유 키를 저장해야 합니다.

*예*,

Pub1 - `{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`Pub2 - `{8d3d113c834cc4f52c2daee0da3cb0a21122a31f0138bfe4b70c9ead79415f41}`

#### 4단계:ActiveMQ 아르테미스 클러스터 활성화 {#step-activate-activemq-artemis-cluster}

각 게시 인스턴스에서:

1. OSGi 구성 관리자 https://&lt;호스트&gt;:&lt; *포트&gt;/system/console/configMgr로 이동합니다.*
1. Apache **ActiveMQ Artems JMS 공급자 구성을** 선택합니다.
1. 다음을 업데이트합니다.

* ***클러스터 암호***:(각 인스턴스당 이전 단계의 암호화된 값 사용)
* ***항목***:{이름:'commands', 주소:'com.adobe.cq.screens.commands', maxConsumers:50}

#### ActiveMQ 아르테미스 클러스터 확인 {#verify-activemq-artemis-cluster}

각 게시 인스턴스의 아래 단계를 따르십시오.

1. OSGi 콘솔 -&gt; 기본 &gt; ActiveMQ Artem으로 이동합니다 `[https://localhost:4505/system/console/mq`.
1. 클러스터 정보 &gt; 토폴로지 &gt; nodes=2, members=2에서 다른 인스턴스의 포트를 확인하고 확인합니다.
1. 테스트 메시지 보내기(브로커 정보 아래의 화면 상단)
1. 필드에 다음 변경 사항을 입력합니다.

   1. **대상**:/com.adobe.cq.screens/devTestTopic
   1. **텍스트**:Hello World
   1. 각 인스턴스의 error.log를 확인하여 메시지가 클라우드 간에 전송되어 수신되었는지 확인합니다

>[!NOTE]
>
>OSGI 콘솔로 이동하면 이전 단계에서 구성을 저장한 후 몇 초 정도 걸릴 수 있습니다. 자세한 내용은 error.log를 확인할 수도 있습니다.

예를 들어 다음 이미지는 ActiveMQ Artemis Server의 성공적인 구성에 표시됩니다.

/system/console/ *mq에서 다음 구성이*&#x200B;표시되지 않으면 */system/console/mq로* 이동하고 **다시 시작을** 클릭하여 브로커를 다시 시작합니다.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 레퍼러 헤더 요구 사항 제거 {#remove-referrer-header-requirement}

각 게시 인스턴스의 단계를 따릅니다.

1. OSGi 콘솔 **&gt; 구성** 관리자로 **이동합니다.**
1. Apache **Sling 레퍼러 필터 선택**
1. 구성 업데이트 및 **비어 있음 확인**

### 작성자 및 게시 인스턴스 구성 {#configuring-author-and-publish-instance}

게시 토폴로지를 설정했으면 작성 및 게시 인스턴스를 구성해야 구현의 실제 결과를 볼 수 있습니다.

>[!NOTE]
>
>**전제 조건**
>
>이 예제를 시작하려면 프로젝트에서 위치, 표시 및 채널을 만든 다음 새 AEM Screens 프로젝트를 만드십시오. 채널에 컨텐츠를 추가하고 디스플레이에 채널을 지정합니다.

#### 1단계:AEM Screens 플레이어 시작(장치) {#step-starting-an-aem-screens-player-device}

1. 별도의 브라우저 창을 실행합니다.
1. Go to Screens player using the *web browser*, that is,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. 장치를 열면 장치의 상태가 등록되지 않음으로 표시됩니다.

>[!NOTE]
>
>다운로드한 AEM Screens 앱 또는 웹 브라우저를 사용하여 AEM Screens 플레이어를 열 수 있습니다.

#### 2단계:작성자에 장치 등록 {#step-registering-a-device-on-author}

1. 프로젝트를 `https://localhost:4502/screens.html/content/screens/we-retail` 이동하거나 선택하고 장치 &gt; 장치 관리자로 이동합니다.
1. 장치 **등록을 선택합니다**.
1. 장치 **등록을** 클릭하여 장치를 봅니다.
1. Select the device you want to register and click **Register Device**.
1. 등록 코드를 확인하고 유효성 검사를 **클릭합니다**.
1. 장치의 제목을 입력하고 등록을 **클릭합니다**.

#### 3단계:표시할 장치 할당 {#step-assigning-the-device-to-display}

1. 이전 **단계에서** 대화 상자에서 디스플레이 할당을 클릭합니다.
1. 위치 폴더에서 채널의 표시 경로를 **선택합니다** .
1. Click **Assign**.
1. Click **Finish** to complete the process, and now the device is assigned.

플레이어를 확인하면 채널에 추가한 콘텐츠가 표시됩니다.

#### 4단계:게시 인스턴스에 장치 구성 게시 {#step-publishing-device-configuration-to-publish-instances}

**장치 확인**

그 전에 아래 단계를 수행하십시오. 장치 ID를 확인하십시오. 확인하려면 CRXDELite에서 */home/users/screens/{project}/devices*&#x200B;경로를 사용하여 디바이스 ID를 검색하십시오.

아래 절차에 따라 장치 사용자를 복제하십시오.

1. 사용자 관리 페이지로 이동합니다(예: `https://localhost:4502/useradmin`
1. 화면 **디바이스-마스터** 그룹 검색
1. 그룹을 마우스 오른쪽 단추로 클릭하고 **활성화를 클릭합니다**

>[!CAUTION]
>
>작성자-게시-스크린 서비스는 작성자 작업에서 사용하는 시스템 사용자이므로 활성화하지 마십시오.

장치 관리 콘솔에서 장치를 활성화할 수도 있습니다. 아래 단계를 따르십시오.

1. 스크린 프로젝트 —&gt; 장치로 **이동합니다**.
1. 작업 표시줄에서 **장치 관리자 **를 클릭합니다.
1. 아래 그림과 같이 장치를 선택하고 **작업** 표시줄에서 활성화를 클릭합니다.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>또는 장치를 활성화한 후에는 아래 그림과 같이 작업 표시줄에서 **서버 URL 편집 **을 클릭하여 서버 URL을 편집하거나 업데이트할 수 있으며 변경 사항이 AEM Screens 플레이어에 전파됩니다.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 게시 확인 목록 {#publishing-check-list}

다음은 게시 검사 목록을 요약하는 점입니다.

* *스크린 장치 사용자* - 이 사용자는 AEM 사용자로 저장되며 도구 &gt; 보안 **&gt;** 사용자에서 **활성화할** 수 ****&#x200B;있습니다. 사용자에게 일련 번호가 긴 문자열이 포함된 "스크린"이 접두사로 추가됩니다.

* *프로젝트* - AEM Screens 프로젝트입니다.
* *위치* - 장치가 연결된 위치입니다.
* *채널* - 위치에 표시되는 하나 이상의 채널
* *예약* - 일정을 사용하는 경우 이 항목이 게시되었는지 확인합니다.
* *위치, 예약 및 채널 폴더* - 해당 리소스가 폴더 안에 있는 경우

확인 목록을 확인한 후 채널에서 다음 변경/동작을 확인해야 합니다.

* 장치 구성을 게시한 후 Screens 플레이어 구성을 열고 게시 인스턴스를 가리킵니다. 장치 관리 콘솔에서 장치를 활성화할 수도 있습니다.
* 작성자의 일부 채널 컨텐츠를 업데이트하고 게시하고 업데이트된 채널이 이제 AEM Screens 플레이어에 표시되는지 확인합니다.
* Screens 플레이어를 다른 게시 인스턴스에 연결하고 위의 동작을 확인합니다.

#### 5단계:관리 패널에서 장치를 게시 인스턴스 가리키기 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Screens 플레이어에서 관리자 UI를 보거나, 왼쪽 위 모서리를 길게 눌러 관리 메뉴, 터치가 활성화된 AEM Screens 플레이어에서 또는 마우스를 사용하여 엽니다.
1. 사이드 **패널에서 구성** 옵션을 클릭합니다.
1. 작성자 인스턴스를 Server에서 게시 인스턴스로 **변경합니다**.

AEM Screens 플레이어에서 변경 내용을 봅니다.

또는 다음 단계를 사용하여 장치 관리 콘솔에서 서버 URL을 업데이트/편집할 수도 있습니다.

1. AEM Screens 프로젝트로 이동하고 장치 **폴더를** 선택합니다.
1. Click **Device Manager** from the action bar.
1. 장치를 선택하고 아래 그림과 같이 작업 표시줄에서 **서버 URL 편집 **을 클릭하면 변경 사항이 AEM Screens 플레이어에 전파됩니다.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

## 게시 관리:작성자에서 장치로 게시까지 컨텐츠 업데이트 제공 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

AEM Screens에서 컨텐츠를 게시하고 게시 취소할 수 있습니다. 게시 관리 기능을 사용하면 작성자에서 장치에 게시하기 위한 컨텐츠 업데이트를 제공할 수 있습니다. 전체 AEM Screens 프로젝트 또는 채널, 위치, 장치, 애플리케이션 또는 일정 중 하나에 대해서만 컨텐츠를 게시/게시 취소할 수 있습니다.

### AEM Screens 프로젝트에 대한 게시 관리 {#managing-publication-for-an-aem-screens-project}

AEM Screens 프로젝트에 대한 콘텐츠 업데이트를 작성자에서 장치로 게시하려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트로 이동합니다.
1. 작업 **표시줄에서** 게시 관리를 클릭하여 프로젝트를 게시하여 인스턴스를 게시합니다.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. The **Manage Publication** wizard opens. 동작을 선택하고 **게시** 시간을 지금 또는 나중에 예약할 수도 있습니다. **다음**&#x200B;을 클릭합니다.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 게시 관리 마법사에서 전체 프로젝트를 선택하려면 **이 확인란을** 선택합니다.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 작업 표시줄에서 **+ 하위** 포함을 클릭하고 모든 옵션을 선택 취소하여 프로젝트의 모든 모듈을 게시하고 게시할 **추가를** 클릭합니다.

   >[!NOTE]
   >
   >기본적으로 모든 상자가 선택되고 프로젝트의 모든 모듈을 게시하려면 확인란을 수동으로 선택 취소해야 합니다.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **하위 포함 대화 상자 이해**

   위에 언급된 단계는 전체 컨텐츠를 게시하는 방법을 보여줍니다. 사용할 수 있는 다른 세 가지 대안을 사용하려면 해당 특정 옵션을 확인해야 합니다.
예를 들어 다음 이미지를 사용하면 프로젝트에서 수정된 페이지만 관리하고 업데이트할 수 있습니다.
   ![이미지](assets/author-publish-manage.png)

   아래 설명을 따라 사용 가능한 옵션을 파악하십시오.

   1. **바로 아래 하위만**&#x200B;포함:이 옵션을 사용하면 프로젝트 구조의 하위 노드에만 업데이트를 관리할 수 있습니다.
   1. **수정된 페이지만 포함**:이 옵션을 사용하면 프로젝트 구조에서 변경 사항이 발견되는 프로젝트의 수정된 페이지에만 업데이트를 관리할 수 있습니다.
   1. **이미 게시된 페이지만**&#x200B;포함:이 옵션을 사용하면 이전에 게시된 페이지의 업데이트만 관리할 수 있습니다.


1. 게시 **관리** 마법사에서 **게시를 클릭합니다.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >컨텐츠가 게시 인스턴스에 도달하도록 몇 초/분 동안 기다립니다.
   >
   >
   >오프라인 **콘텐츠 업데이트를** 사용하여 게시 관리 프로세스는 2단계로 진행되며 단계가 올바른 순서로 진행되어야 합니다.
   >
   >
   >
   >    1. [게시 관리]를 사용하여 게시하기 전에 **오프라인 콘텐츠** 업데이트가 **트리거되면 워크플로우가**&#x200B;작동하지 않습니다.
      >
      >    
   1. 프로젝트에 변경 사항이 없고 오프라인 콘텐츠 업데이트에 대한 내용이 없으면 워크플로우가 **작동하지 않습니다**.
   >    1. 게시 관리 워크플로우에서 게시 단추를 클릭한 후 작성자가 복제 프로세스를 완료하지 않으면(컨텐츠가 여전히 게시 인스턴스에 업로드 **중** ) 워크플로우가 작동하지 않습니다.


1. 게시 관리 워크플로우를 완료한 후에는 작성자에서 오프라인 컨텐츠 업데이트를 트리거해야 합니다. 그러면 작성자 인스턴스에서 오프라인으로 업데이트가 생성됩니다.

   프로젝트로 이동하고 작업 표시줄에서 **오프라인 컨텐츠** 업데이트를 클릭합니다. 이 작업은 동일한 명령을 게시 인스턴스로 전달하여 오프라인 zip이 게시 인스턴스에도 만들어지도록 합니다.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)

   >[!CAUTION]
   >
   >먼저 게시한 다음 이전 단계에 요약된 대로 오프라인 컨텐츠 업데이트를 트리거해야 합니다.

### 채널에 대한 게시 관리 {#managing-publication-for-a-channel}

AEM Screens 프로젝트에서 채널에 대한 콘텐츠 업데이트를 작성자에서 장치로 게시하려면 아래 절차를 따르십시오.

>[!NOTE]
>
>채널에 변경 사항이 있는 경우에만 이 섹션을 따르십시오. 이전 업데이트 오프라인 콘텐츠 이후에 채널에 변경 사항이 없는 경우 개별 채널에 대한 게시 관리 워크플로우가 작동하지 않습니다.

1. 스크린 프로젝트로 이동하고 채널을 선택합니다.
1. 작업 **표시줄에서** 게시 관리를 클릭하여 게시할 채널을 게시합니다.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. The **Manage Publication** wizard opens. 동작을 선택하고 **게시** 시간을 지금 또는 나중에 예약할 수도 있습니다. **다음**&#x200B;을 클릭합니다.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 게시 **관리** 마법사에서 **게시를 클릭합니다.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >컨텐츠가 게시 인스턴스에 도달하도록 몇 초/분 동안 기다립니다.

1. 게시 관리 워크플로우를 완료한 후에는 작성자에서 오프라인 컨텐츠 업데이트를 트리거해야 합니다. 그러면 작성자 인스턴스에서 오프라인으로 업데이트가 생성됩니다.

   채널 대시보드로 이동하고 오프라인 컨텐츠 **업데이트를 클릭합니다**. 이 작업은 동일한 명령을 게시 인스턴스로 전달하여 오프라인 zip이 게시 인스턴스에도 만들어지도록 합니다.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >먼저 게시한 다음 이전 단계에 요약된 대로 오프라인 컨텐츠 업데이트를 트리거해야 합니다.

### 채널 및 장치 재할당: {#channel-and-device-re-assignment}

장치를 다시 할당한 경우 장치를 새 디스플레이에 다시 할당하면 초기 디스플레이와 새 디스플레이를 모두 게시해야 합니다.

마찬가지로 채널을 재할당한 경우 새 디스플레이에 채널이 다시 할당되면 초기 디스플레이와 새 디스플레이를 모두 게시해야 합니다.
