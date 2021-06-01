---
title: 비디오 재생 구성 및 문제 해결
seo-title: 문제 해결 비디오
description: 채널에서 비디오 재생을 디버깅하고 문제를 해결하는 방법을 배우려면 이 페이지를 따르십시오.
seo-description: 비디오 문제 해결 방법을 배우려면 이 페이지를 따르십시오. 비디오를 DAM에 업로드하고 채널을 추가할 때 비디오가 Screens 플레이어에서 재생되지 않을 수 있는 문제가 발생할 수 있으며 이 섹션에서는 채널에서 비디오를 재생하는 방법을 디버깅하고 해결하는 방법을 설명합니다.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: 채널, 대화형
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# 비디오 재생 구성 및 문제 해결 {#video-playback-configuration-and-troubleshooting}

비디오를 DAM에 업로드하고 채널을 추가하면 Screens 플레이어에서 비디오가 재생되지 않을 수 있는 문제가 발생할 수 있습니다.

다음 섹션에서는 채널에서 비디오 재생을 디버깅하고 문제를 해결하는 방법을 설명합니다.

## DAM 표현물 {#dam-renditions}

비디오를 채널에 업로드하면 AEM에서 해당 비디오에 대한 일부 렌디션 만들기를 시작해야 합니다. Assets에서 비디오를 볼 수 있습니다.

비디오를 보려면:

1. 비디오로 이동합니다(예: `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`).
1. 비디오를 클릭하고 왼쪽 위 메뉴를 확장한 다음 **표현물**&#x200B;을 클릭합니다.

다양한 표현물(MP4 또는 M4V)이 있어야 합니다.

변환이 없는 경우 AEM이 실행 중인 OS에 ffmpeg가 설치되어 있는지 확인합니다.

