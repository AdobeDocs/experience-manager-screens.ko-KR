---
title: 비디오 패딩 워크플로우 만들기
seo-title: 비디오 패딩 워크플로우 만들기
description: 자산에 대한 워크플로우에서 비디오 패딩을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: 자산에 대한 워크플로우에서 비디오 패딩을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: 스크린 작성
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 7%

---

# 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow}

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **전제 조건**
* **비디오 패딩 워크플로우 만들기**
   * **워크플로우 만들기**
   * **AEM Screens 프로젝트에서 워크플로우 사용**

* **워크플로우에 대한 출력 유효성 검사**

## 개요 {#overview}

다음 사용 사례에는 비디오를 배치하는 작업이 포함됩니다(예: 1920 x 1080인 채널에서 1280 x 720) 비디오를 0x0(왼쪽 위)에 배치할 수 있습니다. 비디오는 어떤 식으로든 확장하거나 수정해서는 안 되며 비디오 구성 요소에서 **Cover**&#x200B;를 사용하지 마십시오.

비디오는 픽셀 1부터 픽셀 720까지 픽셀 1에서 픽셀 1280까지 오브젝트로 표시되며 나머지 채널은 기본 색상으로 표시됩니다.

## 전제 조건 {#prerequisites}

비디오에 대한 워크플로우를 만들기 전에 다음 사전 요구 사항을 완료하십시오.

1. AEM 인스턴스의 **Assets** 폴더에 비디오를 업로드합니다
1. 아래 그림과 같이 AEM Screens 프로젝트(예: **TestVideoRendition**)와 (**VideoRendering**)를 만듭니다.

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow-1}

비디오 패딩 워크플로우를 만들려면 비디오용 워크플로우를 만든 다음 AEM Screens 프로젝트 채널에서 사용해야 합니다.

아래 절차에 따라 워크플로우를 만들고 사용하십시오.

1. 워크플로우 만들기
1. AEM Screens 프로젝트에서 워크플로우 사용

### 워크플로우 만들기 {#creating-a-workflow}

아래 절차에 따라 비디오에 대한 워크플로우를 만드십시오.

1. AEM 인스턴스로 이동하고 사이드 레일에서 도구를 클릭합니다. **워크플로우** —> **모델**&#x200B;을 선택하여 새 모델을 만듭니다.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. **모델** —> **만들기** —> **모델 만들기**&#x200B;를 클릭합니다. **워크플로우 모델 추가**&#x200B;에 **제목**(**VideoRendition**)과 **이름**&#x200B;을 입력합니다. **완료** 를 클릭하여 워크플로우 모델을 추가합니다.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 워크플로우 모델을 만들면 모델(**VideoRendition**)을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **명령줄** 구성 요소를 워크플로우로 끌어서 놓습니다.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. **명령줄** 구성 요소를 선택하고 속성 대화 상자를 엽니다.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. **인수** 탭을 선택하여 **명령줄 - 단계 속성** 대화 상자에 필드를 입력합니다.

   **Mime 유형**(***비디오/mp4***)에 형식을 입력하고 명령을 (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=black&quot; cq5dam.video.fullhd-hp.mp4***)으로 입력하여 **명령** 필드에서 워크플로우를 시작합니다.

   아래 메모에서 **Mime 유형** 및 **명령**&#x200B;에 대한 세부 정보를 참조하십시오.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 워크플로우(**VideoRenditions**)를 선택하고 작업 표시줄에서 **워크플로우 시작**&#x200B;을 클릭하여 **워크플로우 실행** 대화 상자를 엽니다.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. **페이로드**(***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)에서 자산의 경로를 선택하고 **제목**&#x200B;을 ***RunVideo***&#x200B;로 입력하고 **실행**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens 프로젝트에서 워크플로우 사용 {#using-the-workflow-in-an-aem-screens-project}

AEM Screens 프로젝트에서 워크플로우를 사용하려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트(**TestVideoRendition** —> **채널** —>**VideoRendition**)로 이동합니다.

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 처음에 업로드한 비디오를 **Assets**&#x200B;에 끌어다 놓습니다.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 비디오를 업로드했으면 **미리 보기**&#x200B;를 클릭하여 출력을 확인합니다.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 워크플로우에 대한 출력 유효성 검사 {#validating-the-output-for-the-workflow}

다음 방법으로 출력의 유효성을 검사할 수 있습니다.

* 채널에서 비디오 미리 보기 확인
* 아래 그림과 같이 CRXDE Lite의 ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***&#x200B;로 이동합니다.

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
