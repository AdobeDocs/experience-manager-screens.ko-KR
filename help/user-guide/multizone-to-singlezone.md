---
title: MultiZone에서 SingleZone 전환 사용 사례
description: MultiZone에서 SingleZone 전환 사용 사례에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone에서 SingleZone 전환 사용 사례
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 2%

---


# 다중 영역을 단일 영역으로 전환 {#multizone-to-singlezone-use-case}


## 사용 사례 설명 {#use-case-description}

이 섹션에서는 단일 영역 레이아웃 채널과 대체되는 다중 영역 레이아웃 채널을 설정하는 방법을 강조하는 사용 사례 예제를 설명합니다. 다중 영역 채널에는 시퀀스 이미지/비디오 에셋이 있으며, 다중 영역에서 단일 영역으로 또는 그 반대로 바뀌는 프로젝트를 설정하는 방법을 보여줍니다.

### 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주 배우 {#primary-actors}

컨텐츠 작성자

## 프로젝트 {#setting-up-the-project} 설정

아래 절차에 따라 프로젝트를 설정하십시오.

1. 아래와 같이 **TakeoverLoop**&#x200B;라는 AEM Screens 프로젝트를 만듭니다.

   ![자산](assets/mz-to-sz1.png)


1. **다중 영역 스크린 채널 만들기**

   1. **채널** 폴더를 선택하고 작업 표시줄에서 **만들기**&#x200B;를 클릭하여 채널을 만드는 마법사를 엽니다.
   1. 마법사에서 **왼쪽-L 막대 분할 화면 채널**&#x200B;을 선택하고 **MultiZoneLayout**&#x200B;이라는 이름의 채널을 만듭니다.
   1. 채널에 컨텐츠를 추가합니다. 자산을 각 영역으로 드래그하여 놓습니다. 다음 예제는 아래에 표시된 것처럼 비디오, 이미지 및 텍스트 배너(포함된 시퀀스)로 구성된 **MultiZoneLayout** 채널을 보여줍니다.

   ![자산](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >채널에서 다중 영역 레이아웃을 만드는 방법에 대한 자세한 내용은 [다중 영역 레이아웃](multi-zone-layout-aem-screens.md)을 참조하십시오.


1. **채널** 폴더에 **TakeoverChannel**&#x200B;이라는 이름의 다른 채널을 만듭니다.

   ![자산](assets/mz-to-sz3.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 이 채널에 컨텐츠를 추가합니다. 아래 그림과 같이 이 채널에 전환할 **채널** 구성 요소 및 이미지 자산을 추가합니다.

   ![자산](assets/mz-to-sz4.png)

1. 채널 구성 요소의 설정을 열고 *단계 2*&#x200B;에서 만든 **MultiZoneLayout** 채널을 가리킵니다.

   ![자산](assets/mz-to-sz5.png)

1. **시퀀스** 필드의 지속 시간을 **10000ms**&#x200B;로 설정합니다.

   ![자산](assets/mz-to-sz6.png)

1. 마찬가지로, 이미지(추가한 에셋)에 대한 설정을 열고 **시퀀스** 필드에서 **3000ms**&#x200B;로 기간을 설정합니다.

   ![자산](assets/mz-to-sz7.png)

## 미리 보기 {#checking-the-preview} 확인

플레이어에서 원하는 출력을 보거나 편집기에서 **미리 보기**&#x200B;를 클릭하기만 하면 됩니다.

출력에서는 다중 영역 레이아웃이 *1000ms*&#x200B;에 대해 재생되는 방식을 보여 주고 재생 기간이 *3000ms*&#x200B;인 단일 영역 레이아웃으로 전환한 다음 다시 다중 영역 레이아웃으로 전환합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>필요에 따라 채널 전환(다중 영역에서 단일 영역 레이아웃으로 또는 그 반대로)을 사용자 정의할 수 있습니다.