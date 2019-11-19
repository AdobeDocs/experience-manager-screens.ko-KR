---
title: 비디오 패딩 워크플로우 만들기
seo-title: 비디오 패딩 워크플로우 만들기
description: 이 페이지를 따라 워크플로우에서 자산 패딩 만들기에 대해 알아보십시오.
seo-description: 이 페이지를 따라 워크플로우에서 자산 패딩 만들기에 대해 알아보십시오.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow}

이 섹션에서는 다음과 같은 주제를 다룹니다.

* **개요**
* **전제 조건**
* **비디오 패딩 워크플로우 만들기**
   * **워크플로우 만들기**
   * **AEM Screens 프로젝트에서 워크플로우 사용**

* **워크플로우에 대한 출력 유효성 확인**

## 개요 {#overview}

다음 사용 사례에는 비디오 배치(예:디스플레이가 1920 x 1080이고 비디오가 0x0(왼쪽 위)에 배치된 채널의 1280 x 720). 비디오는 어떤 식으로든 늘리거나 수정해서는 안 되며 비디오 구성 요소에서 **표지를** 사용하지 마십시오.

비디오는 픽셀 1부터 픽셀 1280까지 픽셀 1부터 픽셀 720까지 모두 오브젝트로 표시되며 나머지 채널은 기본 색상이 됩니다.

## 전제 조건 {#prerequisites}

비디오 작업 과정을 만들기 전에 다음 사전 요구 사항을 완료하십시오.

1. AEM 인스턴스의 **자산** 폴더에 비디오 업로드
1. 아래 그림과 같이 AEM Screens 프로젝트(예: **TestVideoRendition**)와 채널(**VideoRendering**)을 만듭니다.

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 비디오 패딩 워크플로우 만들기 {#creating-a-video-padding-workflow-1}

비디오 패딩 작업 과정을 만들려면 비디오에 대한 작업 흐름을 만든 다음 AEM Screens 프로젝트 채널에서 동일하게 사용해야 합니다.

아래 절차에 따라 워크플로우를 만들고 사용합니다.

1. 워크플로우 만들기
1. AEM Screens 프로젝트에서 워크플로우 사용

### 워크플로우 만들기 {#creating-a-workflow}

아래 절차에 따라 비디오에 대한 워크플로우를 만드십시오.

1. AEM 인스턴스로 이동하고 측면 레일에서 도구를 클릭합니다. 워크플로우 **—&gt;** 모델을 선택하여 **** 새 모델을 생성합니다.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 모델 **—&gt; 만들기** —&gt; **모델** **만들기를**&#x200B;클릭합니다. Add Workflow **Model** 에 **Title**(VideoRendition **)과** Name **을**&#x200B;입력합니다. 완료를 **클릭하여** 워크플로우 모델을 추가합니다.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 워크플로우 모델을 생성하고 나면 모델(VideoRendition ****)을 선택하고 작업 **표시줄에서 편집을** 클릭합니다.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **명령줄 **구성 요소를 워크플로우로 드래그하여 놓습니다.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 명령줄 **구성 요소를** 선택하고 속성 대화 상자를 엽니다.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. [ **인수** ] 탭을 선택하여 [명령줄 - 단계 속성] **대화 상자에 필드를** 입력합니다.

   MIME 유형( **비디오/mp4** )에 형식을 입력하고 명령을 (***/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=color=black" cq5dam.video.fullhd-hp.mp4* **) 명령을 사용하여 작업 흐름을 시작할 ***수******* 있습니다.

   아래 메모에서 MIME 유형 및 **명령에** 대한 **자세한** 내용을 참조하십시오.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 워크플로우(VideoRenditions **)를**&#x200B;선택하고 작업 **표시줄에서 워크플로우** 시작을 클릭하여 워크플로우 **실행** 대화 상자를엽니다.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 페이로드에서 자산의 경로( **/content/dam/husefineda-crossrolling** 01_512kb 2.mp ***)를 선택하고 **Title **(as*** RunVideo)를 ***입력하고 실행을*******&#x200B;클릭합니다.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens 프로젝트에서 워크플로우 사용 {#using-the-workflow-in-an-aem-screens-project}

아래 절차에 따라 AEM Screens 프로젝트에서 워크플로우를 사용하십시오.

1. AEM Screens 프로젝트(TestVideoRendition **—&gt; 채널** —&gt; **VideoRendition** )**로 이동합니다**.

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. 처음에 자산에 업로드한 비디오를 드래그하여 **놓습니다**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 비디오를 업로드한 후 미리 보기를 클릭하여 **** 출력을 확인합니다.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 워크플로우에 대한 출력 유효성 확인 {#validating-the-output-for-the-workflow}

다음 방법으로 출력물의 유효성을 확인할 수 있습니다.

* 채널의 비디오 미리 보기 확인
* 아래 그림과 ***같이 CRXDE Lite의 /content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4로*** 이동합니다.

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