>[!CAUTION]
>
>변환이 없는 경우 AEM이 실행 중인 OS에 ffmpeg가 설치되어 있는지 확인합니다.
>
>ffmpeg를 설치하려면 [여기](https://www.ffmpeg.org/download.html)를 클릭하십시오.

## 비디오 자산 {#video-assets}

비디오 아래에 소스 속성이 표시되지 않으면 비디오가 트랜스 코딩되지 않았을 수 있습니다. 비디오가 올바르게 트랜스 코딩되면 아래 그림과 같이 대시보드에 표시됩니다.

ffmpeg가 설치되어 있고 비디오 프로필을 확인합니다.

![chlimage_1-2](assets/chlimage_1-2.png)

### 비디오 프로필 확인 중 {#checking-video-profile}

1. **비디오 프로필**(즉, `http://localhost:4502/etc/dam/video.html`)로 이동하고 **테스트 비디오 업로드**&#x200B;를 클릭합니다.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 테스트 비디오를 업로드하고 **확인** 을 클릭하여 코드 변환을 시작합니다.

   코드가 실패하면 ffmpeg 출력을 확장하여 ffmpeg의 콘솔 출력에 있는 모든 오류를 파악합니다.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   또한, 비디오 코드가 성공적으로 코드 변환된 파일을 다운로드할 수 있습니다.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >채널에 추가하기 전에 비디오가 코드를 변환할 수 있는 충분한 시간(처리 대신 새 태그를 보여 주어야 함)을 주어야 합니다.

### 비디오 구성 요소 {#checking-profile-with-a-video-component}로 프로필 확인

비디오 구성 요소가 제대로 구성되지 않은 경우 페이지 디자인에서 프로필 목록을 확인합니다.

1. 채널로 이동하고 **디자인** 모드를 선택합니다.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 비디오를 선택하고 **편집** 대화 상자를 엽니다. **프로필** 탭을 엽니다.

   >[!NOTE]
   >다른 프로필을 선택합니다(적어도 &quot;High Quality H.264&quot; 프로필이 있어야 함).

### 웹 플레이어에서 비디오 확인 {#checking-the-video-in-the-web-player}

브라우저(Chrome 및 Safari)에서 재생의 유효성을 검사하려면 **웹 플레이어** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`를 사용하십시오. Safari는 OSX 및 iOS 브라우저인 반면 Chrome은 Android 장치에서 사용됩니다.

비디오가 Safari에서 실행되지 않으면 OSX 및 iOS 플레이어에서 실행되지 않습니다. 이는 인코딩 문제일 수 있으며 비디오를 다시 인코딩해야 합니다.

DAM 워크플로우를 사용하여 FullHD 표현물을 생성하려면 다음 단계를 수행합니다.

1. *워크플로우 모델 관리자*&#x200B;로 이동합니다(`http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`).
1. **스크린 자산 업데이트** 모델을 선택합니다.
1. 작업 표시줄에서 **워크플로우 시작**&#x200B;을 클릭하여 **워크플로우 실행** 대화 상자를 엽니다.

1. **페이로드**&#x200B;에서 비디오 자산을 선택합니다.
1. **실행**&#x200B;을 클릭합니다.

>[!NOTE]
>
>잠시 렌디션을 만들 수 있지만, 몇 초/분(비디오 크기에 따라 다름) 후에 Safari에서 웹 플레이어를 다시 로드합니다.

#### 자동 실행 정책 플래그 문제 해결 {#troubleshooting-autoplay-policy-flag}

AEM Screens 플레이어가 비디오를 선택하지만 표시되지 않는 경우 자동 재생 정책 플래그 문제를 해결해야 합니다.

google의 자동 재생 정책 플래그 문제를 해결하려면 아래 절차를 따르십시오.

1. ***chrome://flags/#autoplay-policy***&#x200B;로 이동합니다.
1. **자동 재생 정책**&#x200B;을 **기본**&#x200B;에서 **로 변경할 필요가 없습니다**

1. 웹 브라우저를 다시 시작하고 플레이어를 업데이트합니다

>[!NOTE]
>
>Chrome에서 새로운 자동 재생 정책을 사용하는 사용자 환경 개선 사항에 대한 우수 사례에 대해 자세히 알아보려면 *자동 재생 정책 변경 사항*(즉, `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`)에 대한 설명서를 참조하십시오.

### 여러 플레이어에서 비디오 동기화 {#syncing-video-across-multiple-players}

여러 장치에서 비디오를 동기식으로 재생하려면 비디오가 속해 있는 시퀀스에 대한 절대 전략을 사용해야 합니다.

#### 요구 사항 {#requirements}

* 동일한 2개 이상의 플레이어
* 매우 유사한 하드웨어
* 동일한 네트워크 토폴로지(플레이어는 내부 시스템 클럭을 정렬하는 NTP 서버에 연결됨)

#### 절대 전략 설정 {#setting-up-the-absolute-strategy}

절대적 전략:

* 앵커 시간(현재 날짜의 자정)을 계산합니다.
* 시퀀스의 지속 시간을 계산합니다(모든 항목의 지속 시간 합계).
* 어느 시점에서 sequence_remaining_time = (current_time - anchor_time) % sequence_duration을 해결하여 현재 재생될 항목과 다음 항목을 계산합니다.

아래 단계에 따라 절대 전략을 설정하십시오.

1. 채널 작성자로 이동하고 아래 그림과 같이 시퀀스 구성 요소를 선택합니다.
1. 구성 대화 상자를 엽니다.
1. **전략**&#x200B;을 편집하고 절대값을 추가합니다.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >선수들의 OS는 반드시 같은 시계를 가지고 있어야 한다.

**OS XF에서** 클럭을 정렬하면 아래 단계를 수행하여 OSX에서 클럭을 맞춥니다.

1. 각 OSX 상자에서 **날짜 및 시간** 환경 설정을 엽니다.
1. **날짜 및 시간을 자동으로 설정**
1. 드롭다운에서 값 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com을 붙여넣거나 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 2개 이상의 플레이어 시작

플레이어가 정렬된 새 시퀀스를 시작하기 전에 시간이 걸릴 수 있습니다.

