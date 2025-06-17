---
title: Screens 플레이어 설치
description: AEM Screens 플레이어를 올바르게 설치하는 방법을 알아봅니다.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# AEM Screens Player 설치 {#installing-player}

이 페이지에서는 AEM Screens Player 설치 방법을 설명합니다.

## 사용 가능한 Screens 플레이어 {#available-players}

AEM Screens 플레이어는 Android™, Chrome OS 및 Windows에서 사용할 수 있습니다.

**AEM Screens 플레이어**&#x200B;를 다운로드하려면 [AEM 6.5 플레이어 다운로드](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

>[!NOTE]
>
>최신 플레이어(*.exe*)를 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.
>
>1. 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
>1. 왼쪽 작업 메뉴에서 **구성**(으)로 이동하고 **서버**&#x200B;에서 AEM 인스턴스의 위치 주소를 입력한 다음 **저장**&#x200B;을 클릭합니다.
>1. 왼쪽 작업 메뉴에서 **등록** 링크를 클릭하고 아래 단계를 클릭하여 장치 등록 프로세스를 완료합니다.

## 기본 재생 모니터링 {#playback-monitoring}

플레이어는 기본적으로 30초로 설정된 각 `ping`을(를) 사용하여 다양한 재생 지표를 보고합니다. 이러한 지표를 기반으로 중단 경험, 빈 화면 및 예약 문제와 같은 다양한 에지 사례를 감지할 수 있습니다. 이를 통해 디바이스의 문제를 이해하고 해결할 수 있으므로 조사 및 수정 조치를 신속하게 진행할 수 있습니다.

AEM Screens Player의 기본 재생 모니터링을 사용하면 다음을 수행할 수 있습니다.

* 플레이어가 컨텐츠를 제대로 재생하고 있는지 원격으로 모니터링합니다.

* 현장에서의 빈 화면 또는 깨진 경험에 대한 반응성을 개선합니다.

* 최종 사용자에게 손상된 경험이 표시될 위험을 줄입니다.

### 속성 이해 {#understand-properties}

다음 속성이 각 `ping`에 포함되어 있습니다.

| 속성 | 설명 |
|---|---|
| id {string} | 플레이어 식별자 |
| activeChannel {string} | 현재 재생 중인 채널 경로 또는 일정이 없는 경우 null |
| activeElements {string} | 쉼표로 구분된 문자열, 현재 재생 중인 모든 시퀀스 채널에 표시되는 요소(다중 영역 레이아웃이 있는 경우 여러 개) |
| isDefaultContent {boolean} | 재생 채널이 기본 또는 대체 채널로 간주되는 경우(즉, 우선 순위 1이 있고 일정이 없는 경우) true |
| hasContentChanged {boolean} | 지난 5분 동안 콘텐츠가 변경되면 true이고, 그렇지 않으면 false입니다. |
| lastContentChange {string} | 마지막 콘텐츠 변경 타임스탬프 |

>[!NOTE]
>
>선택적으로, 플레이어 환경 설정(재생 모니터링 활성화)에서 보다 고급 속성을 활성화할 수 있습니다.
>
>| 속성 | 설명 |
>|---|---|
>| isContentRendering {boolean} | GPU가 실제 콘텐츠를 재생하고 있는지 확인할 수 있으면 true입니다(픽셀 분석 기반). |

### 제한 사항 {#limitations}

기본 재생 모니터링에 대한 몇 가지 제한 사항이 아래에 나와 있습니다.

* 플레이어는 자체 재생 상태를 서버에 보고하므로 활성 연결이 필요합니다.

* GPU를 확인하는 `isContentRendering` 속성은 기본적으로 사용하도록 설정하는 데 훨씬 더 많은 리소스를 사용하며 플레이어 환경 설정에서 명시적 옵트인이 필요합니다. Adobe은 프로덕션 환경에서는 비디오와 함께 사용하지 말 것을 권장합니다.

* 이 기능은 시퀀스 채널에만 지원되며 대화형 채널(SPA) 사용 사례는 아직 다루지 않습니다.

* 지표가 아직 고객에게 완전히 노출되지는 않았지만 Adobe은 곧 대시보드와 유사한 보고 및 경고 메커니즘을 활성화하는 작업을 진행하고 있습니다.

### 기타 리소스 {#additional-resources}

자세한 내용은 다음 항목을 참조하십시오.

* Android™ 플레이어를 다운로드하려면 **Google Play**&#x200B;를 방문하세요. Android™ Watchdog 구현에 대한 자세한 내용은 [Android™ 플레이어 구현](implementing-android-player.md)을 참조하세요.

* Chrome OS 플레이어를 구현하려면 [Chrome 관리 콘솔](implementing-chrome-os-player.md)을 참조하십시오.

* AEM Screens Windows Player를 구성하려면 [Windows Player 구현](implementing-windows-player.md)을 참조하십시오.
