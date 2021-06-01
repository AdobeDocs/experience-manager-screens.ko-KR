---
title: Kickstart 안내서
seo-title: Kickstart 안내서
description: 데모 AEM Screens 프로젝트를 만들려면 이 페이지를 따르십시오. 설치 및 새 프로젝트를 설정하여 AEM Screens 플레이어에서 콘텐츠를 볼 수 있는 디지털 서명 경험을 만드는 데 도움이 됩니다.
feature: 개요, 디지털 서명
role: Business Practitioner
level: Beginner
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 6%

---


# 시작 안내서 {#kickstart-guide}

AEM Screens의 킥스타트는 AEM Screens 프로젝트를 설정하고 실행하는 방법을 보여줍니다. 기본 디지털 간판 경험을 설정하고, 각 채널에 자산 및/또는 비디오와 같은 컨텐츠를 추가하고, AEM Screens 플레이어에 컨텐츠를 추가로 게시하는 과정을 안내합니다.

>[!NOTE]
>프로젝트 세부 사항 작업을 시작하기 전에 AEM Screens용 최신 기능 팩을 설치했는지 확인하십시오. Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 최신 기능 팩을 다운로드할 수 있습니다.

## 전제 조건 {#prerequisites}

아래 절차에 따라 AEM Screens에 대한 샘플 프로젝트를 만들고 Screens 플레이어에 컨텐츠를 추가로 게시하십시오.

>[!NOTE]
>다음 튜토리얼에서는 Chrome OS 플레이어에서 채널의 컨텐츠를 재생합니다.

>[!IMPORTANT]
>**OSGi 구성 설정**
>장치가 서버에 데이터를 게시하도록 하려면 빈 레퍼러를 사용하도록 설정해야 합니다. 예를 들어 빈 레퍼러 속성이 비활성화된 경우 장치가 스크린샷을 다시 게시할 수 없습니다. 현재 이러한 기능 중 일부는 OSGi 구성에서 Apache Sling Referrer Filter Allow Empty 가 활성화되어 있을 경우에만 사용할 수 있습니다. 대시보드에 보안 설정으로 인해 이러한 기능 중 일부가 작동하지 않을 수 있다는 경고가 표시될 수 있습니다.
>아래 절차에 따라 ***Apache Sling Referrer Filter Allow Empty***&#x200B;를 활성화하십시오.


## 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM 인스턴스 —> 망치 아이콘 —> **작업** —> **웹 콘솔**&#x200B;을 통해 **Adobe Experience Manager 웹 콘솔 구성**&#x200B;으로 이동합니다.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성** 이 열립니다. sling 레퍼러를 검색합니다.

   Sling 레퍼러 속성을 검색하려면 **Command+F****Mac** 및 **Control+F****을 누르십시오.**

1. 아래 그림과 같이 **Allow Empty** 옵션을 선택합니다.

   ![이미지](assets/config/empty-ref2.png)

1. **저장** 을 클릭하여 Apache Sling 레퍼러 필터가 빈 채로 허용을 활성화합니다.

## 5분 내에 디지털 서명 경험 만들기 {#creating-a-digital-signage-experience-in-minutes}

### AEM Screens 프로젝트 만들기 {#creating-project}

첫 번째 단계는 AEM Screens 프로젝트를 만드는 것입니다.

1. Adobe Experience Manager(AEM) 인스턴스로 이동하고 **Screens**&#x200B;를 클릭합니다. 또는 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`에서 직접 탐색할 수 있습니다.

1. **스크린 프로젝트 만들기**&#x200B;를 클릭하여 새 스크린 프로젝트를 만듭니다. 제목을 **DemoScreens**&#x200B;로 입력하고 **저장**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-1.png)

   >[!NOTE]
   >프로젝트를 만들면 스크린 프로젝트 홈 페이지로 돌아갑니다. 이제 프로젝트를 선택할 수 있습니다. 프로젝트에는 **응용 프로그램**, **채널**, **장치**, **위치** 및 **예약**&#x200B;이라는 다섯 개의 폴더가 있습니다.

### 채널 생성 {#creating-channel}

AEM Screens 프로젝트를 만들었으면 컨텐츠를 관리하는 새 채널을 만들어야 합니다.

프로젝트에 대한 새 채널을 만들려면 아래 절차를 따르십시오.

