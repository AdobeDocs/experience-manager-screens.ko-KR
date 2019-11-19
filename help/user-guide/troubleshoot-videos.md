---
title: 비디오 재생 구성 및 문제 해결
seo-title: 비디오 문제 해결
description: null
seo-description: 비디오 문제 해결 방법을 알려면 이 페이지를 따르십시오. 비디오를 DAM에 업로드하고 채널을 추가하면 비디오가 Screens 플레이어에서 재생되지 않을 수 있는 문제가 발생할 수 있으며 이 섹션에서는 채널에서 재생되는 비디오를 디버깅 및 해결하는 방법에 대해 설명합니다.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 비디오 재생 구성 및 문제 해결 {#video-playback-configuration-and-troubleshooting}

DAM에 비디오를 업로드하고 채널을 추가하면 비디오가 Screens 플레이어에서 재생되지 않을 수 있는 문제가 발생할 수 있습니다.

다음 섹션에서는 채널에서 재생되는 비디오를 디버깅 및 해결하는 방법에 대해 설명합니다.

## DAM 변환 {#dam-renditions}

채널에 비디오를 업로드한 후에는 AEM에서 이에 대한 일부 변환을 만들기 시작해야 합니다. 자산에서 비디오를 볼 수 있습니다.

비디오를 보려면:

1. 예를 들어 비디오로 이동합니다 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. 비디오를 클릭하고 왼쪽 상단 메뉴를 확장한 다음 표현물을 **클릭합니다**.

다른 변환(MP4 또는 M4V)이 있어야 합니다.

변환이 없는 경우 AEM이 실행 중인 OS에 ffmpeg가 설치되어 있는지 확인하십시오.

>[!CAUTION]
>
>변환이 없는 경우 AEM이 실행 중인 OS에 ffmpeg가 설치되어 있는지 확인하십시오.
>
>ffmpeg를 설치하려면 [여기를](https://evermeet.cx/ffmpeg/) 클릭하십시오.

## 비디오 자산 {#video-assets}

비디오 아래에 소스 속성이 표시되지 않으면 비디오가 트랜스코딩되지 않았을 수 있습니다. 비디오가 제대로 트랜스코딩되면 아래 그림과 같이 대시보드에 표시됩니다.

ffmpeg가 설치되어 있고 비디오 프로필을 확인합니다.

![chlimage_1-2](assets/chlimage_1-2.png)

### 비디오 프로필 확인 {#checking-video-profile}

1. 비디오 프로필( **즉**) `http://localhost:4502/etc/dam/video.html` 으로 이동하고 테스트 비디오 **업로드를 클릭합니다**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 테스트 비디오를 업로드하고 **확인 **을 클릭하여 트랜스코딩을 시작합니다.

   트랜스코딩에 실패하면 ffmpeg 출력을 확장하여 ffmpeg의 콘솔 출력에 있는 오류를 파악합니다.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   또한 비디오 트랜스코딩이 성공적으로 코드 변환된 파일을 다운로드할 수 있습니다.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >모든 채널에 비디오를 추가하기 전에 비디오를 트랜스코딩할 충분한 시간을 제공해야 합니다(처리하는 대신 새 태그를 표시해야 함).

### 비디오 구성 요소로 프로필 확인 {#checking-profile-with-a-video-component}

비디오 구성 요소가 제대로 구성되지 않은 경우 페이지 디자인에서 프로필 목록을 확인합니다.

1. 채널을 탐색하고 디자인 **모드를 선택합니다** .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 비디오를 선택하고 편집 **대화 상자를 엽니다** . Open the **Profiles** tab.

   다른 프로파일을 선택합니다(최소한 "High Quality H.264" 프로파일이 있어야 함).

   ![chlimage_1-7](assets/chlimage_1-7.png)

### 웹 플레이어에서 비디오 확인 {#checking-the-video-in-the-web-player}

웹 플레이어를 **사용하여** 브라우저(Chrome 및 Safari)에서 `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 재생의 유효성을 확인합니다. Chrome은 Android 장치에서 사용되며 Safari는 OSX 및 iOS 브라우저입니다.

비디오가 Safari에서 실행되지 않으면 OSX 및 iOS 플레이어에서 실행되지 않습니다. 이는 인코딩 문제이며 비디오를 다시 인코딩해야 합니다.

DAM 워크플로우를 사용하여 FullHD 변환을 만들려면 다음 단계를 따르십시오.

1. 워크플로우 *모델 관리자로*&#x200B;이동합니다. 즉, `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. 스크린 자산 **업데이트 모델을** 선택합니다.
1. 작업 **표시줄에서** 워크플로우 시작을 클릭하여 워크플로우 **실행 대화 상자를 엽니다** .

1. 페이로드에서 비디오 자산을 **선택합니다**.
1. 실행을 **클릭합니다**.

>[!NOTE]
>
>변환을 만드는 데 약간의 시간이 소요될 수 있지만, 몇 초/분(비디오 크기에 따라 다름) 후에 Safari에서 웹 플레이어를 다시 로드하십시오.

#### 자동 재생 정책 플래그 문제 해결 {#troubleshooting-autoplay-policy-flag}

AEM Screens 플레이어에서 비디오를 선택하지만 표시되지 않는 경우 자동 재생 정책 플래그 문제를 해결해야 합니다.

Google의 자동 재생 정책 플래그 문제를 해결하려면 아래 절차를 따르십시오.

1. chrome://flags/#autoplay-policy으로 ***이동***
1. 자동 **재생 정책을** 기본값에서 **사용자 제스처가** **필요하지 않은 상태로 변경**

1. 웹 브라우저를 다시 실행하고 플레이어를 업데이트합니다.

>[!NOTE]
>
>Chrome의 새로운 자동 재생 정책을 통해 향상된 사용자 경험을 위한 모범 사례에 대한 자세한 내용은 자동 재생 정책 *변경 사항*`https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`(즉,

### 여러 플레이어에서 비디오 동기화 {#syncing-video-across-multiple-players}

여러 장치에서 비디오를 동기식으로 재생하려면 비디오가 속한 시퀀스에 대한 절대 전략을 사용해야 합니다.

#### 요구 사항 {#requirements}

* 동일한 2개 이상의 플레이어
* 이상적인 하드웨어
* 동일한 네트워크 토폴로지(플레이어는 내부 시스템 클럭을 정렬하는 NTP 서버에 연결되어 있음)

#### 절대 전략 설정 {#setting-up-the-absolute-strategy}

절대 전략:

* 앵커 시간 계산(현재 날짜의 자정)
* 시퀀스의 지속 시간 계산(모든 항목의 지속 시간 합)
* 언제든지 _remaining_time = (current_time - anchor_time) % sequence_duration을 해결하여 현재 재생해야 하는 항목과 다음 항목을 계산합니다.

아래 절차에 따라 절대 전략을 설정합니다.

1. 채널 작성자로 이동하여 아래 그림과 같이 시퀀스 구성 요소를 선택합니다.
1. 구성 대화 상자를 엽니다.
1. 전략을 **편집하고** 절대값을 추가합니다.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>선수들의 OS는 반드시 같은 시계를 가지고 있어야 한다.

**OS X에서 시계** 정렬 아래 단계에 따라 OSX에서 시계를 정렬합니다.

1. 각 **OSX** 상자에서 날짜 및 시간 환경 설정 열기
1. 확인** 날짜 및 시간 자동 설정**
1. 드롭다운에서 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com 값을 붙여넣거나 sudo ntpdate -u -v *v.pool.ntp.org를 실행하기만 하면 됩니다.*
1. 2개 이상의 플레이어 시작

플레이어가 새 정렬 시퀀스를 시작하는 데 시간이 걸릴 수 있습니다.

