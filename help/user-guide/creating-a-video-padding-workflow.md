---
title: 비디오 패딩 워크플로우 만들기
description: 에셋용 워크플로에서 비디오 패딩 만들기에 대해 자세히 알아보십시오.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow}

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **전제 조건**
* **비디오 패딩 워크플로 만들기**
   * **워크플로 만들기**
   * **AEM Screens 프로젝트에서 워크플로 사용**

* **워크플로우에 대한 출력 확인**

## 개요 {#overview}

다음 사용 사례에는 디스플레이가 1920 x 1080인 채널에 비디오를 배치하고(예: 1280 x 720) 비디오를 0x0(왼쪽 상단)에 배치하는 작업이 포함됩니다. 비디오를 어떤 방식으로든 늘리거나 수정해서는 안 되며 비디오 구성 요소에서 **커버**&#x200B;를 사용하지 마십시오.

비디오는 픽셀 1로부터 픽셀 1280까지, 픽셀 1로부터 픽셀 720까지 이르는 객체로서 표시된다. 채널의 나머지 부분이 기본 색상입니다.

## 사전 요구 사항 {#prerequisites}

비디오에 대한 워크플로우를 만들기 전에 다음 사전 요구 사항을 완료하십시오.

1. AEM 인스턴스의 **Assets** 폴더에 비디오 업로드
1. 아래 그림과 같이 AEM Screens 프로젝트(예: **TestVideoRendering**)와 채널 이름(**VideoRendering**)을 만듭니다.

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow-1}

비디오 패딩 워크플로우를 만들려면 비디오에 대한 워크플로우를 만든 다음 AEM Screens 프로젝트 채널에서 동일한 워크플로우를 사용합니다.

워크플로우를 만들고 사용하려면 아래 단계를 따르십시오.

1. 워크플로우 만들기
1. AEM Screens 프로젝트에서 워크플로우 사용

### 워크플로우 만들기 {#creating-a-workflow}

비디오에 대한 워크플로우를 만들려면 아래 단계를 따르십시오.

1. AEM 인스턴스로 이동합니다.
1. 측면 레일에서 도구를 클릭합니다.
1. 모델을 만들 수 있도록 **워크플로** > **모델**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. **모델** > **만들기** > **모델 만들기**&#x200B;를 클릭합니다. **워크플로 모델 추가**&#x200B;에서 **제목**(예: **VideoRendition**)과 **이름**&#x200B;을(를) 입력하십시오. 워크플로 모델을 추가하려면 **완료**&#x200B;를 클릭하십시오.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 워크플로 모델을 만든 후 모델(**VideoRendition**)을 클릭하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **`Command Line`** 구성 요소를 워크플로우로 끌어서 놓습니다.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. **`Command Line`** 구성 요소를 클릭하고 속성 대화 상자를 엽니다.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. **인수** 탭을 클릭합니다.
1. **명령줄 - 단계 속성** 대화 상자에서 **Mime 유형**(***video/mp4***)에 형식을 입력하고 명령을 (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***)로 입력합니다. 이 명령은 **명령** 필드에서 워크플로를 시작합니다.

   아래 노트에서 **MIME 유형** 및 **명령**&#x200B;에 대한 세부 정보를 참조하십시오.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 워크플로(**VideoRenditions**)를 클릭합니다.
1. 작업 표시줄에서 **워크플로 시작**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. **워크플로 실행** 대화 상자에서 **페이로드**(***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)에서 에셋의 경로를 클릭하고 **제목**&#x200B;을(를) ***RunVideo***(으)로 입력한 다음 **실행**&#x200B;을(를) 클릭합니다.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens 프로젝트에서 워크플로우 사용 {#using-the-workflow-in-an-aem-screens-project}

AEM Screens 프로젝트에서 워크플로우를 사용하려면 아래 단계를 따르십시오.

1. AEM Screens 프로젝트(**TestVideoRendition** > **채널** >**VideoRendition**)로 이동합니다.

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 처음에 **Assets**&#x200B;에 업로드한 비디오를 끌어서 놓습니다.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 비디오를 업로드했으면 **미리 보기**&#x200B;를 클릭하여 출력을 확인합니다.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 워크플로우에 대한 출력 확인 {#validating-the-output-for-the-workflow}

다음을 수행하여 출력의 유효성을 검사할 수 있습니다.

* 채널에서 비디오 미리보기 확인
* 아래 그림과 같이 CRXDE Lite에서 ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***(으)로 이동합니다.

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
