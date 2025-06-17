---
title: 킥스타트 안내서
description: 데모 AEM Screens 프로젝트를 만드는 방법을 알아봅니다. 설치 및 새 프로젝트 설정부터 AEM Screens Player에서 콘텐츠를 볼 수 있도록 디지털 서명 경험을 만드는 데 도움이 됩니다.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 2%

---

# 킥스타트 안내서 {#kickstart-guide}

AEM Screens에 대한 킥스타트는 AEM Screens 프로젝트를 설정하고 실행하는 방법을 보여 줍니다. 기본 디지털 사이니지 경험을 설정하고 각 채널에 에셋 및/또는 비디오와 같은 콘텐츠를 추가하고 콘텐츠를 AEM Screens 플레이어에 게시하는 과정을 안내합니다.

>[!NOTE]
>프로젝트 세부 사항을 작업하기 전에 AEM Screens용 최신 기능 팩을 설치했는지 확인하십시오. Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 최신 기능 팩을 다운로드할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

아래 단계에 따라 AEM Screens용 샘플 프로젝트를 만들고 콘텐츠를 Screens 플레이어에 추가로 게시합니다.

>[!NOTE]
>다음 튜토리얼에서는 Chrome OS 플레이어에서 채널의 콘텐츠를 재생하는 사례를 보여 줍니다.

>[!IMPORTANT]
>**OSGi 구성 설정**
>>장치가 데이터를 서버에 게시할 수 있도록 하려면 빈 레퍼러를 활성화해야 합니다. 예를 들어 빈 레퍼러 속성이 비활성화된 경우 디바이스는 스크린샷을 다시 게시할 수 없습니다. 현재 이러한 기능 중 일부는 OSGi 구성에서 `Apache Sling` 레퍼러 필터 빈 허용을 사용하도록 설정한 경우에만 사용할 수 있습니다. 대시보드에 보안 설정으로 인해 이러한 기능 중 일부가 작동하지 않을 수 있다는 경고가 표시될 수 있습니다.
>>***Apache Sling 레퍼러 필터 허용***&#x200B;을 활성화하려면 아래 단계를 따르십시오.


## 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM 인스턴스 > hammer 아이콘 > **작업** > **웹 콘솔**&#x200B;을 통해 **Adobe Experience Manager 웹 콘솔 구성**(으)로 이동합니다.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성**&#x200B;이 열립니다. Sling 레퍼러를 검색합니다.

   sling 레퍼러 속성을 검색하려면 **Mac**&#x200B;의 경우 **Command+F**&#x200B;를 누르고 **Windows**&#x200B;의 경우 **Control+F**&#x200B;를 누릅니다.

1. 아래 그림과 같이 **비우기 허용** 옵션을 선택합니다.

   ![이미지](assets/config/empty-ref2.png)

1. Apache Sling Referrer Filter Allow Empty를 활성화하려면 **저장**&#x200B;을(를) 클릭하십시오.

## 5분 내에 디지털 신호계 환경 만들기 {#creating-a-digital-signage-experience-in-minutes}

### AEM Screens 프로젝트 만들기 {#creating-project}

첫 번째 단계는 AEM Screens 프로젝트를 만드는 것입니다.

1. Adobe Experience Manager(AEM) 인스턴스로 이동하여 **Screens**&#x200B;을(를) 클릭합니다. 또는 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`에서 바로 탐색할 수 있습니다.

1. Screens 프로젝트를 만들 수 있도록 **Screens 프로젝트 만들기**&#x200B;를 클릭합니다.
1. 제목을 **DemoScreens**(으)로 입력한 다음 **저장**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-1.png)

   >[!NOTE]
   >프로젝트를 만들면 AEM Screens 프로젝트 홈 페이지로 돌아갑니다. 이제 프로젝트를 클릭합니다. 프로젝트에는 **응용 프로그램**, **채널**, **장치**, **위치** 및 **일정**&#x200B;이라는 5개의 다른 폴더가 있습니다.

### 채널 만들기 {#creating-channel}

AEM Screens 프로젝트를 만든 후 콘텐츠를 관리할 채널을 만듭니다.

프로젝트에 대한 채널을 만들려면 아래 단계를 따르십시오.

