---
title: 비디오 재생 구성 및 문제 해결
description: AEM Screens용 채널에서 비디오 재생을 디버깅하고 문제를 해결하는 방법에 대해 알아봅니다.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# 비디오 재생 구성 및 문제 해결 {#video-playback-configuration-and-troubleshooting}

DAM에 비디오를 업로드하고 채널에 추가하면 AEM Screens 플레이어에서 비디오가 재생되지 않는 문제가 발생할 수 있습니다.

다음 섹션에서는 채널에서 비디오가 재생되는 문제를 해결하고 디버그하는 방법에 대해 설명합니다.

## DAM 표현물 {#dam-renditions}

비디오를 채널에 업로드하면 AEM에서 해당 비디오에 대한 일부 렌디션 만들기를 시작해야 합니다. Assets에서 비디오를 볼 수 있습니다.

비디오를 보려면 다음 작업을 수행하십시오.

1. 비디오로 이동합니다(예: `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`).
1. 비디오를 클릭하고 왼쪽 상단 메뉴를 확장한 다음 **렌디션**&#x200B;을 클릭합니다.

다양한 렌디션(MP4 또는 M4V)이 있어야 합니다.

렌디션이 없으면 AEM이 실행 중인 OS에 FFMPEG가 설치되어 있는지 확인하십시오.

>[!CAUTION]
>
>렌디션이 없으면 AEM이 실행 중인 OS에 FFMPEG가 설치되어 있는지 확인하십시오.
>
>FFMPEG를 설치하려면 [여기](https://www.ffmpeg.org/download.html)를 클릭하십시오.

## 비디오 Assets {#video-assets}

비디오에 소스 속성이 표시되지 않으면 비디오가 트랜스 코딩되지 않았을 수 있습니다. 비디오가 제대로 코드 변환되면 다음과 같이 대시보드에 표시됩니다.

FFMPEG가 설치되어 있고 비디오 프로필이 있는지 확인합니다.

![chlimage_1-2](assets/chlimage_1-2.png)

### 비디오 프로필 확인 {#checking-video-profile}

1. **비디오 프로필**, 즉 `http://localhost:4502/etc/dam/video.html`(으)로 이동한 다음 **테스트 비디오 업로드**&#x200B;를 클릭합니다.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 코드 변환을 시작할 수 있도록 테스트 비디오를 업로드하고 **확인**&#x200B;을 클릭합니다.

   트랜스코딩된 비디오가 실패할 경우 FFMPEG 출력을 확장하여 FFMPEG의 콘솔 출력에서 발생한 오류를 파악합니다.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   또한, 비디오 트랜스코딩이 성공적으로 수행되면 트랜스코딩된 파일을 다운로드할 수 있습니다.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >채널에 추가하기 전에 비디오가 코드 변환(처리 대신 새 태그가 표시되어야 함)할 충분한 시간을 제공해야 합니다.

### 비디오 구성 요소로 프로필 확인 {#checking-profile-with-a-video-component}

비디오 구성 요소가 제대로 구성되지 않은 경우 페이지 디자인에서 프로필 목록을 확인하십시오.

1. 채널로 이동하고 **디자인** 모드를 클릭합니다.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 비디오를 클릭하고 **편집** 대화 상자를 엽니다. **프로필** 탭을 엽니다.

   >[!NOTE]
   >다른 프로필을 클릭합니다(적어도 &quot;고품질 H.264&quot; 프로필이 있어야 함).

### 웹 플레이어에서 비디오 확인 {#checking-the-video-in-the-web-player}

**웹 플레이어** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`을(를) 사용하여 브라우저(Chrome 및 Safari)에서 재생의 유효성을 검사하십시오. Chrome은 Android™ 디바이스에서 사용되는 반면 Safari는 OS X 및 iOS 브라우저입니다.

비디오가 Safari에서 실행되지 않는 경우 OS X 및 iOS 플레이어에서도 실행되지 않습니다. 이 문제는 인코딩 문제일 수 있으며 비디오를 다시 인코딩해야 합니다.

DAM 워크플로우를 사용하여 FullHD 렌디션을 만들려면 다음 작업을 수행하십시오.

1. `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`인 *워크플로 모델 관리자*(으)로 이동합니다.
1. **Screens 자산 업데이트** 모델을 클릭합니다.
1. 작업 표시줄에서 **워크플로 시작**&#x200B;을 클릭합니다.
1. **워크플로 실행** 대화 상자에서 **페이로드**&#x200B;에서 비디오 자산을 클릭합니다.
1. **실행**&#x200B;을 클릭합니다.

>[!NOTE]
>
>렌디션을 만드는 데 시간이 좀 걸리지만 몇 초/분 후(비디오 크기에 따라 다름) Safari에서 웹 플레이어를 다시 로드합니다.

#### 자동 재생 정책 플래그 문제 해결 {#troubleshooting-autoplay-policy-flag}

AEM Screens 플레이어가 비디오를 선택하지만 표시되지 않는 경우 자동 재생 정책 플래그 문제를 해결합니다.

Google의 자동 재생 정책 플래그 문제를 해결하려면 아래 단계를 따르십시오.

1. ***chrome://flags/#autoplay-policy***(으)로 이동
1. **자동 재생 정책**&#x200B;을(를) **기본**&#x200B;에서 **사용자 동작 필요 없음**(으)로 변경

1. 웹 브라우저를 다시 시작하고 플레이어 업데이트

>[!NOTE]
>
>Chrome의 새로운 자동 재생 정책을 통해 유용한 사용자 경험을 위한 모범 사례에 대해 자세히 알아보십시오. `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`의 *자동 재생 정책 변경*&#x200B;을(를) 참조하십시오.

### 여러 플레이어에서 비디오 동기화 {#syncing-video-across-multiple-players}

여러 디바이스에서 동기적으로 비디오를 재생하려면 비디오가 포함된 시퀀스에 절대 전략을 사용해야 합니다.

#### 요구 사항 {#requirements}

* 일란성 2+ 플레이어
* 이상적으로 유사한 하드웨어
* 동일한 네트워크 토폴로지(플레이어는 내부 시스템 시계를 맞추는 NTP 서버에 연결됨)

#### 절대 전략 설정 {#setting-up-the-absolute-strategy}

절대 전략:

* 앵커 시간(현재 날짜의 자정)을 계산합니다.
* 시퀀스의 기간(모든 항목의 기간 합계)을 계산합니다.
* 언제든지 시퀀스 _remaining_time = (current_time - anchor_time) % sequence_duration 을 해결하여 현재 재생되어야 하는 항목과 다음 항목을 계산합니다.

절대 전략을 설정하려면 아래 단계를 따르십시오.

1. 아래 그림과 같이 채널 작성자로 이동하여 시퀀스 구성 요소를 클릭합니다.
1. 구성 대화 상자를 엽니다.
1. **전략**&#x200B;을(를) 편집하고 절대 값을 추가하십시오.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >플레이어의 OS는 시계가 같아야 합니다.

**OS X에서 시계 정렬** OS X에서 시계를 정렬하려면 아래 단계를 따르십시오.

1. 각 OS X 상자에서 **날짜 및 시간** 환경 설정 열기
1. **자동으로 날짜 및 시간 설정** 확인
1. 드롭다운에 값 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com을 붙여 넣거나 *`sudo ntpdate -u -v 0.pool.ntp.org`*&#x200B;을(를) 실행하십시오.
1. 2명 이상의 플레이어 시작

플레이어가 새로운 정렬된 시퀀스를 시작하기 전에 약간의 시간이 걸릴 수 있습니다.
