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
source-git-commit: 9e267326da9c8163d85402425e6b46886e4d19f9
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 4%

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


### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 다음에 대한 개념 지식을 확인하십시오.

* [AEM Screens 프로젝트 만들기](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [디스플레이 만들기](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [디스플레이에 채널 지정](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 다중 영역 레이아웃 만들기 {#creating-multi-zone-layout}

채널을 만드는 동안 채널에서 영역을 만들려면 다른 템플릿을 사용할 수 있습니다. 하나의 이미지, 비디오 또는 포함된 채널을 추가하여 여러 자산을 하나의 시퀀스에 표시할 수 있습니다.

**채널 만들기**

1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 **스크린**&#x200B;을 선택합니다. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. 채널 **폴더로** 이동하고 작업 **모음에서** 만들기를 클릭합니다.

1. 만들기 마법사에서 **1x2 분할 화면** 채널 **을** 선택합니다.

1. [ **다음** ]을 클릭하고 **제목을** 다중 영역 **으로**&#x200B;입력합니다.

1. 만들기를 **클릭하여** 채널 만들기를 완료합니다.

### 하나 이상의 영역에서 단일 자산 사용 {#using-single-assets-in-one-or-more-zones}

이미지 또는 비디오와 같은 단일 자산을 세 개의 서로 다른 모든 영역에서 사용할 수 있습니다. 구현하려면 아래 절차를 따르십시오.

1. **채널에 컨텐츠 추가**

   1. 영역 **—> 채널** ****—> **다중 영역**&#x200B;으로이동합니다.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.

1. **채널에 이미지 추가**

   두 영역에서 단일 이미지나 비디오를 재생하려면 아래 그림과 같이 채널 편집기의 각 영역에 이미지를 드래그하여 놓으면 됩니다.

   ![이미지](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 하나 이상의 영역에서 순차적 컨텐츠 사용 {#using-sequenced-content-in-one-or-more-zones}

영역에 두 개의 다른 영역에 이미지 및 비디오 시퀀스를 표시하려면 아래 단계를 따르십시오.

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

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   아래 그림과 같이 **Zone2** 시퀀스 채널의 편집기에 비디오를 추가합니다.

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **기본 채널(다중 영역)에 포함된 시퀀스(구성 요소 추가**

   1. 영역 **—> 채널** **** —> **다중 영역**&#x200B;으로이동합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.
   1. 포함된 시퀀스 **구성** 요소를 두 영역 중 하나로 드래그하여 놓습니다.
   1. 영역 중 하나에서 포함된 시퀀스를 선택합니다.
   1. 편집기에 포함된 시퀀스 중 하나에 **대한 구성** (렌치) 아이콘을 클릭합니다.
   1. 아래 그림에 표시된 대로 채널 경로를 **영역** —> **채널** —> **포함된 채널** —> **Zone1**&#x200B;으로 선택합니다.
   1. 마찬가지로, 편집기의 다른 포함된 **시퀀스 구성 요소에 Zone2** 를 추가합니다.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-3.png)

### 위치 및 디스플레이 생성 {#creating-location}

Screens 플레이어에서 컨텐츠를 보려면 위치 및 디스플레이를 만들어야 합니다. 아래 절차에 따라 위치와 디스플레이를 만드십시오.

1. **위치 생성**

   1. 영역 **—> 위치** **폴더로** 이동합니다.
   1. 위치 **폴더를** 선택하고 작업 **모음에서** 만들기를 클릭합니다.
   1. **만들기** 마법사 **에서** 위치를 선택하고 **다음을**&#x200B;클릭합니다.
   1. Enter the **Title** as **SanJose** and click **Create**.

1. **디스플레이 만들기**

   1. 영역 **—> 위치** **폴더로** 이동합니다.
   1. SanJose **위치를** 선택하고 작업 **모음에서** 만들기를 클릭합니다.
   1. **만들기** 마법사 **에서** 표시를 선택하고 **다음을**&#x200B;클릭합니다.
   1. Enter the **Title** as **Lobby** and click **Create**.

### 디스플레이에 채널 지정 {#channel-channel}

컨텐츠를 보려면 채널을 디스플레이에 지정해야 합니다. 아래 절차에 따라 디스플레이에 채널을 지정합니다.

1. **디스플레이에 채널 지정**

   1. Zones **—>** Locations **—>** SanJose **—>** LobbyCover ****&#x200B;로 이동합니다.
   1. [ **로비** ] 표시를 선택하고 작업 **표시줄에서 [채널** 할당]을 클릭합니다.
   1. 채널 경로에 **다중 영역** 채널 경로를 **입력합니다**.
   1. 지원되는 이벤트 **를** 초기 **로드**, **유휴 화면**&#x200B;및 **으로**&#x200B;설정합니다.
   1. **저장**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 마찬가지로, 다른 두 개의 포함된 채널(**Zone1** 및 **Zone2**)을 이 디스플레이에 할당해야 합니다.
   1. 로비 **디스플레이에 세 개** 채널을 모두 할당하면 디스플레이 대시보드에서 지정된 채널을 볼 수 있습니다.

      ![이미지](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!I역정]
      > 주 채널(이 경우 **다중 영역**)을 디스플레이에 할당하면 다른 두 개의 포함된 채널 **Zone1** 및 **Zone2** 도 동일한 디스플레이에할당해야 합니다.

### 장치 등록 {#registering-device}

위치 및 디스플레이를 설정하고 나면 아래 단계에 따라 장치를 등록하고 장치에 디스플레이를 할당합니다.

1. **장치 등록**

   1. 영역 **—> 장치** **폴더로** 이동합니다.
   1. Select the **Devices** folder and click **Device Manager** from the action bar.
   1. 장치 **등록을** 클릭하고 목록에서 보류 중인 장치를 선택합니다.
      >[!NOTE]
      > 장치의 제목은 [장치 등록]**탭** 에 표시된 장치 토큰( **토큰** 필드)과 일치해야 합니다.
   1. 제목이 장치 토큰과 일치하는 경우 장치를 선택하고 작업 표시줄에서 **장치** 등록을 클릭합니다.
   1. 등록 코드가 Screens 플레이어 **장치 등록** 탭의 코드와 일치하는 경우 작업 표시줄에서 **유효성 검사** 를 클릭합니다.
      ![이미지](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Enter the **Title** as **Chrome-Device1** and click **Register**.
   1. 디스플레이 **할당을** 선택하고 장치 구성의 경로를 선택합니다.
   >[!NOTE]
   >Screens 플레이어에서 컨텐츠를 보려고 하는 경우 채널 대시보드에서 **오프라인 컨텐츠** 업데이트를 클릭해야 합니다.

#### 결과 보기 {#viewing-the-result}

이전 단계를 사용하여 다중 영역 레이아웃을 구현하면 다음 출력이 표시됩니다.

서로 다른 두 영역에 컨텐츠를 표시하는 출력을 보려면 Screens 플레이어를 선택합니다. 왼쪽 및 오른쪽 영역(둘 다 포함된 시퀀스를 구성 요소로 사용).

왼쪽 영역은 시퀀스 채널이고 오른쪽 영역에는 비디오가 포함됩니다.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


