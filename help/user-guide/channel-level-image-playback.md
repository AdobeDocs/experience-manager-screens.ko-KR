---
title: 채널 레벨 벌크 이미지 재생 기간
seo-title: 채널 레벨 벌크 이미지 재생 기간
description: 이 페이지에서는 특정 이미지 구성 요소의 재생 시간을 편집하는 방법에 대해 설명합니다.
seo-description: 이 페이지에서는 특정 이미지 구성 요소의 재생 시간을 편집하는 방법에 대해 설명합니다.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 7%

---


# 채널 수준 벌크 이미지 재생 지속 시간 {#channel-level-bulk-image-playback-duration}

## 개요 {#overview}

시퀀스 채널을 만들고 여기에 이미지를 추가하면 기본적으로 모든 이미지는 채널 레벨 구성에 정의된 재생 지속 시간을 가정하게 됩니다. 개별 이미지는 여전히 기본값을 무시할 수 있으며 재생 시간이 다를 수 있습니다. 이는 특정 이미지 구성 요소의 재생 시간을 편집하여 수행합니다.

### 전제 조건 {#prerequisites}

이 기능 구현을 시작하기 전에 이 기능 구현을 시작하기 위한 전제 조건으로 프로젝트를 설정해야 합니다. 예,

1. AEM Screens 프로젝트 예 **ChannelLevelPlayback**&#x200B;을 만듭니다.

1. **채널** 폴더 아래에 **PlaybackChannel**&#x200B;으로 시퀀스 채널을 만듭니다.

1. **PlaybackChannel**&#x200B;에 컨텐츠를 추가합니다.

## 채널 수준 이미지 재생 시간 할당 편집 {#editing-channel-level-image-playback-duration-assignment}

아래 섹션에서는 AEM Screens 채널에서 컨텐츠의 재생 시간을 편집하는 방법에 대해 설명합니다.

### 채널 {#updating-the-playback-duration-for-images-in-a-channel}에서 이미지의 재생 기간 업데이트

채널 레벨 이미지 재생 기간 할당을 업데이트하는 방법을 알려면 아래 단계를 따르십시오.

1. 시퀀스 채널 **PlaybackChannel**&#x200B;으로 이동합니다.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 아래 그림과 같이 채널 편집기에서 두 개 이상의 이미지를 추가합니다.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 채널에서 모든 이미지를 선택하고 왼쪽 상단에 있는 공구 모양 아이콘(아래 그림에 표시된 대로)을 클릭하여 채널 수준 구성 대화 상자를 엽니다.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **페이지** 대화 상자가 열립니다.

   >[!NOTE]
   >기본적으로 채널의 이미지는 재생 지속 시간이 8초로 설정됩니다.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   **지속 시간**&#x200B;을 8000(ms)에서 3000(ms)까지, 즉 3초를 편집합니다. **페이지** 대화 상자의 오른쪽 상단에 있는 확인 표시를 클릭하여 변경 사항을 저장합니다.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 결과 보기 {#viewing-the-result}

채널 재생 지속 시간(이 예에서는 세 개 이미지 모두)을 업데이트하면 이미지가 8초(기본값)이 아니라 3초 동안 재생된다는 것을 알 수 있습니다.

![channel_preview](assets/channel_preview.gif)

