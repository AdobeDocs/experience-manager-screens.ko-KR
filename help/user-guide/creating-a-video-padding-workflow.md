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

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **전제 조건**
* **비디오 패딩 작업 과정 만들기**
   * **워크플로우 만들기**
   * **AEM Screens 프로젝트에서 워크플로우 사용**

* **워크플로우에 대한 출력 유효성 확인**

## 개요 {#overview}

다음 사용 사례에는 비디오 배치(예:1280 x 720) - 1920 x 1080이고 비디오를 0x0(왼쪽 위)에 배치하도록 하는 채널입니다. 비디오는 어떤 식으로든 스트레치하거나 수정할 수 없으며 비디오 구성 요소에 **표지**&#x200B;를 사용하지 마십시오.

비디오는 픽셀 1부터 픽셀 720까지 픽셀 1부터 픽셀 1280까지 픽셀 1부터 픽셀 1280까지 오브젝트로 표시되며 나머지 채널은 기본 색상이 됩니다.

## 전제 조건 {#prerequisites}

비디오 작업 과정을 만들기 전에 다음 사전 요구 사항을 완료하십시오.

1. AEM 인스턴스의 **자산** 폴더에 비디오 업로드
1. 아래 그림과 같이 AEM Screens 프로젝트(예: **TestVideoRendition**)와 (**VideoRendering**) 채널을 만듭니다.

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 비디오 패딩 작업 과정 만들기 {#creating-a-video-padding-workflow-1}

비디오 패딩 작업 과정을 만들려면 비디오에 대한 작업 과정을 만든 다음 AEM Screens 프로젝트 채널에서 동일하게 사용해야 합니다.

아래 절차에 따라 워크플로우를 만들고 사용하십시오.

1. 워크플로우 만들기
1. AEM Screens 프로젝트에서 워크플로우 사용

### 워크플로 {#creating-a-workflow} 만들기

아래 절차에 따라 비디오용 워크플로우를 만드십시오.

1. AEM 인스턴스로 이동하고 측면 레일에서 도구를 클릭합니다. **워크플로우** —> **모델**&#x200B;을 선택하여 새 모델을 만듭니다.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. **모델** —> **만들기** —> **모델 만들기**&#x200B;를 클릭합니다. **워크플로우 모델 추가**&#x200B;에 **제목**(예: **VideoRendition**) 및 **이름**&#x200B;을 입력합니다. 워크플로우 모델을 추가하려면 **완료**&#x200B;를 클릭합니다.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 워크플로우 모델을 만든 후 모델(**VideoRendition**)을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **명령줄** 구성 요소를 워크플로우로 드래그하여 놓습니다.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. **명령줄** 구성 요소를 선택하고 속성 대화 상자를 엽니다.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. **인수** 탭을 선택하여 **명령줄 - 단계 속성** 대화 상자에 필드를 입력합니다.

   **MIME 유형**(예: ***비디오/mp4***)에 형식을 입력하고 명령을 (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=color=black&quot; cq5dam.으로 입력합니다. video.fullhd-hp.mp4***)을 사용하여 **명령** 필드에서 워크플로우를 시작합니다.

   아래 메모에서 **MIME 유형** 및 **명령**&#x200B;에 대한 세부 정보를 참조하십시오.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 워크플로(**VideoRenditions**)를 선택하고 작업 표시줄에서 **워크플로우 시작**&#x200B;을 클릭하여 **워크플로우 실행** 대화 상자를 엽니다.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. **페이로드**(예: ***/content/dam/huseindeda-crossrolls01_512kb 2.mp4***)에서 자산의 경로를 선택하고 **제목**&#x200B;을 ***RunVideo***&#x200B;으로 입력하고 **을 클릭합니다.**&#x200B;을(를) 실행합니다.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens 프로젝트 {#using-the-workflow-in-an-aem-screens-project}에서 워크플로우 사용

AEM Screens 프로젝트에서 워크플로우를 사용하려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트(**TestVideoRendition** —> **채널** —>**VideoRendition**)로 이동합니다.

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 처음에 업로드한 비디오를 **자산**&#x200B;에 드래그하여 놓습니다.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 비디오를 업로드한 후에는 **미리 보기**&#x200B;를 클릭하여 출력을 봅니다.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 워크플로 {#validating-the-output-for-the-workflow}에 대한 출력 유효성 확인

다음과 같이 출력물의 유효성을 확인할 수 있습니다.

* 채널에서 비디오 미리 보기 확인
* 아래 그림과 같이 CRXDE Lite의 ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***&#x200B;로 이동합니다.

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

