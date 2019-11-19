---
title: 텍스트 오버레이
seo-title: 텍스트 오버레이
description: 텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 제목이나 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
seo-description: 텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 제목이나 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 텍스트 오버레이 {#text-overlay}

이 섹션에서는 다음과 같은 주제를 다룹니다.

* **개요**
* **텍스트 오버레이 사용**
* **전제 조건**
* **텍스트 오버레이 속성 이해**

>[!CAUTION]
>
>텍스트 **오버레이** 기능은 AEM 6.3 기능 팩 5 또는 AEM 6.4 기능 팩 3을 설치한 경우에만 사용할 수 있습니다.

## 개요 {#overview}

텍스트 오버레이는 AEM Screens에서 사용할 수 있는 기능으로, 이미지 위에 제목이나 설명을 제공하여 시퀀스 채널에서 매력적인 경험을 만들 수 있습니다.

고유한 사용자 지정 구성 요소를 만드는 방법에 대한 자세한 내용은 AEM Screens 구성 **요소 확장을 참조하십시오**.

이 섹션에서는 AEM Screens 프로젝트에서 포스터 구성 요소를 사용하고 활용하는 방법을 소개하고 시퀀스 채널 중 하나에서 텍스트 오버레이로 사용하는 방법을 보여줍니다.

## 텍스트 오버레이 사용 {#using-text-overlay}

다음 섹션에서는 AEM Screens 프로젝트에서 텍스트 오버레이를 사용하는 방법에 대해 설명합니다.

### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 텍스트 오버레이 구현을 시작하기 위한 전제 조건으로 프로젝트를 설정해야 합니다. 예,

* AEM Screens 프로젝트 만들기(이 예에서는 TextOverlayDemo ****)

* 채널 폴더 아래에 **TextSample** 으로 채널을 **만듭니다**

* TextSample 채널에 **컨텐츠** 추가

다음 이미지는 채널 폴더에 **TextSample** 채널이 있는 **TextOverlayDemo** 프로젝트를 **보여줍니다** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. TextOverlayDemo **데모** —&gt; 채널 **—&gt;** 텍스트 **샘플로 이동하고** 편집을 **** 클릭하여 작업 표시줄에서 편집기를 엽니다.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 이미지를 선택하고 구성( **렌치** 아이콘)을 클릭하여 속성 대화 상자를 엽니다.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 아래 **그림과 같이** 대화 상자의 탐색 막대에서 텍스트 오버레이 옵션을 선택합니다.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 텍스트 오버레이 속성 이해 {#understanding-text-overlay-properties}

텍스트 오버레이 속성을 사용하여 스크린 프로젝트의 구성 요소에 텍스트를 추가할 수 있습니다. 다음 섹션에서는 텍스트 오버레이에서 사용할 수 있는 속성에 대한 개요를 제공합니다.

![텍스트](assets/text.gif)

텍스트 상자에 텍스트를 추가하고 굵게, 기울임체, 밑줄 등과 같은 타이포그래피 강조를 추가할 수 있습니다.

**색상 변형** 이 옵션을 사용하면 텍스트를 어둡게(검은색 텍스트) 또는 밝게(흰색 텍스트)로 지정할 수 있습니다.

**크기 조정 및 위치** 지정 이 옵션을 사용하면 텍스트를 가로 또는 세로로 정렬하거나 텍스트 정렬을 위해 세밀하게 정렬된 도구를 사용할 수 있습니다.

>[!NOTE]
>
>세밀하게 정렬된 툴을 제대로 사용하려면 접미어로(px)를 사용하여 올바른 위치를 픽셀 단위로 식별하십시오(예: 200px). 이 표현식의 결과는 시작점으로부터 200픽셀이 됩니다.

