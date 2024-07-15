---
title: 프로젝트 수준 이미지 재생 기간
description: 프로젝트 수준에서 이미지 재생 기간을 정의하는 방법을 알아봅니다.
contentOwner: jsyal
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# 프로젝트 수준 이미지 재생 기간 {#project-level-image-playback}

## 개요 {#overview}

이 기능을 사용하면 프로젝트 수준에서 이미지 재생 기간을 정의할 수 있습니다. 모든 이미지는 기본적으로 이 재생 기간을 상속합니다. 프로젝트 수준에서 지속 시간이 정의되지 않은 경우 기본 재생인 8초가 계속됩니다.

### 사전 요구 사항 {#prerequisites}

이 기능을 사용하기 전에 프로젝트를 필수 구성 요소로 설정하여 이 기능을 구현하십시오. 예:

1. AEM Screens 프로젝트를 만듭니다(이 예제에서는 **ProjectLevelPlayback**).
1. **채널** 폴더 아래에 시퀀스 채널을 **PlayBackChannel**(으)로 만듭니다.
1. **PlayBackChannel**&#x200B;에 콘텐츠를 추가합니다.

   ![자산](assets/image_playback1.png)

   예를 들어 다음 이미지는 **PlayBackChannel** 편집기에 추가된 이미지를 보여 줍니다.

   ![자산](assets/image_playback2.png)

## 프로젝트 수준 이미지 재생 기간 할당 편집 {#editing-project-level-image-playback-duration-assignment}

아래 섹션에서는 AEM Screens 프로젝트에서 컨텐츠 재생 기간을 편집하는 방법에 대해 설명합니다.

### 프로젝트 수준에서 이미지 재생 기간 업데이트 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>이미지 또는 채널 수준 재생 기간을 업데이트하려면 [채널 수준 이미지 재생 기간](channel-level-image-playback.md)을 참조하세요.

프로젝트 수준 이미지 재생 기간을 업데이트하는 방법을 알려면 아래 단계를 따르십시오.

1. 프로젝트 **ProjectLevelPlayback**(으)로 이동하고 작업 표시줄에서 **속성**을 클릭합니다.
   ![자산](assets/image_playback3.png)

1. 채널의 모든 이미지를 클릭하고 아래 그림과 같이 왼쪽 상단의 렌치 아이콘을 클릭하여 채널 수준 구성 대화 상자를 열 수 있습니다.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **페이지** 대화 상자가 열립니다.

   >[!NOTE]
   >
   >기본적으로 채널의 이미지는 재생 시간(8초)으로 설정되고 비디오는 기본 지속 시간에 재생됩니다.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   **기간**&#x200B;을(를) 8000(밀리초)에서 3000(밀리초)까지(즉, 3초) 편집합니다. 변경 내용이 저장되도록 **페이지** 대화 상자의 오른쪽 맨 위에 있는 확인 표시를 선택합니다.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 결과 보기 {#viewing-the-result}

채널 재생 기간(이 예에서는 세 개의 이미지 모두)을 업데이트한 후 이미지가 8초(기본값)가 아닌 3초 동안 재생됩니다.

![channel_preview](assets/channel_preview.gif)

