---
title: 채널 레이아웃 편집기
seo-title: 채널 레이아웃 편집기
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 81490abc-58cf-4daa-93d6-d697f7495232
contentOwner: jsyal
discoiquuid: 10beb13e-d8b2-440e-b2b0-d9fc2dafdc26
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 채널 레이아웃 편집기 {#channel-layout-editor}

***채널 레이아웃 편집기***&#x200B;를 사용하면 다중 영역 컨텐츠를 만들고, 문맥에 따라 단일 화면에서 결합할 수 있는 비디오, 이미지 및 텍스트와 같은 다양한 자산을 사용할 수 있습니다. 이미지, 비디오 및 텍스트를 가져와서 모두 함께 혼합하여 대화령의 직관적인 디지털 경험을 만들 수 있습니다. 

프로젝트 요구 사항에 따라 채널에서 여러 영역이 필요하고 이를 하나의 포괄적인 단위로 편집하는 경우가 있습니다. 예를 들어, 단일 채널의 세 개의 분리된 영역에서 관련 소셜 미디어 피드가 실행되는 제품 시퀀스가 있습니다.

## 개요 {#overview}

채널을 만드는 동안 채널에서 영역을 작성하기 위해 다양한 템플릿을 사용할 수 있습니다. 프로젝트 요구 사항에 따라 이미지, 비디오 또는 포함된 채널을 추가하여 컨텐츠를 활용할 수 있습니다.

### 사용 사례 설명 {#use-case-description}

다음 사용 사례에서는 채널에서의 다중 영역 만들기에 대해 설명합니다.

1. ***스크린 프로젝트 생성***

   1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 **스크린**&#x200B;을 선택합니다. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
   1. Click **Create** to create a new Screens project.
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.
   1. Enter the title as **Channel Layout Project** and click **Create**.
   ![ch1](assets/ch1.gif)

1. ***채널 생성***

   1. Navigate to **Channel Layout Project**.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사가 열립니다.
   1. Choose the **1x2 Split Screen Channel** and click **Next**.
   1. Enter the **Title** as **Split horizontal** and click **Create**.
   ![채널 생성](assets/channelcreation.gif)

1. ***채널에 컨텐츠 추가***

   1. Navigate to the **Channel Layout Project** you created and select the channel (**Split Channel**).
   1. Click **Edit** from the action bar and the editor for the **Split Channel** opens.
   1. 작업 표시줄의 왼쪽에 있는 사이드 패널을 전환하는 아이콘을 클릭하여 자산과 구성 요소를 엽니다. 채널에 추가할 구성 요소를 드래그하여 놓습니다.
   ![ch4](assets/ch4.gif)

   >[!NOTE]
   >
   >한 예로, 다음 두 개의 이미지가 편집기에서 채널에 추가됩니다.

   ![screen_shot_2018-02-08at123635pm](assets/screen_shot_2018-02-08at123635pm.png)

1. ***위치 생성***

   1. Navigate to the Locations folder where you want to create your display (**Channel Layout Project**--&gt; **Locations**).
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. Select **Location** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your location as **San Jose**.
   1. **만들기**&#x200B;를 클릭합니다.
   ![ch5](assets/ch5.gif)

1. ***새 디스플레이 생성***

   1. Navigate to the location where you want to create your display (**Acme** --&gt; **Locations** --&gt; **San Jose**) and select **San Jose**.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your display location (enter the title as **Split Display)**.
   1. Under the **Display** tab, choose the details of the Layout. Choose the **Resolution** as **Full HD**. Choose the **Number of Devices Horizontally** as 1 and the **Number of Devices Vertically** as **1**.
   1. **만들기**&#x200B;를 클릭합니다.
   ![ch6](assets/ch6.gif)

1. ***채널 지정***

   1. Navigate to the display from **Channel Layout Project** --&gt; **Locations** --&gt; **San Jose** --&gt; **Split Display**.
   1. Select **Split Display** and tap/click **Assign Channel** from the action bar, Or,
   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel. **채널 지정** 대화 상자가 열립니다.
   1. Enter the **Channel Role** as **Split**.
   1. Select **Reference Channel** by path. Select the channel folder path (**Channel Layout Project** --&gt; **Channels** --&gt; **Split horizontal**) in the Channel.
   1. Select the **Priority** for this channel as **1**.
   1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. **저장**&#x200B;을 클릭합니다.
   ![ch7](assets/ch7.gif)

1. ***장치 등록 및 지정***

   1. 별도의 브라우저 창을 실행합니다. 웹 브라우저를 사용하여 Screens 플레이어로 이동하거나 AEM Screens 앱을 실행합니다.
   1. 장치를 열면 장치의 상태가 등록되지 않음으로 표시됩니다. From the AEM dashboard, navigate to **Channel Layout Project** --&gt; **Devices**.
   1. Click **Device Manager** from the action bar.
   1. Click **Device Registration** and you will see the pending devices. Select the device you want to register and click **Register Device**.
   1. 웹 브라우저나 AEM Screens 플레이어에서 코드를 확인하여 코드의 유효성을 검사해야 합니다. Click **Validate** to navigate to **Device Registration** screen.
   1. Enter Title as **NewD** and click **Register** and the device will be registered.
   1. Click **Assign Display** to move on to the next step where you assign the device to a display.
   1. 장치 지정을 클릭하고 채널의 표시 경로()를 /content/screens/Test_Project/Locations/TestLocation/TestDisplay로 선택합니다. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.
   ![ch8](assets/ch8.gif)

#### AEM Screens 플레이어에서 컨텐츠 보기 {#viewing-content-in-aem-screens-player}

AEM Screens 플레이어를 로드하거나 웹 브라우저를 사용하십시오. 채널의 컨텐츠가 Screens 플레이어에 표시되는 것을 확인할 수 있습니다. 이 컨텐츠는1x2 분할 화면 채널 템플릿으로 표시됩니다.

![](do-not-localize/screen_shot_2018-02-08at123648pm.png)

### 유추 {#inference}

채널을 만들 때 사용 가능한 템플릿을 사용하면 다양한 영역에서 컨텐츠를 활용하고 표시할 수 있습니다. 위의 예는 2x2 템플릿에 대한 사용 사례를 보여줍니다.

다음 이미지는 다양한 템플릿을 사용하여 성취할 수 있는 레이아웃을 보여줍니다.