1. 프로젝트를 만든 후 아래 그림과 같이 **DemoScreens** 프로젝트를 클릭하고 **채널** 폴더를 클릭하십시오. 작업 표시줄에서 **+ 만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-2.png)

1. 마법사에서 **시퀀스 채널**&#x200B;을(를) 선택하고 **다음**을(를) 클릭합니다.
   ![이미지](assets/kickstart/demo-3.png)

1. **제목**&#x200B;을(를) **TestChannel**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-4.png)

   아래 그림과 같이 이제 **TestChannel**&#x200B;이(가) 채널 폴더에 추가됩니다.

   ![이미지](assets/kickstart/demo-5.png)

### 채널에 콘텐츠 추가 {#adding-content}

채널이 준비되면 AEM Screens Player에서 표시할 수 있는 채널에 콘텐츠를 추가합니다.

프로젝트의 채널(**TestChannel**)에 콘텐츠를 추가하려면 아래 단계를 따르십시오.

1. 만든 **DemoProject**(으)로 이동하고 **채널** 폴더에서 **TestChannel**&#x200B;을(를) 클릭합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다(아래 그림 참조). **TestChannel**&#x200B;의 편집기가 열립니다.

   ![이미지](assets/kickstart/demo-6.png)

1. 작업 표시줄의 왼쪽에 있는 사이드 패널을 토글하여 에셋 및 구성 요소를 여는 아이콘을 클릭합니다.

1. 채널에 추가하려는 구성 요소를 드래그하여 놓습니다.

   ![이미지](assets/kickstart/demo-7.png)

### 위치 생성 {#creating-location}

채널이 준비되면 위치를 만듭니다.

>[!NOTE]
>***위치***&#x200B;는 사용자의 다양한 디지털 사이니지 환경을 구분하고 다양한 화면의 위치에 따른 디스플레이 구성을 포함합니다.

프로젝트의 위치를 만들려면 아래 단계를 따르십시오.

1. 만든 **DemoProject**(으)로 이동하여 **위치** 폴더를 클릭합니다.
1. 작업 표시줄에서 **+ 만들기**&#x200B;를 클릭합니다.
1. 마법사에서 **위치**&#x200B;를 클릭하고 **다음**&#x200B;을 클릭합니다.
1. 위치에 대한 **이름**&#x200B;을(를) 입력하고(제목을 **TestLocation**(으)로 입력) **만들기**&#x200B;를 클릭합니다.

**TestLocation**&#x200B;이(가) 만들어지고 **Locations** 폴더에 추가됩니다.


### 위치에 대한 디스플레이 만들기 {#creating-display}

위치를 만든 경우 해당 위치에 대한 디스플레이를 만듭니다.

>[!NOTE]
>***디스플레이***&#x200B;은(는) 하나 이상의 화면에서 실행되는 디지털 환경을 나타냅니다.

1. **TestLocation**(으)로 이동하여 클릭합니다.
1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-disp1.png)

1. **만들기** 마법사에서 **표시**&#x200B;를 클릭하고 **다음**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-disp2.png)

1. **제목**&#x200B;을(를) **LobbyDisplay**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-disp3.png)

   아래 그림과 같이 제목이 **TestDisplay**&#x200B;인 새 디스플레이가 위치 **TestLocation**&#x200B;에 추가됩니다.

   ![이미지](assets/kickstart/demo-disp4.png)

### 채널 할당 {#assigning-channel}

프로젝트 설정이 완료되면 콘텐츠를 볼 수 있도록 채널을 디스플레이에 할당합니다.

1. **DemoScreens** > **위치** > **TestLocation** > **LobbyDisplay**&#x200B;에서 필요한 표시로 이동합니다.

1. 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-assign1.png)

   또는,

   작업 표시줄에서 **대시보드**&#x200B;를 클릭하고 **할당된 채널 및 일정** 패널에서 **+채널 할당**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-assign2.png)

1. **채널 할당** 대화 상자가 열립니다.

