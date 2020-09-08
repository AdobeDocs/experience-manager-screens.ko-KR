---
title: 시작 안내서
seo-title: 시작 안내서
description: 데모 AEM Screens 프로젝트를 만들려면 이 페이지를 따르십시오. 이 플러그인을 사용하면 설치에서부터 디지털 사이니지 경험을 만들고 AEM Screens 플레이어에서 컨텐츠를 볼 수 있는 새 프로젝트를 설정할 수 있습니다.
translation-type: tm+mt
source-git-commit: f2fef18cc73825b3f062a79c560097e8fd00ac9f
workflow-type: tm+mt
source-wordcount: '1080'
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

### Creating a new AEM Screens Project {#creating-project}

첫 번째 단계는 새로운 AEM Screens 프로젝트를 만드는 것입니다.

1. Adobe Experience Manager(AEM) 인스턴스로 이동하고 **스크린을 클릭합니다**. 또는 다음에서 직접 탐색할 수 있습니다 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. 제목으로 DemoScreens를 **입력하고** 저장을 **클릭합니다**.

   ![이미지](assets/kickstart/demo-1.png)

   >[!NOTE]
   >프로젝트를 만들면 스크린 프로젝트 홈 페이지로 돌아갑니다. 이제 프로젝트를 선택할 수 있습니다. 프로젝트에는 **채널**, **장치**, 위치 **,**&#x200B;및Schedule이라는 이름의 다섯 개의 다른 폴더가 ********&#x200B;있습니다.


### 새 채널 만들기 {#creating-channel}

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

1. Navigate to the *Test_Project* you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.

1. 작업 표시줄의 왼쪽에 있는 사이드 패널을 전환하는 아이콘을 클릭하여 자산과 구성 요소를 엽니다.

1. 채널에 추가할 구성 요소를 드래그하여 놓습니다.

   ![chlimage_1-8](assets/chlimage_1-8.png)

이 예에서 편집기에는 채널에 추가된 이미지가 표시됩니다.

![chlimage_1-9](assets/chlimage_1-9.png)

### 새 위치 만들기 {#creating-location}

적합한 채널을 확보했다면 위치를 만들어야 합니다.

***위치는*** 다양한 디지털 사이니지 경험을 구분하고 다양한 화면의 위치에 따라 디스플레이의 구성을 포함합니다.

아래 절차에 따라 프로젝트의 새 위치를 만드십시오.

1. Navigate to the *Test_Project* you created and select the **Locations** folder.

1. 작업 **표시줄의 더하기 아이콘 옆에 있는 만들기를** 클릭합니다(아래 그림 참조). 마법사가 열립니다.
1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** and **Title** for your location (enter the title as *TestLocation*) and click **Create**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

TestLocation *이* 만들어지고 위치 **폴더에** 추가됩니다.

![chlimage_1-11](assets/chlimage_1-11.png)

### TestLocation에 대한 새 표시 만들기 {#creating-display}

위치를 생성한 후에는 위치에 대한 새 디스플레이를 생성해야 합니다.

***하나*** 이상의 화면에서 실행되는 디지털 경험을 표시합니다.

1. 위 그림에 표시된 대로 디스플레이를 만들 위치(*Test_* Project —> **위치** —> *TestLocation)* 로 이동하고 TestLocation **&#x200B;을 선택합니다.

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
1. **만들기** 마법사 **에서** 표시를 선택하고 **다음을**&#x200B;클릭합니다.

1. 표시 위치에 사용할 **이름** 및 **제목을** 입력합니다(제목으로 *TestDisplay를*&#x200B;입력).

1. Under the **Display** tab, choose the details of the Layout.

   1. Choose the **Resolution** as **Full HD**.

   1. Choose the **Number of Devices Horizontally** as 1.

   1. Choose the **Number of Devices Vertically** as 1.

   1. **만들기**&#x200B;를 클릭합니다.

아래 그림과 같이 새 디스플레이(*TestDisplay*)가 위치 *TestLocation*&#x200B;에 추가됩니다.

![chlimage_1-12](assets/chlimage_1-12.png)

### 채널 지정 {#assigning-channel}

1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

1. Select *TestDisplay* and tap/click **Assign Channel **from the action bar, *Or*,

1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **채널 지정** 대화 상자가 열립니다.

1. Select **Reference Channel** by **path**

1. Enter the **Channel Role** as *LiveStream*.

1. Channel Path( **Test_Project** —>*Channels* —> Test *Channel* TestChannel ** ****&#x200B;에서 Channel Path를 선택합니다.

1. Select the **Priority** for this channel as *1*.

1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.

1. 스케줄 **을** 입력하고 **활성** 및 **활성**&#x200B;일자를선택합니다.

1. **저장**&#x200B;을 클릭합니다.

채널이 만들어지고 패널에 추가됩니다.

![chlimage_1-15](assets/chlimage_1-15.png)

### 장치 등록 {#registering-device}

AEM 대시보드를 사용하여 장치를 등록해야 합니다.

>[!NOTE]
>다운로드한 AEM Screens 앱 또는 웹 브라우저를 사용하여 Screens 플레이어를 열 수 있습니다.



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

위의 구성을 추가한 후에는 플레이어에 장치에 표시되는 기본 채널이 자동으로 표시됩니다.

![chlimage_1-23](assets/chlimage_1-23.png)

AEM Screens 플레이어에 대한 자세한 내용은 [AEM Screens 플레이어를](working-with-screens-player.md) 참조하십시오.
