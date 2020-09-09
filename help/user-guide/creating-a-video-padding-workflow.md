---
title: 비디오 패딩 작업 과정 만들기
seo-title: 비디오 패딩 작업 과정 만들기
description: 자산에 대한 워크플로우에서 비디오 패딩 만들기에 대해 알려면 이 페이지를 따르십시오.
seo-description: 자산에 대한 워크플로우에서 비디오 패딩 만들기에 대해 알려면 이 페이지를 따르십시오.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 7%

---


# 비디오 패딩 작업 과정 만들기 {#creating-a-video-padding-workflow}

이 섹션에서는 다음과 같은 주제를 다룹니다.

* **개요**
* **전제 조건**
* **비디오 패딩 작업 과정 만들기**
   * **워크플로우 만들기**
   * **AEM Screens 프로젝트에서 워크플로우 사용**

* **워크플로우에 대한 출력 유효성 확인**

## 개요 {#overview}

다음 사용 사례에는 비디오 배치(예:1280 x 720) - 1920 x 1080이고 비디오를 0x0(왼쪽 위)에 배치할 수 있는 채널입니다. 비디오는 어떤 식으로든 늘리거나 수정해서는 안 되며 비디오 구성 요소에서 **표지** 를 사용하지 마십시오.

이 비디오는 픽셀 1부터 픽셀 1280까지 픽셀 1부터 픽셀 720까지 모두 하나의 개체로 표시되며 나머지 채널은 기본 색상이 됩니다.

## 전제 조건 {#prerequisites}

비디오 작업 과정을 만들기 전에 다음 사전 요구 사항을 완료하십시오.

1. AEM 인스턴스의 **자산** 폴더에 비디오 업로드
1. 아래 그림과 같이 AEM Screens 프로젝트(예: **TestVideoRendition**)와 채널(**VideoRendering**)을 만듭니다.

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 비디오 패딩 작업 과정 만들기 {#creating-a-video-padding-workflow-1}

비디오 패딩 워크플로우를 만들려면 비디오에 대한 워크플로우를 만든 다음 AEM Screens 프로젝트 채널에서 동일하게 사용해야 합니다.

아래 절차에 따라 워크플로우를 만들고 사용하십시오.

1. 워크플로우 만들기
1. AEM Screens 프로젝트에서 워크플로우 사용

### 워크플로우 만들기 {#creating-a-workflow}

아래 절차에 따라 비디오에 대한 워크플로우를 만드십시오.

1. AEM 인스턴스로 이동하고 측면 레일에서 도구를 클릭합니다. 워크플로우 **** —> **모델** 을 선택하여 새 모델을 생성합니다.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 모델 **—>** 만들기 **—> 모델** 만들기를 **클릭합니다**. Add Workflow Model에 **제목** ( **VideoRendition**)과 **이름** 을 ****&#x200B;입력합니다. 완료 **를** 클릭하여 워크플로우 모델을 추가합니다.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 워크플로우 모델을 생성하고 나면 모델(**VideoRendition**)을 선택하고 작업 표시줄에서 **편집을** 클릭합니다.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 명령줄 **구성 요소를 워크플로우로** 드래그하여 놓습니다.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 명령줄 **구성 요소를** 선택하고 속성 대화 상자를 엽니다.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. [ **인수** ] 탭을 선택하여 **명령줄 - 단계 속성** 대화 상자에 필드를 입력합니다.

   MIME 형식 **(** video/mp4 ***)의 형식을 입력하고 명령을 (****/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=color=black&quot; cq5dam.video.fullhd-hp.mp4* **) 명령(Commands)***&#x200B;필드에서 워크플로우를 **** 시작합니다.

   아래 메모에서 MIME 형식 **및** 명령 **에** 대한 자세한 내용을 참조하십시오.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 워크플로우(**VideoRenditions**)를 선택하고 작업 **표시줄에서 워크플로우** 시작을 클릭하여 워크플로우 **실행** 대화상자를엽니다.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 페이로드 **(예:** /content/dam/dam/husefinyda-501_512kb 2 ***)에서 자산의 경로를 선택하고*** Grollx **GrollxVideoRun** VideoRun 및 Click Runs ***VideoGloss*** ****&#x200B;로 Connect Title을 입력합니다.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens 프로젝트에서 워크플로우 사용 {#using-the-workflow-in-an-aem-screens-project}

AEM Screens 프로젝트의 워크플로우를 사용하려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트(TestVideoRendition **—>** 채널 **—>** VideoRendition **)로 이동합니다**.

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. 처음에 자산에 업로드한 비디오를 드래그하여 **놓습니다**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 비디오를 업로드한 후에는 미리 보기 **를** 클릭하여 출력을 확인합니다.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 워크플로우에 대한 출력 유효성 확인 {#validating-the-output-for-the-workflow}

다음과 같이 출력물의 유효성을 확인할 수 있습니다.

* 채널에서 비디오 미리 보기 확인
* 아래 그림과 같이 CRXDE Lite의 ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** 로 이동합니다.

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

