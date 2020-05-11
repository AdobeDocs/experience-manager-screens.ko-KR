---
title: 다중 영역 레이아웃
seo-title: 다중 영역 레이아웃
description: 다중 영역 레이아웃을 사용하면 여러 영역 컨텐츠를 만들고 단일 화면에서 결합할 수 있는 비디오, 이미지 및 텍스트와 같은 다양한 에셋을 사용할 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
seo-description: 다중 영역 레이아웃을 사용하면 여러 영역 컨텐츠를 만들고 단일 화면에서 결합할 수 있는 비디오, 이미지 및 텍스트와 같은 다양한 에셋을 사용할 수 있습니다. 자세한 내용은 이 페이지를 참조하십시오.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: e33175a8c4282d89ed77fc430b1a48eb8470585f
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 6%

---


# 다중 영역 레이아웃 {#multi-zone-layout}

다음 페이지에서는 다중 영역 레이아웃의 사용에 대해 설명하고 다음 주제를 다룹니다.

* 개요
* 다중 영역 레이아웃 만들기
* 전제 조건
* 하나 이상의 영역에서 단일 자산 사용
* 하나 이상의 영역에서 순차적 컨텐츠 사용

## 개요 {#overview}

***다중 영역 레이아웃을*** 사용하면 여러 영역 컨텐츠를 만들고 단일 화면에서 결합할 수 있는 비디오, 이미지 및 텍스트와 같은 다양한 에셋을 사용할 수 있습니다. 이미지, 비디오 및 텍스트를 가져와서 모두 함께 혼합하고 직관적인 디지털 경험을 만들 수 있습니다.

프로젝트 요구 사항에 따라 채널에서 여러 영역이 필요하고 이를 하나의 포괄적인 단위로 편집하는 경우가 있습니다. 예를 들어, 단일 채널의 분리된 세 영역에서 관련 소셜 미디어 피드가 실행되는 제품 시퀀스가 있습니다.

## 다중 영역 레이아웃 만들기 {#creating-multi-zone-layout}

채널을 만드는 동안 채널에서 영역을 만들려면 다른 템플릿을 사용할 수 있습니다. 하나의 이미지, 비디오 또는 포함된 채널을 추가하여 여러 자산을 하나의 시퀀스에 표시할 수 있습니다.

### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 다중 영역 레이아웃 구현을 시작하기 위한 사전 요구 사항으로 프로젝트를 준비했는지 확인하십시오. 예,

* 영역으로 제목이 있는 AEM Screens 프로젝트 **만들기**
* MultiZoneDisplay라는 **위치**&#x200B;에&#x200B;**표시 만들기**

영역 프로젝트에서 **다중** 영역 **으로** 제목이 지정된 채널을만듭니다. 아래 단계를 따르십시오.

**채널 만들기**

1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 **스크린**&#x200B;을 선택합니다. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. 채널 **폴더로** 이동하고 작업 **모음에서** 만들기를 클릭합니다.

1. 만들기 **마법사에서 왼쪽 L-바 분할 화면** 채널을 **선택합니다** .

1. [ **다음** ]을 클릭하고 **제목을** 다중 영역 **으로**&#x200B;입력합니다.

1. 만들기를 **클릭하여** 채널 만들기를 완료합니다.

![screen_shot_2018-12-07at120026pm](assets/screen_shot_2018-12-07at120026pm.png)

### 하나 이상의 영역에서 단일 자산 사용 {#using-single-assets-in-one-or-more-zones}

이미지 또는 비디오와 같은 단일 자산을 세 개의 서로 다른 모든 영역에서 사용할 수 있습니다. 구현하려면 아래 절차를 따르십시오.

1. **채널에 컨텐츠 추가**

   1. 영역 **—> 채널** **—>**&#x200B;다중 영역&#x200B;**으로**&#x200B;이동합니다.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.
   ![screen_shot_2018-12-07at14917pm](assets/screen_shot_2018-12-07at14917pm.png)

1. **채널에 이미지 추가**

   3개 영역 모두에서 단일 이미지나 비디오를 재생하려면 아래에 표시된 대로 채널 편집기에 이미지를 드래그하여 놓으면 됩니다.

   ![new1-1](assets/new1-1.gif)

### 하나 이상의 영역에서 순차적 컨텐츠 사용 {#using-sequenced-content-in-one-or-more-zones}

영역에 세 개의 다른 영역에 이미지 또는 컨텐츠의 시퀀스 및 정적 이미지를 표시하려면 아래 단계를 따르십시오.

1. **채널 폴더 만들기**

   1. 영역 —> **MultiZone** —> 채널 **** 으로 **이동하고 작업** 표시줄에서 **** 만들기를 클릭합니다.
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **채널 폴더에 두 개 더 추가**

   1. 영역 —> **채널****—>** 포함된 채널 **** 으로 이동하고 작업 표시줄에서 **** 만들기를 클릭합니다.
   1. 만들기 **마법사에서** 시퀀스 채널 **을** 선택하여 **영역** 1로 명명된 채널을만듭니다.
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. 이미지를 드래그하여 이 채널에 놓습니다.
   마찬가지로, EmbeddedChannels 폴더에 **Zone2라는** 다른 시퀀스 채널 **을** 만듭니다.

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Zone1 **시퀀스 채널의 편집기에 추가된 이미지는** 아래에표시되어 있습니다.

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-1.png)

   Zone2 **시퀀스 채널 편집기에 추가된 이미지는 아래에** 표시되어 있습니다.

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-2.png)

1. **기본 채널에 포함된 시퀀스/구성 요소 추가(다중 영역)**

   1. 영역 **—> 채널** **** —> **다중 영역**&#x200B;으로이동합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.
   1. 포함된 시퀀스 **구성** 요소를 두 영역 중 하나로 드래그하여 놓습니다.

1. **세 영역 모두에 컨텐츠 추가**

   1. 영역 **—> 채널** **** —> **다중 영역**&#x200B;으로이동합니다.
   1. 영역 중 하나에서 포함된 시퀀스를 선택합니다.
   1. 편집기에 포함된 시퀀스 중 하나에 **대한 구성** (렌치) 아이콘을 클릭합니다.
   1. 아래 그림에 표시된 대로 채널 경로를 **영역** —> **채널** —> **포함된 채널** —> **Zone1**&#x200B;으로 선택합니다.
   마찬가지로, 편집기의 다른 포함된 **시퀀스 구성 요소에 Zone2** 를 추가합니다.

   ![이미지](/help/user-guide/assets/multi-zone/multizone-3.png)

#### 결과 보기 {#viewing-the-result}

위의 단계를 사용하여 다중 영역 레이아웃을 구현하면 아래 그림과 같이 다음 출력이 표시됩니다.

Screens 플레이어의 다음 출력은 서로 다른 세 영역의 컨텐츠를 표시합니다. 왼쪽 및 오른쪽 영역(모두 구성 요소로 포함된 시퀀스를 사용)은 이미지 시퀀스를 표시하고 아래 영역에는 정적 이미지가 표시됩니다.

![new2-1](/help/user-guide/assets/multi-zone/screens-multi1.gif)


