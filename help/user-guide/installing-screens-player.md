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
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 1%

---

# AEM Screens Player 설치 {#installing-player}

이 페이지에서는 AEM Screens 플레이어를 설치하는 방법을 설명합니다.

## 사용 가능한 화면 플레이어 {#available-players}

AEM Screens 플레이어는 Android, Chrome OS 및 Windows에서 사용할 수 있습니다.

다운로드하려면 **AEM Screens 플레이어**, 다음 방문: [AEM 6.5 플레이어 다운로드](https://download.macromedia.com/screens/) 페이지를 가리키도록 업데이트하는 중입니다.

>[!NOTE]
>
>최신 플레이어를 다운로드하면(*.exe*)를 클릭하여 플레이어의 단계에 따라 임시 설치를 완료합니다.
>
>1. 왼쪽 상단 모서리에서 길게 눌러 관리 패널을 엽니다.
>1. 다음으로 이동 **구성** 왼쪽 작업 메뉴에서 AEM 인스턴스의 위치 주소를 입력합니다 **서버** 및 클릭 **저장**.
>1. 을(를) 클릭합니다 **등록** 왼쪽 작업 메뉴 및 아래 단계를 연결하여 디바이스 등록 프로세스를 완료합니다.

## 기본 재생 모니터링 {#playback-monitoring}

플레이어는 각 재생 지표에서 다양한 재생 지표를 보고합니다 `ping` 기본값은 30초입니다. 이러한 지표를 기반으로 중단 경험, 빈 화면 및 예약 문제와 같은 다양한 에지 사례를 감지할 수 있습니다. 이를 통해 디바이스의 문제를 파악하고 해결할 수 있으므로 귀하와 함께 조사 및 시정 조치를 신속하게 취할 수 있습니다.

AEM Screens 플레이어에서 기본 재생 모니터링을 사용하면 다음을 수행할 수 있습니다.

* 플레이어가 컨텐츠를 제대로 재생하고 있는지 원격으로 모니터링합니다.

* 현장에서의 빈 화면 또는 깨진 경험에 대한 반응성을 개선합니다.

* 최종 사용자에게 손상된 경험이 표시될 위험을 줄입니다.

### 속성 이해 {#understand-properties}

각 속성에는 다음 속성이 포함됩니다 `ping`:

| 속성 | 설명 |
|---|---|
| id {string} | 플레이어 식별자 |
| activeChannel {string} | 현재 재생 중인 채널 경로 또는 일정이 없는 경우 null |
| 활성 요소 {string} | 재생 중인 모든 시퀀스 채널에 현재 표시되는 쉼표로 구분된 문자열(다중 영역 레이아웃의 경우 다중) |
| isDefaultContent {boolean} | 재생 채널이 기본 또는 대체 채널로 간주되는 경우(즉, 우선 순위 1이 있고 일정이 없는 경우) true |
| hasContentChanged {boolean} | 지난 5분 동안 콘텐츠가 변경되면 true이고, 그렇지 않으면 false입니다. |
| lastContentChange {string} | 마지막 콘텐츠 변경 타임스탬프 |

>[!NOTE]
>선택적으로, 플레이어 환경 설정(재생 모니터링 활성화)에서 보다 고급 속성을 활성화할 수 있습니다.
>|속성|설명|
>|—|—|
>|isContentRendering {boolean}|true - GPU가 실제 콘텐츠를 재생하고 있는지 확인할 수 있는 경우(픽셀 분석 기반)|

### 제한 사항 {#limitations}

기본 재생 모니터링에 대한 몇 가지 제한 사항이 아래에 나와 있습니다.

* 플레이어는 자체 재생 상태를 서버에 보고하므로 활성 연결이 필요합니다.

* 다음 `isContentRendering` gpu를 확인하는 속성은 현재 리소스 사용량이 너무 많아 기본적으로 사용할 수 없으며 플레이어 환경 설정에서 명시적인 옵트인이 필요합니다. 프로덕션 환경에서는 비디오와 함께 사용하지 않는 것이 좋습니다.

* 이 기능은 시퀀스 채널에만 지원되며 대화형 채널(SPA) 사용 사례는 아직 다루지 않습니다.

* 지표가 아직 고객에게 완전히 노출되지 않았으며 가까운 시일 내에 대시보드와 유사한 보고 및 경고 메커니즘을 활성화하기 위해 노력하고 있습니다.

### 추가 리소스 {#additional-resources}

자세한 내용은 다음 항목을 참조하십시오.

* Android 플레이어를 다운로드하려면 다음을 방문하십시오. **Google Play**. Android Watchdog 구현에 대한 자세한 내용은 [Android 플레이어 구현](implementing-android-player.md).

* Chrome OS 플레이어를 구현하려면 다음을 참조하십시오. [Chrome 관리 콘솔](implementing-chrome-os-player.md) 추가 정보.

* AEM Screens Windows 플레이어를 구성하려면 다음을 참조하십시오. [Windows Player 구현](implementing-windows-player.md).
