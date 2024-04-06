---
title: 텍스트 오버레이
seo-title: Text Overlay
description: 텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 오버레이된 제목이나 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
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
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

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

텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 오버레이된 제목이나 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다.

사용자 지정 구성 요소를 만드는 방법에 대해 알아보려면 을 참조하십시오. **AEM Screens 구성 요소 확장**.

이 섹션에서는 AEM Screens 프로젝트에서 포스터 구성 요소를 사용 및 적용하고 시퀀스 채널 중 하나에서 텍스트 오버레이로 사용하는 방법만 보여 줍니다.

## 텍스트 오버레이 사용 {#using-text-overlay}

다음 섹션에서는 AEM Screens 프로젝트에서의 텍스트 오버레이 사용에 대해 설명합니다.

**전제 조건**

이 기능의 구현을 시작하기 전에 텍스트 오버레이 구현을 시작하기 위한 필수 조건으로 프로젝트를 설정했는지 확인하십시오. 예:

* AEM Screens 프로젝트 만들기(이 예에서는 **TextOverlayDemo**)

* 이라는 이름의 시퀀스 채널 만들기 **텍스트 샘플** 아래에 **채널** 폴더

* 에 콘텐츠 추가 **텍스트 샘플** 채널

다음 이미지는 **TextOverlayDemo** 프로젝트 포함 **텍스트 샘플** 의 채널 **채널** 폴더를 삭제합니다.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

AEM Screens 채널에서 텍스트 오버레이를 사용하려면 아래 단계를 따르십시오.

1. 다음으로 이동 **TextOverlayDemo** > **채널** > **텍스트 샘플** 및 클릭 **편집** 작업 표시줄에서 을 클릭하여 편집기를 엽니다.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 이미지를 선택하고 **구성** (렌치 아이콘) 을 클릭하여 속성 대화 상자를 엽니다.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 다음 항목 선택 **텍스트 오버레이** 아래 그림과 같이 대화 상자의 탐색 모음에서 옵션을 선택합니다.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 텍스트 오버레이 속성 이해 {#understanding-text-overlay-properties}

Text Overlay 속성을 사용하여 Screens 프로젝트의 구성 요소에 텍스트를 추가할 수 있습니다. 다음 섹션에서는 텍스트 오버레이에서 사용할 수 있는 속성에 대한 개요를 제공합니다.

![텍스트](assets/text.gif)

텍스트 상자에 텍스트를 추가하고 굵게, 기울임꼴, 밑줄 등 입력 강조를 추가할 수 있습니다.

**색상 변형** 이 옵션을 사용하면 텍스트가 [어둡게](검정색 텍스트) 또는 [밝게](흰색 텍스트)일 수 있습니다.

**크기 조정 및 위치 지정** 이 옵션을 사용하면 텍스트를 가로 또는 세로로 정렬하거나 텍스트 정렬에 세밀한 도구를 사용할 수 있습니다.

>[!NOTE]
>
>세분화된 도구를 올바르게 사용하려면 (px)를 접미사(예: 200px)로 사용하여 올바른 위치를 픽셀 단위로 식별해야 합니다. 이 표현식의 결과는 시작점에서 200픽셀입니다.

## 텍스트 오버레이에서 ContextHub 값 사용 {#using-text-overlay-context-hub}

다음 섹션에서는 텍스트 오버레이 구성 요소의 Google Sheets와 같은 데이터 스토어의 값 사용에 대해 설명합니다.

**전제 조건**

AEM Screens 프로젝트에 대한 ContextHub 구성을 설정합니다.

데이터 저장소를 사용하여 데이터 기반 에셋 변경 사항을 설정하고 관리하는 방법에 대한 자세한 내용은 [AEM Screens에서 ContextHub 구성](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

프로젝트에 필요한 구성을 설정했으면 아래 단계에 따라 Google Sheets의 값을 사용하십시오.

1. 다음으로 이동 **TextOverlayDemo** > **채널** > **텍스트 샘플** 및 클릭 **속성** 작업 표시줄에서

1. 다음 항목 선택 **개인화** 탭을 사용하여 ContextHub 구성을 설정할 수 있습니다.

   1. 다음 항목 선택 **ContextHub 경로** 다음으로: **리브** > **설정** > **cloudsettings** > **기본값** > **ContextHub 구성** 및 클릭 **선택**.

   1. 다음 항목 선택 **세그먼트 경로** 다음으로: **conf** > **screens** > **설정** > **wcm** > **세그먼트** 및 클릭 **선택**.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      >
      >처음에 ContextHub 구성 및 세그먼트를 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 다음으로 이동 **TextOverlayDemo** > **채널** > **텍스트 샘플** 및 클릭 **편집** 작업 표시줄에서 을 클릭하여 편집기를 엽니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 에 설명된 대로 이미지 및 텍스트 오버레이 구성 요소를 이미지에 추가합니다. [텍스트 오버레이 사용](/help/user-guide/text-overlay.md#using-text-overlay) 섹션에 있는 마지막 항목이 될 필요가 없습니다.

1. 클릭 **구성** (렌치 아이콘) **이미지** 대화 상자.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 다음 위치로 이동 **컨텍스트 허브** 의 탭 **이미지** 대화 상자. 클릭 **추가**.

   >[!NOTE]
   >ContextHub 구성을 설정하지 않은 경우 프로젝트에 대해 이 옵션이 비활성화됩니다.

1. 입력 **값** 다음에서 **자리 표시자** 필드. Google 시트에서 값을 가져올 행을 선택합니다. **ContextHub 변수**. 이 경우 값은 Google 시트의 행 2 및 열 1에서 검색됩니다. 이제 을(를) 입력합니다. **기본값** 다음으로: **20**&#x200B;을 참조하십시오. 완료되면 확인 표시를 클릭합니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >다음 이미지는 Google Sheets에서 검색한 값을 보여 줍니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 다음으로 돌아가기 **텍스트 오버레이** 이미지 대화 상자의 탭을 클릭하고 텍스트를 추가합니다 *현재 온도 {Value}*&#x200B;을 참조하십시오.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 클릭 **미리 보기** 원하는 출력을 봅니다.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
