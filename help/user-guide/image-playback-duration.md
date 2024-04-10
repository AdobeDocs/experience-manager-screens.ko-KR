---
title: 이미지 재생 기간
description: AEM Screens의 이미지 재생 기간에 대해 알아봅니다.
contentOwner: jsyal
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# 이미지 재생 기간 {#image-playback-duration}

## 개요 {#overview}

시퀀스 채널을 만들고 여기에 이미지를 추가하면 기본적으로 모든 이미지가 채널 레벨 구성에 정의된 재생 기간을 가정합니다. 개별 이미지는 여전히 기본값을 재정의하고 다른 재생 시간을 가질 수 있습니다. 이는 특정 이미지 구성 요소의 재생 시간을 편집하여 수행됩니다.

### 사전 요구 사항 {#prerequisites}

이 기능을 구현하려면 먼저 이 기능을 구현하기 위한 필수 조건으로 프로젝트를 설정해야 합니다. 예:

1. AEM Screens 프로젝트 만들기(이 예에서는 **ChannelLevelPlayback**)
1. 다음으로 시퀀스 채널 만들기 **PlaybackChannel** 아래에 **채널** 폴더
1. 콘텐츠 추가 **PlaybackChannel**

## 채널 수준 이미지 재생 기간 할당 편집 {#editing-channel-level-image-playback-duration-assignment}

아래 섹션에서는 AEM Screens 채널에서 컨텐츠 재생 기간을 편집하는 방법에 대해 설명합니다.

### 채널에서 이미지의 재생 시간 업데이트 {#updating-the-playback-duration-for-images-in-a-channel}

채널 수준 이미지 재생 기간 할당을 업데이트하는 방법을 배우려면 아래 단계를 따르십시오.

1. 시퀀스 채널로 이동합니다. **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 클릭 **편집** 작업 표시줄에서

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 아래 그림과 같이 채널 편집기에 이미지를 두 개 이상 추가합니다.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 채널의 모든 이미지를 선택하고 아래 그림과 같이 왼쪽 상단의 렌치 아이콘을 선택합니다. 채널 수준 구성 대화 상자가 열립니다.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **페이지** 대화 상자가 열립니다.

   >[!NOTE]
   >
   >기본적으로 채널의 이미지는 재생 시간(8초)으로 설정됩니다.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   편집 **기간** 8000(밀리초)부터 3000(밀리초)까지, 즉 3초입니다. 오른쪽 상단의 확인 표시를 클릭합니다. **페이지** 대화 상자를 통해 변경 사항을 저장할 수 있습니다.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 결과 보기 {#viewing-the-result}

채널 재생 지속 시간(이 예에서는 세 개의 이미지 모두)을 업데이트한 경우 이미지가 이제 8초(기본값)가 아닌 3초 동안 재생됩니다.

![channel_preview](assets/channel_preview.gif)

