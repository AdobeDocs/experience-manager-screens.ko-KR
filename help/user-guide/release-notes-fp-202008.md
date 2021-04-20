---
title: Feature Pack 202008용 릴리스 노트
description: '"2020년 9월 30일 릴리스된 AEM Screens Feature Pack 2008에 대한 정보를 보려면 이 페이지를 따르십시오."'
feature: Feature Pack
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 5%

---


# 기능 팩 202008에 대한 릴리스 노트 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>AEM(Adobe Experience Manager)의 최신 버전으로 업그레이드하는 것이 좋습니다. 스크린은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 5를 출시했습니다.

Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens 6.5.5 릴리스의 최신 기능 팩을 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;를 검색하여 최신 기능 팩을 가져옵니다.

## 릴리스 날짜 {#release-date}

AEM Screens 기능 팩 202008의 릴리스 날짜는 2020년 9월 3일입니다.

### 새로운 기능 {#what-is-new}

* **예약 대시보드에서 타임라인 보기**

   타임라인 보기를 사용하면 사용자가 디스플레이 대시보드에서 채널에 지정된 일정을 볼 수 있습니다.

   자세한 내용은 [타임라인 보기](/help/user-guide/channel-assignment-latest-fp.md#timeline-view)를 참조하십시오.

* **재현 예약**

   되풀이 일정을 사용하면 채널에 대한 반복 일정을 설정할 수 있습니다. 채널에 대해 여러 개의 되풀이 일정을 설정합니다.

   자세한 내용은 [되풀이 일정](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)을 참조하십시오.

* **AEM Screens의 음성 인식 기능**

   음성 인식 기능을 사용하면 음성 인터랙션을 기반으로 AEM Screens 채널의 컨텐츠를 변경할 수 있습니다.

   콘텐츠 작성자는 음성을 사용하도록 디스플레이를 구성할 수 있습니다. 이 기능의 목적은 고객이 자신의 디스플레이와 상호 작용하는 방법으로 음성을 활용할 수 있도록 하는 것입니다.

   자세한 내용은 [음성 인식](voice-recognition.md)을 참조하십시오.

### 알려진 문제 및 수정 사항 {#known-issues}

AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Windows 또는 Android 플레이어용 환경을 설정해야 합니다.

로그인 토큰 쿠키에 대한 **SameSite 특성을** Lax **에서** Adobe Experience Manager 웹 콘솔에서 **None**으로 설정합니다.
모든 AEM 작성자 및 게시 인스턴스에 대한 구성**.**

* 자세한 내용은 [Windows 10 Player 구현](implementing-windows-player.md#fp-environment-setup)을 참조하십시오.

* 자세한 내용은 [Android 플레이어 구현](implementing-android-player.md#fp-environment-setup)을 참조하십시오.

### 릴리스된 AEM Screens 플레이어 {#released-aem-screens-players}

다음 AEM Screens Player는 AEM 6.5 기능 팩 5를 위해 출시되었습니다.

* Chrome OS
* Windows
* Android

#### AEM Screens Player 다운로드 {#aem-screens-player-downloads}

최신 AEM Screens 플레이어를 다운로드하여 버그 수정에 대한 자세한 내용은 **[AEM Screens Player 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
