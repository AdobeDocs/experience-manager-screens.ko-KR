---
title: 다중 영역 레이아웃
seo-title: 다중 영역 레이아웃
description: 다중 영역 레이아웃 을 사용하면 여러 영역 컨텐츠를 만들고 비디오, 이미지 및 텍스트와 같은 다양한 자산을 단일 화면에서 결합할 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
seo-description: 다중 영역 레이아웃 을 사용하면 여러 영역 컨텐츠를 만들고 비디오, 이미지 및 텍스트와 같은 다양한 자산을 단일 화면에서 결합할 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: 스크린 작성
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 8%

---

# 다중 영역 레이아웃 {#multi-zone-layout}

다음 페이지에서는 다중 영역 레이아웃의 사용에 대해 설명하고 다음 주제를 다룹니다.

* 개요
* 다중 영역 레이아웃 만들기
* 전제 조건
* 하나 이상의 영역에서 단일 자산 사용
* 하나 이상의 영역에서 시퀀스 컨텐츠 사용

## 개요 {#overview}

***다중 영역 레이아웃*** 을 사용하면 여러 영역 컨텐츠를 만들고 비디오, 이미지 및 텍스트와 같은 다양한 자산을 단일 화면에서 결합할 수 있습니다. 이미지, 비디오 및 텍스트를 가져와서 모두 함께 혼합하여 직관적인 디지털 경험을 만들 수 있습니다.

프로젝트 요구 사항에 따라 채널에서 여러 영역이 필요하고 이를 하나의 포괄적인 단위로 편집하는 경우가 있습니다. 예를 들어, 단일 채널의 분리된 세 영역에서 관련된 소셜 미디어 피드가 실행 중인 제품 시퀀스가 있을 수 있습니다.


### 전제 조건 {#prerequisites}

이 기능 구현을 시작하기 전에 다음 사항에 대한 개념적 지식이 있는지 확인하십시오.

