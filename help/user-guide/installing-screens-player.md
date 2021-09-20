---
title: Screens 플레이어 설치
seo-title: Installing Screens Player
description: 사용 가능한 AEM Screens Player 설치에 대해 알려면 이 페이지를 따르십시오.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# AEM Screens Player 설치 {#installing-player}

이 페이지에서는 AEM Screens 플레이어를 설치하는 방법을 설명합니다.

## 사용 가능한 스크린 플레이어 {#available-players}

AEM Screens 플레이어는 Android, Chrome OS 및 Windows에서 사용할 수 있습니다.

**AEM Screens Player**&#x200B;를 다운로드하려면 [AEM 6.5 Player 다운로드](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

>[!NOTE]
>
>최신 플레이어(*.exe*)를 다운로드하면 플레이어의 단계에 따라 임시 설치를 완료합니다.
>
>1. 왼쪽 상단 모서리에서 을(를) 길게 눌러 관리 패널을 엽니다.
>1. 왼쪽 작업 메뉴에서 **구성**&#x200B;으로 이동하고 **서버**&#x200B;에 AEM 인스턴스의 위치 주소를 입력하고 **저장**&#x200B;을 클릭합니다.
>1. 왼쪽 작업 메뉴에서 **등록** 링크를 클릭하고 아래 단계를 클릭하여 장치 등록 프로세스를 완료합니다.


## 기본 재생 모니터링 {#playback-monitoring}

플레이어는 기본값인 각 `ping`이 30초로 설정된 다양한 재생 지표를 보고합니다. 이러한 지표를 기반으로 중단 경험, 빈 화면 및 예약 문제와 같은 다양한 에지 사례를 감지할 수 있습니다. 따라서 장치의 문제를 이해하고 문제를 해결할 수 있으므로 신속한 조사 및 해결 조치를 취할 수 있습니다.

AEM Screens 플레이어의 기본 재생 모니터링을 통해 다음을 수행할 수 있습니다.

* 플레이어가 컨텐츠를 제대로 재생하는 경우 원격으로 모니터링합니다.

* 필드의 빈 화면 또는 끊어진 경험에 대한 반응성을 개선합니다.

* 최종 사용자에게 손상된 경험을 표시할 위험을 줄입니다.

### 속성 이해 {#understand-properties}

다음 속성은 각 `ping`에 포함됩니다.

| 속성 | 설명 |
|---|---|
| id {string} | 플레이어 식별자 |
| activeChannel {string} | 현재 재생 중인 채널 경로이거나 예약된 항목이 없으면 null입니다. |
| activeElements {string} | 쉼표로 구분된 문자열, 현재 표시된 모든 재생 시퀀스 채널에 요소(다중 영역 레이아웃의 경우 다중) |
| isDefaultContent {boolean} | 재생 채널이 기본 또는 폴백 채널로 간주되는 경우 true(즉, 우선 순위 1이 있고 예약이 없는 경우) |
| hasContentChanged {boolean} | 지난 5분 동안 내용이 변경된 경우 true이고, 그렇지 않으면 false입니다 |
| lastContentChange {string} | 마지막 콘텐츠 변경 타임스탬프 |

>[!NOTE]
>선택적으로 플레이어 환경 설정(재생 모니터링 활성화)에서 더 많은 고급 속성을 활성화할 수 있으며, 이러한 속성은 다음과 같습니다.
>|속성|설명|
>|—|—|
>|isContentRendering {boolean}|GPU에서 실제 컨텐츠 재생(픽셀 분석 기반)을 확인할 수 있는 경우 true|

### 제한 사항 {#limitations}

다음은 기본 재생 모니터링에 대한 몇 가지 제한 사항입니다.

* 플레이어는 자체 재생 상태를 서버에 보고하므로 활성 연결이 필요합니다.

* GPU를 확인하는 `isContentRendering` 속성은 현재 리소스를 너무 많이 사용하므로 기본적으로 활성화할 수 없으며 플레이어 환경 설정에서 명시적 옵트인이 필요합니다. 프로덕션 환경에서 비디오와 함께 사용하지 않는 것이 좋습니다.

* 이 기능은 시퀀스 채널에서만 지원되며 대화형 채널(SPA) 사용 사례는 아직 다루지 않습니다.

* 이 지표는 아직 고객에게 완전히 노출되지 않았으며, 가까운 시일 내에 대시보드와 유사한 보고 및 경고 메커니즘을 사용하기 위해 노력하고 있습니다.

### 추가 리소스 {#additional-resources}

자세한 내용은 다음 주제를 참조하십시오.

* Android 플레이어를 다운로드하려면 **Google Play**&#x200B;를 방문하십시오. Android Watchdog 구현에 대한 자세한 내용은 [Android 플레이어 구현](implementing-android-player.md)을 참조하십시오.

* Chrome OS Player를 구현하려면 [Chrome Management Console](implementing-chrome-os-player.md) 을 참조하십시오.

* AEM Screens Windows 플레이어를 구성하려면 [Windows Player 구현](implementing-windows-player.md)을 참조하십시오.