1. **설정** 옵션에서 채널 **경로별** 및 **지원되는 이벤트**(예: **초기 로드** 및 **유휴 화면**)를 선택합니다.

   >[!NOTE]
   >
   >**채널 역할**, **우선 순위** 및 **중단 메서드**&#x200B;는 모두 기본적으로 채워집니다. 채널 할당 속성에 대한 자세한 내용은 [채널 속성](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 섹션을 참조하십시오.

   ![이미지](assets/kickstart/demo-assign3.png)

   **활성화 기간** 및 **반복 일정**&#x200B;을 클릭할 수도 있습니다.

   >[!NOTE]
   >*반복 일정*을 통해 채널에 대한 반복 일정을 설정할 수 있습니다. 한 채널에 대해 여러 반복 일정을 설정할 수 있습니다.
   >자세한 내용은 [반복 일정](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)을 참조하세요.

1. 환경 설정을 구성했으면 **저장**&#x200B;을 클릭합니다.

### 장치 등록 및 디스플레이에 장치 할당 {#registering-device}

AEM 대시보드를 사용하여 장치를 등록합니다.

>[!IMPORTANT]
>Chrome OS 플레이어는 실제 Chrome 플레이어 장치 없이 개발자 모드에서 Chrome 브라우저 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 따르십시오.
>
>1. 최신 Chrome 플레이어를 다운로드하려면 [여기](https://download.macromedia.com/screens/)를 클릭하십시오.
>1. 압축을 풀고 디스크에 저장합니다.
>1. Chrome 브라우저를 열고 메뉴에서 **확장**&#x200B;을 클릭하거나 직접 ***chrome://extensions***(으)로 이동합니다.
>1. 오른쪽 상단에서 **개발자 모드**&#x200B;를 켭니다.
>1. 왼쪽 상단 모서리에서 **압축을 푼 항목 로드**&#x200B;를 클릭하고 압축을 푼 Chrome Player를 로드합니다.
>1. 확장 목록에서 **AEM Screens Chrome 플레이어** 플러그 인을 사용할 수 있는지 확인하십시오.
>1. 새 탭을 열고 왼쪽 상단 모서리에서 **앱** 아이콘을 클릭하거나 직접 ***chrome://apps***(으)로 이동합니다.
>1. Chrome Player를 시작할 수 있도록 **AEM Screens** 플러그 인을 클릭합니다. 기본적으로 플레이어는 전체 화면 모드로 실행됩니다. 전체 화면 모드를 종료하려면 **Esc**&#x200B;을 누르십시오.

Chrome OS 플레이어가 켜진 후 아래 단계에 따라 Chrome 장치를 등록합니다.

1. AEM 인스턴스에서 프로젝트의 **장치** 폴더로 이동합니다.

1. 작업 표시줄에서 **장치 관리자**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-register1.png)

1. 오른쪽 상단에서 **장치 등록**&#x200B;을 클릭합니다.

1. 필요한 장치를 클릭하고 **장치 등록**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-register2.png)

1. 장치가 등록 코드를 보낼 때까지 기다렸다가 Chrome 장치에서 **등록 코드**을(를) 동시에 확인합니다.
   ![이미지](assets/kickstart/demo-register3.png)

1. **등록 코드**&#x200B;가 두 컴퓨터에서 동일한 경우 AEM에서 **유효성 검사**&#x200B;를 클릭하십시오.

1. 원하는 이름을 장치의 **ChromeDeviceforDemo**(으)로 설정하고 **등록**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-register4.png)

1. **장치 등록 성공** 대화 상자에서 **디스플레이 할당**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-register5.png)

1. 디스플레이 경로를 **DemoScreens** > **위치** > **TestLocation** > **LobbyDisplay**(으)로 클릭하고 **할당**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-device6.png)

1. 장치가 성공적으로 할당되면 다음 확인이 표시됩니다.

   ![이미지](assets/kickstart/demo-register8.png)

1. 등록 프로세스를 완료하려면 **완료**&#x200B;를 클릭하십시오. 이제 디스플레이 대시보드에서 등록된 장치를 볼 수 있습니다.

   ![이미지](assets/kickstart/demo-register9.png)

### Chrome Player에서 컨텐츠 보기 {#viewing-content-output}

채널의 모든 에셋이 이제 Chrome OS 플레이어에서 재생됩니다.

축하합니다. 이제 AEM Screens 채널에서 콘텐츠를 재생하고 있습니다!

![이미지](assets/kickstart/demo-video-screens.gif)
