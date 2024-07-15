---
title: 텍스트 오버레이
description: 이미지 위에 오버레이된 제목 또는 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있는 AEM Screens의 텍스트 오버레이에 대해 알아봅니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
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
>**텍스트 오버레이** 기능은 AEM 6.3 기능 팩 5 또는 AEM 6.4 기능 팩 3을 설치한 경우에만 사용할 수 있습니다.

## 개요 {#overview}

텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능입니다. 이미지 위에 오버레이된 제목 또는 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다.

사용자 지정 구성 요소를 만드는 방법에 대해 알아보려면 **AEM Screens 구성 요소 확장**&#x200B;을 참조하십시오.

이 섹션에서는 AEM Screens 프로젝트에서 포스터 구성 요소를 사용하고 적용하는 방법에 대해서만 설명합니다. 또한 시퀀스 채널 중 하나에서 텍스트 오버레이로 사용하는 사례를 보여 줍니다.

## 텍스트 오버레이 사용 {#using-text-overlay}

다음 섹션에서는 AEM Screens 프로젝트에서의 텍스트 오버레이 사용에 대해 설명합니다.

**전제 조건**

이 기능을 구현하려면 먼저 텍스트 오버레이 구현을 시작하기 위한 필수 조건으로 프로젝트를 설정해야 합니다. 예:

* AEM Screens 프로젝트 만들기(이 예제에서는 **TextOverlayDemo**)

* **Channels** 폴더 아래에 **TextSample**(으)로 제목이 지정된 시퀀스 채널을 만듭니다.

* **TextSample** 채널에 콘텐츠 추가

다음 이미지는 **Channels** 폴더에 **TextSample** 채널이 있는 **TextOverlayDemo** 프로젝트를 보여 줍니다.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

AEM Screens 채널에서 텍스트 오버레이를 사용하려면 아래 단계를 따르십시오.

1. **TextOverlayDemo** > **채널** > **TextSample**&#x200B;로 이동하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 이미지를 클릭하고 **구성**(렌치 아이콘)을 클릭하여 속성 대화 상자를 엽니다.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 아래 그림과 같이 대화 상자의 탐색 모음에서 **텍스트 오버레이** 옵션을 클릭합니다.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 텍스트 오버레이 속성 이해 {#understanding-text-overlay-properties}

텍스트 오버레이 속성을 사용하여 Screens 프로젝트의 구성 요소에 텍스트를 추가할 수 있습니다. 다음 섹션에서는 텍스트 오버레이에서 사용할 수 있는 속성에 대한 개요를 제공합니다.

![텍스트](assets/text.gif)

텍스트 상자에 텍스트를 추가하고 굵게, 기울임꼴, 밑줄 등 입력 강조를 추가할 수 있습니다.

**색상 변형** 이 옵션을 사용하면 텍스트가 어둡게(검정색 텍스트) 또는 밝게(흰색 텍스트) 중 하나가 됩니다.

**크기 조정 및 위치 지정** 이 옵션을 사용하면 사용자가 텍스트를 가로 또는 세로로 정렬할 수 있으며 텍스트 맞춤에는 세분화된 도구를 사용할 수도 있습니다.

>[!NOTE]
>
>세분화된 도구를 사용할 때는 (px)를 접미사(예: 200px)로 사용하여 올바른 위치를 픽셀 단위로 식별해야 합니다. 이 표현식의 결과는 시작점에서 200픽셀입니다.

## 텍스트 오버레이에서 ContextHub 값 사용 {#using-text-overlay-context-hub}

다음 섹션에서는 텍스트 오버레이 구성 요소의 Google Sheets와 같은 데이터 스토어의 값 사용에 대해 설명합니다.

**전제 조건**

AEM Screens 프로젝트에 대한 ContextHub 구성을 설정합니다.

데이터 저장소를 사용하여 데이터 기반 자산 변경 내용을 설정하고 관리하는 방법에 대한 자세한 내용은 [AEM Screens에서 ContextHub 구성](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub)을 참조하세요.

프로젝트에 필요한 구성을 설정한 후 아래 단계에 따라 Google 시트의 값을 사용하십시오.

1. **TextOverlayDemo** > **채널** > **TextSample**&#x200B;로 이동하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

1. ContextHub 구성을 설정하려면 **Personalization** 탭을 클릭하십시오.

   1. **libs** > **설정** > **cloudsettings** > **기본** > **ContextHub 구성**(으)로 **ContextHub 경로**&#x200B;를 클릭하고 **선택**&#x200B;을 클릭합니다.

   1. **conf** > **screens** > **설정** > **wcm** > **세그먼트**(으)로 **세그먼트 경로**&#x200B;를 클릭하고 **선택**&#x200B;을 클릭합니다.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      >
      >처음에 ContextHub 구성 및 세그먼트를 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![이미지1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. **TextOverlayDemo** > **채널** > **TextSample**&#x200B;로 이동하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 이 페이지의 [텍스트 오버레이 사용](/help/user-guide/text-overlay.md#using-text-overlay) 섹션에 설명된 대로 이미지 및 텍스트 오버레이 구성 요소를 이미지에 추가하십시오.

1. **구성**(렌치 아이콘)을 클릭하여 **이미지** 대화 상자를 엽니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. **이미지** 대화 상자에서 **ContextHub** 탭으로 이동합니다. **추가**&#x200B;를 클릭합니다.

   >[!NOTE]
   >ContextHub 구성을 설정하지 않은 경우 프로젝트에 대해 이 옵션이 비활성화됩니다.

1. **자리 표시자** 필드에 **값**&#x200B;을(를) 입력하십시오. **ContextHub 변수**&#x200B;에서 Google 시트에서 값을 가져올 행을 클릭합니다. 이 경우 값은 Google 시트의 행 2 및 열 1에서 검색됩니다. 이제 아래 그림과 같이 **기본값**&#x200B;을(를) **20**(으)로 입력하십시오. 완료되면 확인 표시를 클릭합니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >다음 이미지는 Google 시트에서 검색한 값을 보여 줍니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 아래 그림과 같이 이미지 대화 상자에서 **텍스트 오버레이** 탭으로 돌아가서 *현재 온도 {Value}* 텍스트를 추가합니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. **미리 보기**&#x200B;를 클릭합니다.

   ![이미지1](/help/user-guide/assets/text-overlay/text-overlay10.png)
