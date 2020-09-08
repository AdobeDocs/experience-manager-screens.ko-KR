---
title: 시작 안내서
seo-title: 시작 안내서
description: 데모 AEM Screens 프로젝트를 만들려면 이 페이지를 따르십시오. 이 플러그인을 사용하면 설치에서부터 디지털 사이니지 경험을 만들고 AEM Screens 플레이어에서 컨텐츠를 볼 수 있는 새 프로젝트를 설정할 수 있습니다.
translation-type: tm+mt
source-git-commit: 78ddd2b45f39d69b66f740910327eef475bcdcac
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 7%

---


# 시작 안내서 {#kickstart-guide}

이 섹션은 AEM Screens의 첫 번째 부분이며 AEM Screens 프로젝트를 설정하고 실행하는 방법을 보여줍니다. 기본적인 디지털 사이니지 경험을 설정하고 각 채널에 자산 및/또는 비디오와 같은 컨텐츠를 추가하고 AEM Screens 플레이어에 컨텐츠를 게시하는 과정을 안내합니다.

>[!NOTE]
>프로젝트 세부 사항 작업을 시작하기 전에 최신 기능 팩을 설치했는지 확인하십시오. Adobe ID을 사용하여 [소프트웨어 배포 포털에서](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) AEM Screens 6.5.5 릴리스의 최신 기능 팩을 다운로드할 수 있습니다.

## 5분 내에 디지털 사이니지 경험 만들기 {#creating-a-digital-signage-experience-in-minutes}

아래 절차에 따라 AEM Screens용 샘플 프로젝트를 만들고 Screens 플레이어에 컨텐츠를 추가로 게시하십시오.

>[!NOTE]
>다음 자습서에서는 Chrome OS 플레이어에서 채널의 컨텐츠를 재생하는 방법을 보여줍니다.

>[!IMPORTANT]
>**OSGi 구성 설정**
>장치가 서버에 데이터를 게시하도록 하려면 빈 레퍼러를 활성화해야 합니다. 예를 들어 빈 레퍼러 속성이 비활성화되어 있으면 장치가 스크린샷을 다시 게시할 수 없습니다. 현재 이러한 기능 중 일부는 OSGi 구성에서 [Apache Sling Referrer 필터 비어 있음 허용]이 활성화되어 있을 경우에만 사용할 수 있습니다. 대시보드에는 보안 설정으로 인해 이러한 기능 중 일부가 작동하지 않을 수 있다는 경고가 표시될 수 있습니다.
>아래 절차에 따라 ***Apache Sling Referrer Filter Allow Empty를 활성화합니다***.


## 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM 인스턴스 —> 망치 아이콘 —> 작업 **** —> **웹 콘솔** 을 통해 **Adobe Experience Manager 웹 콘솔 구성으로 이동합니다**.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성이** 열립니다. 슬링 레퍼러를 검색합니다.

   sling referrer 속성을 검색하려면 **Mac** 용 **Command+F** 를 누르고 **Windows용 Ctrl+F** 를 **누릅니다**.

1. 아래 그림과 같이 **빈** 허용 옵션을 선택합니다.

   ![이미지](assets/config/empty-ref2.png)

1. [ **저장** ]을 클릭하여 Apache Sling 레퍼러 필터 [비어 있음]을 활성화합니다.


## 자습서 {#tutorial}

### Creating an AEM Screens Project {#creating-project}

첫 번째 단계는 새로운 AEM Screens 프로젝트를 만드는 것입니다.

1. Adobe Experience Manager(AEM) 인스턴스로 이동하고 **스크린을 클릭합니다**. 또는 다음에서 직접 탐색할 수 있습니다 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. 제목으로 DemoScreens를 **입력하고** 저장을 **클릭합니다**.

   ![이미지](assets/kickstart/demo-1.png)

   >[!NOTE]
   >프로젝트를 만들면 스크린 프로젝트 홈 페이지로 돌아갑니다. 이제 프로젝트를 선택할 수 있습니다. 프로젝트에는 **채널**, **장치**, 위치 **,**&#x200B;및Schedule이라는 이름의 다섯 개의 다른 폴더가 ********&#x200B;있습니다.


### 채널 생성 {#creating-channel}