* [AEM Screens 프로젝트 만들기](https://docs.adobe.com/content/help/ko-KR/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [디스플레이 만들기](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [디스플레이에 채널 지정](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 다중 영역 레이아웃 만들기 {#creating-multi-zone-layout}

채널을 만드는 동안 채널에서 영역을 만들기 위해 다른 템플릿을 사용할 수 있습니다. 단일 이미지, 비디오 또는 포함된 채널을 추가하여 여러 자산을 시퀀스로 표시할 수 있습니다.

**채널 생성**

1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 **스크린**&#x200B;을 선택합니다. 또는 다음 위치로 바로 이동할 수 있습니다. `http://localhost:4502/screens.html/content/screens`
1. **채널** 폴더로 이동하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

1. **만들기** 마법사에서 **1x2 분할 화면 채널**&#x200B;을 선택합니다.

1. **다음**&#x200B;을 클릭하고 **title**&#x200B;을 **MultiZone**&#x200B;으로 입력합니다.

1. **만들기**&#x200B;를 클릭하여 채널 만들기를 완료합니다.

### 하나 이상의 영역에서 단일 자산 사용 {#using-single-assets-in-one-or-more-zones}

모든 개별 영역에서 이미지 또는 비디오와 같은 단일 자산을 사용할 수 있습니다. 구현하려면 아래 절차를 따르십시오.

1. **채널에 컨텐츠 추가**

   1. **영역** —> **채널**—> **다중 영역**&#x200B;으로 이동합니다.
   1. **MultiZone** 채널을 선택하고 작업 표시줄에서 **편집** 을 클릭하여 편집기를 엽니다.

1. **채널에 이미지 추가**

   두 영역에서 단일 이미지나 비디오를 재생하려면 아래 그림과 같이 채널 편집기의 각 영역에 이미지를 끌어다 놓으면 됩니다.

   ![이미지](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 하나 이상의 영역에서 시퀀스 컨텐츠 사용 {#using-sequenced-content-in-one-or-more-zones}

영역에 다른 영역에 이미지 시퀀스와 비디오가 표시되도록 하려면 아래 단계를 수행하여 자세한 내용을 확인하십시오.

1. **채널 폴더 만들기**

   1. **영역** —> **MultiZone** —> **채널**&#x200B;으로 이동하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. **만들기** 마법사에서 **채널 폴더**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.
   1. 제목을 **EmbeddedChannels**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **채널 폴더에 두 개의 채널 추가**

   1. **Zones** —> **채널** —> **EmbeddedChannels**&#x200B;로 이동하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. **만들기** 마법사에서 **시퀀스 채널**&#x200B;을 선택하여 **Zone1**&#x200B;이라는 이름의 채널을 만듭니다.
   1. **Zone1** 을 선택하고 작업 표시줄에서 **편집** 을 클릭하여 편집기를 엽니다.
   1. 몇 개의 이미지를 이 채널에 끌어다 놓습니다.
   1. 마찬가지로 **EmbeddedChannels** 폴더에서 **Zone2**&#x200B;로 명명된 다른 시퀀스 채널을 만듭니다.
   1. 비디오를 이 채널에 끌어다 놓습니다.

   다음 그림은 **Zone1** 및 **Zone2** 채널을 보여줍니다.

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   **Zone1** 시퀀스 채널의 편집기에 추가된 이미지는 아래와 같습니다.

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   **Zone2** 시퀀스 채널의 편집기에 추가된 비디오는 아래에 표시되어 있습니다.

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **기본 채널(MultiZone)에 포함된 시퀀스(구성 요소) 추가**

   1. **영역** —> **채널** —> **다중 영역**&#x200B;으로 이동합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.
   1. **포함된 시퀀스** 구성 요소를 두 영역으로 끌어다 놓습니다.
   1. 영역 중 하나에서 포함된 시퀀스를 선택합니다.
   1. 편집기에 포함된 시퀀스 중 하나에 해당하는 **구성** (공구모양) 아이콘을 클릭합니다.
   1. 채널 경로를 아래 그림과 같이 **영역** —> **채널** —> **포함된 채널** —> **영역1**&#x200B;으로 선택합니다.
   1. 마찬가지로 **Zone2**&#x200B;을 편집기의 다른 포함된 시퀀스 구성 요소에 추가하십시오.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-3.png)

### 위치 및 디스플레이 생성 {#creating-location}

Screens 플레이어에서 컨텐츠를 보려면 위치 및 디스플레이를 만들어야 합니다. 위치 및 디스플레이를 생성하려면 아래 절차를 따르십시오.

1. **위치 생성**

   1. **영역** —> **위치** 폴더로 이동합니다.
   1. **위치** 폴더를 선택하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. **만들기** 마법사에서 **위치**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.
   1. **제목** 을 **SanJose**&#x200B;로 입력하고 **만들기**&#x200B;를 클릭합니다.

1. **디스플레이 만들기**

   1. **영역** —> **위치** 폴더로 이동합니다.
   1. **SanJose** 위치를 선택하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. **만들기** 마법사에서 **표시**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.
   1. **제목**&#x200B;을 **Lobby**&#x200B;으로 입력하고 **만들기**&#x200B;를 클릭하십시오.

### 디스플레이에 채널 지정 {#channel-channel}

컨텐츠를 보려면 채널을 디스플레이에 지정해야 합니다. 아래 절차에 따라 디스플레이에 채널을 지정하십시오.

1. **디스플레이에 채널 지정**

   1. **영역** —> **위치** —> **SanJose**—> **Lobby**&#x200B;로 이동합니다.
   1. **Lobby** 디스플레이를 선택하고 작업 표시줄에서 **채널 지정**&#x200B;을 클릭합니다.
   1. **채널 경로**&#x200B;에 **MultiZone** 채널의 경로를 입력합니다.
   1. **지원되는 이벤트**&#x200B;를 **초기 로드**, **유휴 화면** 및 **타이머**&#x200B;로 설정합니다.
   1. **저장**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 마찬가지로, 다른 두 개의 포함된 채널(**Zone1** 및 **Zone2**)을 이 디스플레이에 할당해야 합니다.
   1. 세 채널을 모두 **Lobby** 표시에 할당하면 디스플레이 대시보드에서 지정된 채널을 볼 수 있습니다.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 주 채널을 디스플레이에 할당하면(이 경우, **MultiZone**), 포함된 다른 두 채널 **Zone1** 및 **Zone2**&#x200B;도 동일한 디스플레이에 할당해야 합니다.

### 장치 등록 {#registering-device}

위치 및 디스플레이를 설정하고 나면 아래 단계에 따라 장치를 등록하고 디스플레이를 장치에 할당합니다.

1. **장치 등록**

   1. **영역** —> **장치** 폴더로 이동합니다.
   1. **장치** 폴더를 선택하고 작업 표시줄에서 **장치 관리자**&#x200B;를 클릭합니다.
   1. **장치 등록**&#x200B;을 클릭하고 목록에서 보류 중인 장치를 선택합니다.

      >[!NOTE]
      > 장치의 제목은 **장치 등록** 탭에 표시되는 장치 토큰(**토큰** 필드)과 일치해야 합니다.
   1. 제목이 장치 토큰과 일치하는 경우 장치를 선택하고 작업 표시줄에서 **장치 등록**&#x200B;을 클릭합니다.
   1. 등록 코드가 Screens 플레이어 **Device Registration** 탭의 코드와 일치하는 경우 작업 표시줄에서 **유효성 검사**를 클릭합니다.
      ![이미지](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. **제목**&#x200B;을 **Chrome-Device1**&#x200B;로 입력하고 **등록**&#x200B;을 클릭합니다.
   1. **디스플레이 지정**&#x200B;을 선택하고 장치 구성에 대한 경로를 선택합니다.

   >[!NOTE]
   >Screens 플레이어에서 컨텐츠를 보려는 경우 디스플레이에 지정된 각 채널에 대해 채널 대시보드에서 **오프라인 컨텐츠 업데이트**&#x200B;를 클릭해야 합니다.

### 결과 보기 {#viewing-the-result}

앞의 단계를 사용하여 다중 영역 레이아웃을 구현하면 다음 출력이 표시됩니다.

두 개의 다른 영역에 컨텐츠를 표시하는 출력을 보려면 스크린 플레이어를 선택합니다. 왼쪽 및 오른쪽 영역(둘 다 포함된 시퀀스를 구성 요소로 사용).

왼쪽 영역은 시퀀스 채널이고 오른쪽 영역은 비디오를 포함합니다.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