1. 프로젝트를 만든 후 **DemoScreens** 프로젝트를 선택하고 아래 그림과 같이 **채널** 폴더를 선택합니다. 작업 표시줄에서 **+ 만들기** 를 클릭합니다.

   ![이미지](assets/kickstart/demo-2.png)

1. 마법사에서 **시퀀스 채널**&#x200B;을 선택하고 **다음**을 클릭합니다.
   ![이미지](assets/kickstart/demo-3.png)

1. **제목** 을 **TestChannel** 로 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-4.png)

   이제 **TestChannel**&#x200B;이 아래 그림과 같이 채널 폴더에 추가됩니다.

   ![이미지](assets/kickstart/demo-5.png)

### 채널에 컨텐츠 추가 {#adding-content}

채널이 준비되면 AEM Screens 플레이어에서 표시할 채널에 컨텐츠를 추가해야 합니다.

아래 절차에 따라 프로젝트의 채널(**TestChannel**)에 컨텐츠를 추가하십시오.

1. 만든 **DemoProject** 로 이동하고 **채널** 폴더에서 **TestChannel**&#x200B;을 선택합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다(아래 그림 참조). **TestChannel**&#x200B;에 대한 편집기가 열립니다.

   ![이미지](assets/kickstart/demo-6.png)

1. 작업 표시줄의 왼쪽에 있는 사이드 패널을 전환하는 아이콘을 클릭하여 자산과 구성 요소를 엽니다.

1. 채널에 추가할 구성 요소를 드래그하여 놓습니다.

   ![이미지](assets/kickstart/demo-7.png)

### 위치 생성 {#creating-location}

채널이 준비되면 위치를 만들어야 합니다.

>[!NOTE]
>***위치***&#x200B;는 다양한 디지털 간판 경험을 구분하고 다양한 화면이 있는 위치에 따라 디스플레이의 구성을 포함합니다.

아래 절차에 따라 프로젝트의 새 위치를 만드십시오.

1. 만든 **DemoProject** 로 이동하고 **위치** 폴더를 선택합니다.

1. 작업 표시줄에서 **+ 만들기** 를 클릭합니다.

1. 마법사에서 **위치**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.

1. 위치에 대한 **이름**&#x200B;을 입력하고(를 **TestLocation**) **만들기**&#x200B;를 클릭합니다.

**TestLocation**&#x200B;이(가) 만들어지고 **Locations** 폴더에 추가됩니다.


### 위치 {#creating-display}에 대한 표시 만들기

위치를 만들었으면 위치에 대한 새 디스플레이를 만들어야 합니다.

>[!NOTE]
>***Display*** 는 하나 이상의 화면에서 실행되는 디지털 경험을 나타냅니다.

1. **TestLocation**&#x200B;으로 이동하여 선택합니다.

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

   ![이미지](assets/kickstart/demo-disp1.png)

1. **만들기** 마법사에서 **표시**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-disp2.png)

1. **제목**&#x200B;을 **LobbyDisplay**&#x200B;로 입력하고 **만들기**&#x200B;를 클릭하십시오.

   ![이미지](assets/kickstart/demo-disp3.png)

   이제 **TestDisplay**&#x200B;라는 새 디스플레이가 아래 그림과 같이 위치 **TestLocation**&#x200B;에 추가됩니다.

   ![이미지](assets/kickstart/demo-disp4.png)

### 채널 {#assigning-channel} 할당

프로젝트 설정이 완료되면 컨텐츠를 보려면 채널을 디스플레이에 지정해야 합니다.

1. **DemoScreens** —> **위치** —> **TestLocation** —> **LobbyDisplay**&#x200B;에서 필요한 디스플레이로 이동합니다.

1. 작업 표시줄에서 **채널 지정**&#x200B;을 탭/클릭합니다.

   ![이미지](assets/kickstart/demo-assign1.png)

   또는,

   작업 표시줄에서 **대시보드**&#x200B;를 탭/클릭하고 **지정된 채널 및 예약** 패널에서 **+채널 지정**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-assign2.png)

1. **채널 지정** 대화 상자가 열립니다.