프로젝트가 제자리에 배치되면 컨텐츠를 관리하는 새 채널을 만들어야 합니다.

아래 절차에 따라 프로젝트에 사용할 새 채널을 만드십시오.

1. 프로젝트를 만든 후 **DemoScreens** 프로젝트를 선택하고 아래 그림과 같이 **채널 폴더를**&#x200B;선택합니다. Click **+ Create** from the action bar.

   ![이미지](assets/kickstart/demo-2.png)

1. 마법사에서 **시퀀스 채널** 을 선택하고 다음을 **클릭합니다**.
   ![이미지](assets/kickstart/demo-3.png)

1. Enter the **Title** as *TestChannel* and click **Create**.

   ![이미지](assets/kickstart/demo-4.png)

아래 그림과 같이 *TestChannel* 이 만들어지고 채널 폴더에 추가됩니다.

![이미지](assets/kickstart/demo-5.png)

### Adding Content to a Channel {#adding-content}

적절한 채널을 확보했으면 Screens 플레이어가 표시할 채널에 컨텐츠를 추가해야 합니다.

프로젝트의 채널(TestChannel **)에 컨텐츠를 추가하려면 아래 단계를 따르십시오.

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the **TestChannel** opens.

   ![이미지](assets/kickstart/demo-6.png)

1. 작업 표시줄의 왼쪽에 있는 사이드 패널을 전환하는 아이콘을 클릭하여 자산과 구성 요소를 엽니다.

1. 채널에 추가할 구성 요소를 드래그하여 놓습니다.

   ![이미지](assets/kickstart/demo-7.png)

### 위치 생성 {#creating-location}

적절한 채널을 확보했으면 위치를 만들어야 합니다.

>[!NOTE]
>***위치는*** 다양한 디지털 사이니지 경험을 구분하고 다양한 화면의 위치에 따라 디스플레이의 구성을 포함합니다.

아래 절차에 따라 프로젝트의 새 위치를 만드십시오.

1. Navigate to the **DemoProject** you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

TestLocation **이** 만들어지고 위치 **폴더에** 추가됩니다.


### 위치에 대한 디스플레이 만들기 {#creating-display}

위치를 생성한 후에는 위치에 대한 새 디스플레이를 생성해야 합니다.

>[!NOTE]
>***하나*** 이상의 화면에서 실행되는 디지털 경험을 표시합니다.

1. TestLocation으로 **이동하여** 선택합니다.

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

1. **만들기** 마법사 **에서** 표시를 선택하고 **다음을**&#x200B;클릭합니다.

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

이제 아래 그림과 같이 TestDisplay **라는** 새 디스플레이가 위치 **TestLocation**&#x200B;에 추가됩니다.

### Assigning a Channel {#assigning-channel}

프로젝트 설정이 완료되면, 컨텐츠를 보려면 디스플레이에 채널을 지정해야 합니다.

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **TestLocation** --> **LobbyDisplay**.

1. Tap/click **Assign Channel** from the action bar.

   또는,

   작업 표시줄에서 **대시보드** 를 탭/클릭하고 지정된 채널 및 일정 **패널에서** 채널 **지정을** 클릭합니다.

1. The **Channel Assignment** dialog box opens.

1. [ **설정** ] 옵션 **에서 이름별로 경로** 또는 경로 **별로 채널을 선택하고, 역할**, 채널, **채널PriorityPriority**, 지원되는Events,지원되는Events, 및Safety ************&#x200B;와 SafetyAInterftion Methods를 입력합니다. 또한 이 대화 상자에서 명소 도구 설명을 활성화할 수 있습니다.


   >[!NOTE]
   >채널 지정 속성에 대한 자세한 내용은 [채널 속성](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 섹션을 참조하십시오.

1. 예약 **옵션** 에서 **활성화 창** 및 **되풀이 일정**&#x200B;을선택합니다.

1. 환경 **설정을** 구성했으면 저장을 클릭합니다.

### 장치 등록 {#registering-device}

AEM 대시보드를 사용하여 장치를 등록해야 합니다.

### Chrome Player에서 콘텐트 보기 {#viewing-content-output}

이 예에서는 Chrome Player에서 출력을 보여 줍니다. 디스플레이에 채널을 지정했으면 플레이어를 플레이어에 등록해야 합니다.



