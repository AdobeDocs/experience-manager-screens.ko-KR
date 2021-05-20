---
title: 프로젝트 수준 이미지 재생 기간
seo-title: 프로젝트 수준 이미지 재생 기간
description: '이 기능을 사용하면 프로젝트 수준에서 이미지 재생 기간을 정의할 수 있습니다. '
seo-description: '이 기능을 사용하면 프로젝트 수준에서 이미지 재생 기간을 정의할 수 있습니다. '
contentOwner: jsyal
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# 프로젝트 수준 이미지 재생 기간 {#project-level-image-playback}

## 개요 {#overview}

이 기능을 사용하면 프로젝트 수준에서 이미지 재생 기간을 정의할 수 있습니다. 모든 이미지는 기본적으로 이 재생 기간을 상속합니다. 프로젝트 수준에서 지속 시간이 정의되지 않으면 기본 재생 8초가 계속 재생됩니다.

### 전제 조건 {#prerequisites}

이 기능을 사용하기 전에 이 기능 구현을 시작하기 위한 전제 조건으로 프로젝트를 설정해야 합니다. 예,

1. AEM Screens 프로젝트를 만듭니다(이 예에서 **ProjectLevelPlayback**)

1. **채널** 폴더 아래에 **PlayBackChannel**&#x200B;으로 시퀀스 채널을 만듭니다

1. **PlayBackChannel**&#x200B;에 컨텐츠 추가

   ![assets](assets/image_playback1.png)

   예를 들어 다음 이미지는 **PlayBackChannel** 편집기에 추가된 이미지를 보여줍니다.

   ![assets](assets/image_playback2.png)

## 프로젝트 수준 이미지 재생 시간 할당 편집 {#editing-project-level-image-playback-duration-assignment}

아래 섹션에서는 AEM Screens 프로젝트에서 컨텐츠의 재생 기간을 편집하는 방법을 설명합니다.

### 프로젝트 수준 {#updating-the-playback-duration-for-images-in-a-project}에서 이미지의 재생 기간 업데이트


>[!NOTE]
>
>이미지 또는 채널 수준 재생 기간을 업데이트하려면 [채널 수준 이미지 재생 기간](channel-level-image-playback.md)을(를) 참조하십시오.

프로젝트 수준 이미지 재생 기간을 업데이트하는 방법을 배우려면 아래 단계를 따르십시오.

1. 프로젝트 **ProjectLevelPlayback** 로 이동하고 작업 표시줄에서 **속성**을 클릭합니다.
   ![assets](assets/image_playback3.png)

1. 채널에서 모든 이미지를 선택하고 왼쪽 상단의 렌치 아이콘(아래 그림에 표시된 대로)을 클릭하여 채널 수준 구성 대화 상자를 엽니다.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **** 페이지 대화 상자가 열립니다.

   >[!NOTE]
   >
   >기본적으로 채널에 있는 이미지는 8초의 재생 기간으로 설정되고 비디오가 기본 지속 시간에 재생됩니다.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   **기간**&#x200B;을 8000(ms)에서 3000(ms)으로, 즉 3초로 편집합니다. **페이지** 대화 상자의 오른쪽 상단에 있는 확인 표시를 클릭하여 변경 사항을 저장합니다.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 결과 보기 {#viewing-the-result}

채널 재생 지속 시간을 업데이트하면(이 예에서는 세 개의 이미지 모두) 이제 이미지가 8초(기본값)가 아닌 3초 동안 재생됩니다.

![channel_preview](assets/channel_preview.gif)