1. **설정** 옵션에서 채널 **을 경로**&#x200B;로 선택하고 **지원되는 이벤트**&#x200B;를 **초기 로드** 및 **유휴 화면**&#x200B;으로 선택합니다.

   >[!NOTE]
   >
   >**채널 역할**, **우선순위** 및 **중단 메서드**&#x200B;는 모두 기본적으로 채워집니다. 채널 지정 속성에 대한 자세한 내용은 [채널 속성](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 섹션을 참조하십시오.

   ![이미지](assets/kickstart/demo-assign3.png)

   또한 **활성화 창** 및 **되풀이 일정**&#x200B;을 선택할 수도 있습니다.

   >[!NOTE]
   >*되풀이 일정*을 사용하면 채널에 대한 반복 일정을 설정할 수 있습니다. 채널에 대해 여러 개의 되풀이 일정을 설정합니다.
   >자세한 내용은 [되풀이 일정](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)을 참조하십시오.

1. 환경 설정을 구성했으면 **저장**&#x200B;을 클릭합니다.

### 장치 등록 및 디스플레이에 장치 지정 {#registering-device}

AEM 대시보드를 사용하여 장치를 등록해야 합니다.

>[!IMPORTANT]
>Chrome OS 플레이어는 실제 chrome 플레이어 장치가 필요 없는 개발자 모드에서 Chrome Browser 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 수행하십시오.
>
>1. [여기](https://download.macromedia.com/screens/)를 클릭하여 최신 Chrome Player를 다운로드합니다.
>1. 압축을 풀고 디스크에 저장합니다.
>1. Chrome 브라우저를 열고 메뉴에서 **확장 프로그램**&#x200B;을 선택하거나 ***chrome://extensions***&#x200B;로 직접 이동합니다.
>1. 오른쪽 상단 모서리에서 **개발자 모드**&#x200B;를 전환합니다.
>1. 왼쪽 상단 모서리에서 **압축 해제**&#x200B;를 클릭하고 압축 해제된 Chrome 플레이어를 로드합니다.
>1. 확장 목록에서 사용 가능한 경우 **AEM Screens Chrome Player** 플러그인을 확인하십시오.
>1. 새 탭을 열고 왼쪽 상단 모서리에서 **Apps** 아이콘을 클릭하거나 ***chrome://apps***&#x200B;로 직접 이동합니다.
>1. **AEM Screens** 플러그인을 클릭하여 Chrome Player를 시작합니다. 기본적으로 플레이어가 전체 화면 모드로 실행됩니다. 전체 화면 모드를 종료하려면 **esc** 키를 누릅니다.


Chrome OS 플레이어가 켜져 있으면 아래 단계에 따라 Chrome 장치를 등록합니다.

1. AEM 인스턴스에서 프로젝트의 **장치** 폴더로 이동합니다.

1. 작업 표시줄에서 **장치 관리자**&#x200B;를 탭/클릭합니다.

   ![이미지](assets/kickstart/demo-register1.png)

1. 오른쪽 상단에 있는 **장치 등록**&#x200B;을 탭/클릭합니다.

1. 필요한 장치를 선택하고 **장치 등록**&#x200B;을 탭/클릭합니다.

   ![이미지](assets/kickstart/demo-register2.png)

1. 장치가 등록 코드를 전송할 때까지 기다렸다가 Chrome 장치에서 **등록 코드**를 동시에 확인합니다.
   ![이미지](assets/kickstart/demo-register3.png)

1. **등록 코드**&#x200B;가 두 컴퓨터에서 동일한 경우 AEM에서 **유효성 검사**&#x200B;를 탭/클릭합니다.

1. 원하는 이름을 장치의 **ChromeDeviceforDemo**&#x200B;로 설정하고 **등록**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-register4.png)

1. **장치 등록 성공** 대화 상자에서 **디스플레이 지정**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-register5.png)

1. 디스플레이 경로를 **DemoScreens** —> **위치** —> **TestLocation** —> **LobbyDisplay**&#x200B;로 선택하고 **할당**&#x200B;을 클릭합니다.

   ![이미지](assets/kickstart/demo-device6.png)

1. 장치가 성공적으로 할당되면 다음 확인 메시지가 표시됩니다.

   ![이미지](assets/kickstart/demo-register8.png)

1. **완료**&#x200B;를 탭/클릭하여 등록 프로세스를 완료합니다. 디스플레이 대시보드에서 등록된 장치를 볼 수 있어야 합니다.

   ![이미지](assets/kickstart/demo-register9.png)

### Chrome 플레이어에서 컨텐츠 보기 {#viewing-content-output}

채널의 모든 자산이 이제 Chrome OS 플레이어에서 재생됩니다.

이제 AEM Screens 채널에서 콘텐츠를 재생합니다!

![이미지](assets/kickstart/demo-video-screens.gif)
