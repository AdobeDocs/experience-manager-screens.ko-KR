---
title: MultiZone에서 SingleZone으로 전환 사용 사례
description: MultiZone에서 SingleZone으로 전환 사용 사례에 대해 배울 수 있도록 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---

# 다중 영역에서 단일 영역으로 전환 {#multizone-to-singlezone-use-case}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 단일 영역 레이아웃 채널과 교대로 반복되는 다중 영역 레이아웃 채널을 설정하는 방법에 중점을 둔 사용 사례 예를 설명합니다. 다중 영역 채널에는 시퀀스 이미지/비디오 자산이 있으며 다중 영역에서 단일 영역으로 또는 그 반대로 반복되는 프로젝트를 설정하는 방법을 보여 줍니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해했는지 확인하십시오.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 생성 및 관리](managing-locations.md)**
* **[일정 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 기본 작업자 {#primary-actors}

콘텐츠 작성자

## 프로젝트 설정 {#setting-up-the-project}

프로젝트를 설정하려면 아래 단계를 따르십시오.

1. (이)라는 이름의 AEM Screens 프로젝트 만들기 **TakeoverLoop**&#x200B;아래에 표시된 대로 를 클릭합니다.

   ![자산](assets/mz-to-sz1.png)


1. **다중 영역 화면 채널 만들기**

   1. 다음을 클릭합니다. **채널** 폴더 및 클릭 **만들기** 을 클릭하고 마법사를 열어 채널을 만들 수 있습니다.
   1. 클릭 **왼쪽-L 막대 분할 화면 채널** 마법사에서 라는 이름의 채널을 만들고 **다중 영역 레이아웃**.
   1. 채널에 컨텐츠를 추가합니다. 자산을 각 영역에 끌어다 놓습니다. 다음 예제는 **다중 영역 레이아웃** 아래 표시된 대로 비디오, 이미지 및 텍스트 배너(포함된 시퀀스)로 구성된 채널.

   ![자산](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >채널에서 다중 영역 레이아웃을 만드는 방법에 대한 자세한 내용은 [다중 영역 레이아웃](multi-zone-layout-aem-screens.md).


1. 이라는 다른 채널 만들기 **TakeoverChannel** (으)로 **채널** 폴더를 삭제합니다.

   ![자산](assets/mz-to-sz3.png)

1. 클릭 **편집** 이 채널에 컨텐츠를 추가할 수 있도록 작업 표시줄에서 을 선택합니다. 추가 **채널** 아래 그림과 같이 이 채널에 대해 전환할 구성 요소 및 이미지 자산

   ![자산](assets/mz-to-sz4.png)

1. 채널 구성 요소에 대한 설정을 열고 다음을 가리킵니다. **다중 영역 레이아웃** 만든 채널 *2단계*.

   ![자산](assets/mz-to-sz5.png)

1. 다음에서 기간을 설정합니다. **시퀀스** 필드 대상 **10000밀리초**.

   ![자산](assets/mz-to-sz6.png)

1. 마찬가지로 이미지(추가한 에셋)에 대한 설정을 열고 **시퀀스** 필드 대상 **3000밀리초**.

   ![자산](assets/mz-to-sz7.png)

## 미리보기 확인 {#checking-the-preview}

플레이어에서 또는 을 선택하여 원하는 출력을 볼 수 있습니다 **미리 보기** 편집기에서 가져왔습니다.

출력은에 대한 다중 영역 레이아웃이 재생되는 방식을 보여 줍니다 *10000밀리초* 재생 기간이 인 단일 영역 레이아웃으로 전환합니다. *3000밀리초* 그런 다음 다중 영역 레이아웃으로 다시 전환합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>필요에 따라 채널 전환을 사용자 정의할 수 있습니다(다중 영역에서 단일 영역 레이아웃으로 또는 반대로).
