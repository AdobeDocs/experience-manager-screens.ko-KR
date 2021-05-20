---
title: 비디오 표현물
seo-title: 비디오 표현물
description: 스크린 프로젝트에 대한 Full HD 표현물 생성에 대해 알려면 이 페이지를 따르십시오.
seo-description: 스크린 프로젝트에 대한 Full HD 표현물 생성에 대해 알려면 이 페이지를 따르십시오.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: 스크린 작성
role: Administrator, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 66%

---

# 비디오 표현물 {#video-renditions}

수동 및 자동 Full HD 표현물을 생성할 수 있습니다. 다음 섹션에서는 자산에 표현물을 추가하는 워크플로우에 대해 설명합니다.

## Full HD 표현물 자동 생성  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>AEM Screens 비디오 표현물이 장치에서 최적으로 재생되지 않는 경우 하드웨어 공급업체에 비디오 사양에 대해 문의하십시오. 이는 장치에서 최상의 성능을 얻는 데 도움이 되며, 따라서 표현물을 생성하기 위한 FFMPEG에 적합한 매개 변수를 제공하는 고유의 사용자 지정 비디오 프로필을 만드는 데에도 도움이 됩니다. 그런 다음에는 아래 절차를 사용하여 프로필 목록에 사용자 지정 비디오 프로필을 추가하십시오.
>
>추가로, 채널에서 비디오를 재생할 때 발생하는 버그와 문제를 해결하려면 [문제 해결 비디오](troubleshoot-videos.md)를 참조하십시오.

Full HD 표현물을 자동으로 생성하려면 아래 절차를 따르십시오.

1. Adobe Experience Manager 링크(맨위 왼쪽)를 선택하고 망치 아이콘을 클릭하여 **워크플로우**&#x200B;를 선택합니다.

   **모델**&#x200B;을 클릭하여 워크플로우 모델 관리를 입력합니다.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. **DAM 자산 업데이트** 모델을 선택하고 작업 표시줄에서 편집 을 클릭하여 **DAM 자산 업데이트** 창을 엽니다.

   ![step5_-_edit_damupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. **FFmpeg 코드 변환** 단계를 두 번 클릭합니다.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. **프로세스** 탭을 선택하여 프로세스 인수를 편집합니다. **인수**&#x200B;에 있는 목록에 대한 전체 HD 프로필을 다음과 같이 입력합니다.***,profile:fullhd-bp,profile:fullhd-hp*** 및 **확인**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. **DAM 자산 업데이트** 화면의 맨위 왼쪽에 있는 **저장**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. **자산**&#x200B;으로 이동하여 새 비디오를 업로드합니다. 비디오를 클릭하고 표현물 사이드 레일을 여십시오. 그러면 두 개의 Full HD 비디오가 표시됩니다.

   ![step10_-_open_videoasset](assets/step10_-_open_thevideoasset.png)

1. 사이드 레일에서 **표현물**&#x200B;을 엽니다.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 새로운 Full HD 표현물 두 개를 발견할 수 있습니다.

   ![step12_-_2_new_renditionsAreaddedtothe video](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Full HD 표현물 수동 생성 {#manually-generating-full-hd-renditions}

Full HD 표현물을 수동으로 생성하려면 아래 절차를 따르십시오.

1. Adobe Experience Manager 링크(맨위 왼쪽)를 선택하고 망치 아이콘을 클릭하여 **워크플로우**&#x200B;를 선택합니다.

   **모델**&#x200B;을 클릭하여 워크플로우 모델 관리를 입력합니다.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. **스크린 자산 업데이트** 모델을 선택하고 **워크플로우 시작**&#x200B;을 클릭하여 **워크플로우 실행** 대화 상자를 엽니다.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. **페이로드**&#x200B;에서 원하는 비디오를 선택하고 **실행**&#x200B;을 클릭합니다.

   ![step6_-_select_thedesiedvideo](assets/step6_-_select_thedesiredvideo.png)

1. **자산**&#x200B;으로 이동하여 자산으로 드릴다운하고 해당 자산을 클릭합니다.

   ![step7_-_open_videoasset](assets/step7_-_open_thevideoasset.png)

1. **표현물** 사이드 레일을 여십시오. 그러면 새 Full HD 표현물을 확인할 수 있습니다.

   ![step8_-_open_therenditionsiderail](assets/step8_-_open_therenditionssiderail.png)
