---
title: 텍스트 오버레이
seo-title: Text Overlay
description: 텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 겹쳐진 제목 또는 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 4%

---

# 텍스트 오버레이 {#text-overlay}

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **텍스트 오버레이 사용**
* **텍스트 오버레이 속성 이해**
* **텍스트 오버레이에서 ContextHub 값 사용**

>[!CAUTION]
>
>다음 **텍스트 오버레이** 이 기능은 AEM 6.3 기능 팩 5 또는 AEM 6.4 기능 팩 3을 설치한 경우에만 사용할 수 있습니다.

## 개요 {#overview}

텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 겹쳐진 제목 또는 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다.

자신만의 사용자 지정 구성 요소를 만드는 방법에 대해 알아보려면 **AEM Screens 구성 요소 확장**.

이 섹션에서는 AEM Screens 프로젝트에서 포스터 구성 요소를 사용 및 적용하고 시퀀스 채널 중 하나에서 텍스트 오버레이로 사용하는 방법을 소개합니다.

## 텍스트 오버레이 사용 {#using-text-overlay}

다음 섹션에서는 AEM Screens 프로젝트에서 텍스트 오버레이를 사용하는 방법에 대해 설명합니다.

**전제 조건**

이 기능 구현을 시작하기 전에 텍스트 오버레이 구현을 시작하기 위한 전제 조건으로 프로젝트를 설정했는지 확인하십시오. 예를 들어

* AEM Screens 프로젝트를 만듭니다(이 예제에서는 **텍스트 오버레이 데모**)

* 라는 이름의 시퀀스 채널을 만듭니다 **텍스트 샘플** 아래에 **채널** 폴더

* 에 컨텐츠 추가 **텍스트 샘플** 채널

다음 이미지는 **텍스트 오버레이 데모** 프로젝트 사용 **텍스트 샘플** 채널 **채널** 폴더를 입력합니다.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

AEM Screens 채널에서 텍스트 오버레이를 사용하려면 아래 절차를 따르십시오.

1. 다음으로 이동 **텍스트 오버레이 데모** —> **채널** —> **텍스트 샘플** 을(를) 클릭합니다. **편집** 작업 표시줄에서 편집기를 엽니다.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 이미지를 선택하고 을(를) 클릭합니다 **구성** (공구모양 아이콘)을 클릭하여 등록 정보 대화 상자를 엽니다.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 을(를) 선택합니다 **텍스트 오버레이** 아래 그림과 같이 대화 상자의 탐색 막대에서 옵션을 선택합니다.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 텍스트 오버레이 속성 이해 {#understanding-text-overlay-properties}

텍스트 오버레이 속성을 사용하여 스크린 프로젝트의 구성 요소에 텍스트를 추가할 수 있습니다. 다음 섹션에서는 텍스트 오버레이에서 사용할 수 있는 속성에 대한 개요를 제공합니다.

![텍스트](assets/text.gif)

텍스트 상자에 텍스트를 추가하고 굵게, 기울임체 및 밑줄과 같은 인쇄 강조를 추가할 수 있습니다.

**색상 변형** 이 옵션을 사용하면 텍스트를 어둡게(검은색 텍스트) 또는 밝게(흰색 색상의 텍스트)로 지정할 수 있습니다.

**크기 조정 및 포지셔닝** 이 옵션을 사용하면 사용자가 텍스트를 가로 또는 세로로 정렬하거나 텍스트 정렬을 위해 세밀하게 정렬된 도구를 사용할 수 있습니다.

>[!NOTE]
>
>세분화된 도구를 올바르게 사용하려면 (px)를 접미어로 사용하여 올바른 위치(예: 200px)를 픽셀 단위로 식별하십시오. 이 식의 결과는 시작점에서 200픽셀입니다.

## 텍스트 오버레이에서 ContextHub 값 사용 {#using-text-overlay-context-hub}

다음 섹션에서는 데이터 저장소의 값 사용(예: 텍스트 오버레이 구성 요소의 google 시트)에 대해 설명합니다.

**전제 조건**

AEM Screens 프로젝트에 대한 ContextHub 구성을 설정합니다.

데이터 저장소를 사용하여 데이터 기반 자산 변경 사항을 설정 및 관리하는 방법에 대해 알아보려면 [AEM Screens에서 ContextHub 구성](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

프로젝트에 필요한 구성을 설정한 후에는 아래 단계에 따라 google 시트의 값을 사용하십시오.

1. 다음으로 이동 **텍스트 오버레이 데모** —> **채널** —> **텍스트 샘플** 을(를) 클릭합니다. **속성** 작업 표시줄.

1. 을(를) 선택합니다 **개인화** 탭을 클릭하여 ContextHub 구성을 설정합니다.

   1. 을(를) 선택합니다 **ContextHub 경로** 로서의 **libs** > **설정** > **cloudsettings** > **기본** > **ContextHub 구성** 을(를) 클릭합니다. **선택**.

   1. 을(를) 선택합니다 **세그먼트 경로** 로서의 **conf** > **screens** > **설정** > **wcm** > **세그먼트** 을(를) 클릭합니다. **선택**.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      >
      >Context Hub 구성 및 세그먼트를 처음 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 다음으로 이동 **텍스트 오버레이 데모** —> **채널** —> **텍스트 샘플** 을(를) 클릭합니다. **편집** 작업 표시줄에서 편집기를 엽니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 에 설명된 대로 이미지에 이미지 및 텍스트 오버레이 구성 요소를 추가합니다. [텍스트 오버레이 사용](/help/user-guide/text-overlay.md#using-text-overlay) 섹션을 참조하십시오.

1. 클릭 **구성** (공구모양 아이콘) **이미지** 대화 상자

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 로 이동합니다 **ContextHub** 탭에서 **이미지** 대화 상자 **추가**&#x200B;를 클릭합니다.

   >[!NOTE]
   >ContextHub 구성을 설정하지 않은 경우 이 옵션은 프로젝트에 대해 비활성화됩니다.

1. Enter 키 **값** 에서 **자리 표시자** 필드. 의 Google 시트에서 값을 가져올 행을 선택합니다 **ContextHub 변수**. 이 경우 값은 Google 시트의 2행 및 1열에서 검색됩니다. 이제 을(를) 입력합니다. **기본값** 로서의 **20년**: 아래 그림과 같습니다. 완료되면 확인 표시를 클릭합니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >참조용으로 다음 이미지에는 google 시트에서 검색된 값이 표시됩니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 로 돌아갑니다. **텍스트 오버레이** 이미지 대화 상자에서 탭을 선택하고 텍스트를 추가합니다 *현재 온도 {Value}*&#x200B;아래 그림과 같이,

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 클릭 **미리 보기** 원하는 출력을 보려면

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
