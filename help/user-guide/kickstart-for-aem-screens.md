---
title: 시작 안내서
seo-title: 시작 안내서
description: 데모 AEM Screens 프로젝트를 만들려면 이 페이지를 따르십시오. 이 플러그인을 사용하면 설치에서부터 디지털 사이니지 경험을 만들고 AEM Screens 플레이어에서 컨텐츠를 볼 수 있는 새 프로젝트를 설정할 수 있습니다.
translation-type: tm+mt
source-git-commit: 6f95322e35861ef4b552c89320847d97f9644a4b
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 6%

---


# 시작 안내서 {#kickstart-guide}

이 섹션은 AEM Screens의 첫 번째 부분이며 AEM Screens 프로젝트를 설정하고 실행하는 방법을 보여줍니다. 기본적인 디지털 사이니지 경험을 설정하고 각 채널에 자산 및/또는 비디오와 같은 컨텐츠를 추가하고 AEM Screens 플레이어에 컨텐츠를 게시하는 과정을 안내합니다.

>[!NOTE]
>프로젝트 세부 사항 작업을 시작하기 전에 최신 기능 팩을 설치했는지 확인하십시오. Adobe ID을 사용하여 [소프트웨어 배포 포털에서](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) AEM Screens 6.5.5 릴리스의 최신 기능 팩을 다운로드할 수 있습니다.

## 전제 조건 {#prerequisites}

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


## 5분 내에 디지털 사이니지 경험 만들기 {#creating-a-digital-signage-experience-in-minutes}

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

   ![이미지](assets/kickstart/demo-disp1.png)

1. **만들기** 마법사 **에서** 표시를 선택하고 **다음을**&#x200B;클릭합니다.

   ![이미지](assets/kickstart/demo-disp2.png)

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

   ![이미지](assets/kickstart/demo-disp3.png)

이제 아래 그림과 같이 TestDisplay **라는** 새 디스플레이가 위치 **TestLocation**&#x200B;에 추가됩니다.

![이미지](assets/kickstart/demo-disp4.png)

### Assigning a Channel {#assigning-channel}

프로젝트 설정이 완료되면, 컨텐츠를 보려면 디스플레이에 채널을 지정해야 합니다.

1. DemoScreens —> 위치 ******—>** TestLocation **—> LobbyDisplay** ****&#x200B;에서 필요한 디스플레이로 이동합니다.

1. Tap/click **Assign Channel** from the action bar.

   ![이미지](assets/kickstart/demo-assign1.png)

   또는,

   작업 표시줄에서 **대시보드** 를 탭/클릭하고 지정된 채널 및 일정 **패널에서** 채널 **지정을** 클릭합니다.

   ![이미지](assets/kickstart/demo-assign2.png)

1. The **Channel Assignment** dialog box opens.

1. [ **설정** ] 옵션 **에서 경로** 및 **지원되는 이벤트** 를 초기 로드와 **** 과Idle Screen으로 경로 ****&#x200B;로 선택합니다.

   >[!NOTE]
   >
   >기본적으로 **채널 역할**, 우선 **순위**&#x200B;및 **중단 방법** 이 모두채워집니다. 채널 [할당 속성에 대한 자세한 내용은 채널 속성](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 섹션을 참조하십시오.

   ![이미지](assets/kickstart/demo-assign3.png)

   또한 **활성화 창** 및 **되풀이 일정을 선택할 수도 있습니다**.

   >[!NOTE]
   >되풀이 *일정* 을 사용하면 채널에 대한 반복 일정을 설정할 수 있습니다. 채널에 대해 여러 개의 되풀이 일정을 설정합니다.
   >자세한 [내용은 되풀이](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) 일정을 참조하십시오.

1. 환경 **설정을** 구성했으면 저장을 클릭합니다.

### 장치 등록 및 디스플레이에 장치 할당{#registering-device}

AEM 대시보드를 사용하여 장치를 등록해야 합니다.

>[!IMPORTANT]
>ChromeOS 플레이어는 실제 크롬 플레이어 장치가 없어도 개발자 모드에서 Chrome Browser 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 수행하십시오.
>
>1. 최신 Chrome Player를 다운로드하려면 [여기를](https://download.macromedia.com/screens/) 클릭하십시오.
>1. 압축을 풀고 디스크에 저장합니다.
>1. 크롬 브라우저를 열고 메뉴에서 **확장** 기능을 선택하거나 chrome://extensions으로 직접 ***이동합니다***.
>1. 오른쪽 상단 모서리에서 **개발자 모드를** 전환합니다.
>1. 왼쪽 위 **모서리에서 [압축을** 푼 파일 로드]를 클릭하고 압축을 푼 Chrome Player를 로드합니다.
>1. 확장 프로그램 목록에 **있는 경우 AEM Screens Chrome Player** 플러그인을 확인하십시오.
>1. 새 탭을 열고 왼쪽 상단 모서리에서 **앱** 아이콘을 클릭하거나 chrome://apps으로 직접 ***이동합니다***.
>1. Chrome Player를 **시작하려면 AEM Screens** 플러그인을 클릭합니다. 기본적으로 플레이어가 전체 화면 모드로 실행됩니다. 전체 화면 모드를 **종료하려면 esc** 키를 누릅니다.


ChromeOS 플레이어가 켜지면 아래 단계에 따라 Chrome 장치를 등록하십시오.

1. AEM 인스턴스에서 **프로젝트의** 장치 폴더로 이동합니다.

1. Tap/click the **Device Manager** from the action bar.

   ![이미지](assets/kickstart/demo-register1.png)

1. 오른쪽 상단에서 **장치** 등록을 탭/클릭합니다.

1. 필요한 장치를 선택하고 장치 등록을 탭/ **클릭합니다**.

   ![이미지](assets/kickstart/demo-register2.png)

1. 장치가 등록 코드를 동시에 전송할 때까지 기다렸다가 Chrome 장치에서 **등록 코드를** 확인합니다.
   ![이미지](assets/kickstart/demo-register3.png)

1. 두 시스템에서 **등록 코드가** 동일한 경우 AEM에서 유효성 **검사를** 탭/클릭합니다.

1. 원하는 이름을 **장치의 ChromeDeviceforDemo로** 설정하고 [ **등록]을 클릭합니다**.

   ![이미지](assets/kickstart/demo-register4.png)

1. Device **Registration Successful** 대화 상자에서 Assign Display를 **** 클릭합니다.

   ![이미지](assets/kickstart/demo-register5.png)

1. 표시할 경로를 DemoScreens **—>** 위치 **—>** TestLocation **—> LobbyDisplay** 를 선택하고 ClickPublish를 클릭하여 Assign **** ****&#x200B;을 지정합니다.

   ![이미지](assets/kickstart/demo-device6.png)

1. 장치가 성공적으로 할당되면 다음 확인 메시지가 표시됩니다.

   ![이미지](assets/kickstart/demo-register8.png)

1. Tap/click **Finish** to complete the registration process.

1. 디스플레이 대시보드에서 등록된 장치를 볼 수 있어야 합니다.

   ![이미지](assets/kickstart/demo-register9.png)

### Chrome Player에서 콘텐트 보기 {#viewing-content-output}

이제 채널의 모든 에셋이 Chrome 장치에서 재생됩니다.

AEM Screens 채널에서 콘텐츠를 재생해 주셔서 감사합니다.

![이미지](assets/kickstart/demo-video-screens.gif)






