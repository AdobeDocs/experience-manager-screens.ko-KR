---
title: 이미지 재생 지속 시간
seo-title: 이미지 재생 지속 시간
description: 이미지 재생 지속 시간에 대해 알려면 이 페이지를 따르십시오.
seo-description: 이미지 재생 지속 시간에 대해 알려면 이 페이지를 따르십시오.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49

---


# 이미지 재생 지속 시간 {#image-playback-duration}

## 개요 {#overview}

시퀀스 채널을 만들고 여기에 이미지를 추가하면 기본적으로 모든 이미지는 채널 수준 구성에 정의된 재생 지속 시간을 가정하게 됩니다. 개별 이미지는 여전히 기본값을 재정의할 수 있으며 재생 시간이 다를 수 있습니다. 이는 특정 이미지 구성 요소의 재생 시간을 편집하여 수행할 수 있습니다.

### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 이 기능 구현을 시작하기 위한 전제 조건으로 프로젝트를 설정해야 합니다. 예,

1. AEM Screens 프로젝트 만들기(이 예에서는 ChannelLevelPlayback ****)

1. 채널 폴더 아래에 시퀀스 채널을 **PlaybackChannel** 로 **만들기**

1. PlaybackChannel에 컨텐츠 **추가**

## 채널 레벨 이미지 재생 지속 시간 할당 편집 {#editing-channel-level-image-playback-duration-assignment}

아래 섹션에서는 AEM Screens 채널에서 컨텐츠의 재생 기간을 편집하는 방법에 대해 설명합니다.

### 채널에서 이미지의 재생 지속 시간 업데이트 {#updating-the-playback-duration-for-images-in-a-channel}

아래 절차에 따라 채널 레벨 이미지 재생 지속 시간 할당을 업데이트하는 방법을 알아보십시오.

1. 시퀀스 채널 PlaybackChannel로 **이동합니다**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 아래 그림과 같이 채널 편집기에서 두 개 이상의 이미지를 추가합니다.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 채널에서 모든 이미지를 선택하고 왼쪽 상단에 있는 공구 모양 아이콘(아래 그림에 표시된 대로)을 클릭하여 채널 수준 구성 대화 상자를 엽니다.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **페이지** 대화 상자가 열립니다.

   >[!NOTE]
   >
   >기본적으로 채널의 이미지는 재생 지속 시간 8초로 설정됩니다.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   지속 **시간을** 8000(ms)에서 3000(ms)까지, 즉 3초로 편집합니다. 페이지 대화 상자의 오른쪽 상단에 있는 **확인** 표시를 클릭하여 변경 사항을 저장합니다.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 결과 보기 {#viewing-the-result}

채널 재생 지속 시간(이 예에서는 3개 이미지 모두)을 업데이트하면 이미지가 8초 대신 3초 동안 재생됩니다(기본값).

![channel_preview](assets/channel_preview.gif)

