---
title: MultiZone에서 SingleZone으로 전환 사용 사례
description: MultiZone에서 SingleZone으로 전환 사용 사례에 대해 배울 수 있도록 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# 다중 영역에서 단일 영역으로 전환 {#multizone-to-singlezone-use-case}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 단일 영역 레이아웃 채널과 교대로 반복되는 다중 영역 레이아웃 채널을 설정하는 방법에 중점을 둔 사용 사례 예를 설명합니다. 멀티존 채널에는 시퀀싱 이미지/비디오 자산이 있으며 멀티존에서 단일 존으로, 그리고 역으로 프로젝트를 설정하는 방법을 보여 줍니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해했는지 확인하십시오.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[일정 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 기본 작업자 {#primary-actors}

콘텐츠 작성자

## 프로젝트 설정 {#setting-up-the-project}

프로젝트를 설정하려면 아래 단계를 따르십시오.

1. 아래와 같이 이름이 **TakeoverLoop**&#x200B;인 AEM Screens 프로젝트를 만듭니다.

   ![자산](assets/mz-to-sz1.png)


1. **다중 영역 Screens 채널 만들기**

   1. 채널을 만들 수 있도록 **채널** 폴더를 클릭하고 작업 표시줄에서 **만들기**&#x200B;를 클릭한 다음 마법사를 엽니다.
   1. 마법사에서 **왼쪽 L 표시줄 분할 화면 채널**&#x200B;을(를) 클릭하고 제목이 **MultiZoneLayout**&#x200B;인 채널을 만듭니다.
   1. 채널에 컨텐츠를 추가합니다. 자산을 각 영역에 끌어다 놓습니다. 다음 예제에서는 비디오, 이미지 및 텍스트 배너(포함된 순서로)를 구성하는 **MultiZoneLayout** 채널을 보여 줍니다.

   ![자산](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >채널에서 다중 영역 레이아웃을 만드는 방법에 대한 자세한 내용은 [다중 영역 레이아웃](multi-zone-layout-aem-screens.md)을 참조하세요.


1. **채널** 폴더에 **TakeoverChannel**(으)로 제목이 지정된 다른 채널을 만듭니다.

   ![자산](assets/mz-to-sz3.png)

1. 이 채널에 콘텐츠를 추가할 수 있도록 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 아래 그림과 같이 이 채널에 대해 전환할 **채널** 구성 요소와 이미지 자산을 추가합니다.

   ![자산](assets/mz-to-sz4.png)

1. 채널 구성 요소의 설정을 열고 *2단계*&#x200B;에서 만든 **MultiZoneLayout** 채널을 가리킵니다.

   ![자산](assets/mz-to-sz5.png)

1. **시퀀스** 필드의 기간을 **밀리초&lbrace;310000(으)로 설정합니다.**

   ![자산](assets/mz-to-sz6.png)

1. 마찬가지로 이미지(추가한 자산)에 대한 설정을 열고 기간을 **시퀀스** 필드에서 **3,000밀리초**(으)로 설정합니다.

   ![자산](assets/mz-to-sz7.png)

## 미리보기 확인 {#checking-the-preview}

플레이어에서 원하는 출력을 보거나 편집기에서 **미리 보기**&#x200B;를 선택하면 됩니다.

출력에서는 다중 영역 레이아웃이 *밀리초* 10000 재생되는 방식을 보여 줍니다. 그런 다음 재생 기간이 *3000밀리초*&#x200B;인 단일 영역 레이아웃으로 전환합니다. 그리고 마지막으로 다중 영역 레이아웃으로 다시 전환합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>필요에 따라 채널 전환을 사용자 정의할 수 있습니다(다중 영역에서 단일 영역 레이아웃으로 또는 반대로).
