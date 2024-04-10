---
title: 기능 팩 202103 릴리스 정보
description: 2021년 3월 5일에 릴리스된 AEM Screens 기능 팩 202103에 대해 자세히 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 2%

---

# 기능 팩 202103 릴리스 정보 {#release-notes-for-feature-pack}

>[!CAUTION]
>최신 버전의 Adobe Experience Manager(AEM)로 업그레이드하는 것이 좋습니다. AEM Screens은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 7을 출시했습니다.

AEM Screens 6.5.7 릴리스의 최신 기능 팩을 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe ID 사용. 다음으로 이동 **Adobe Experience Manager** 탭 및 검색 **스크린** 이라는 최신 기능 팩을 가져오려면 **AEM 6.5 Screens FP7**.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 202103의 릴리스 날짜는 2021년 3월 5일입니다.

### 새로운 기능 {#what-is-new}

* **AEM Screens 플레이어 자동 등록**

  수천 명의 플레이어를 수동으로 일괄 등록하는 것은 번거롭고 시간과 비용을 추가한다. 이 프로세스를 단순화하기 위해 플레이어 자동 등록 기능을 사용하여 AEM에 미리 공유한 키를 지정할 수 있습니다. 이 키는 구성 파일 또는 MDM(모바일 장치 관리) 솔루션을 통해 플레이어에 제공할 수 있습니다.

  다음을 참조하십시오 [플레이어 자동 등록](/help/user-guide/auto-registration-players.md) 을 참조하십시오.


* **Enterprise Mobility Management를 사용한 Android™ Player 일괄 프로비저닝**

  Android™ 플레이어를 대량으로 배포할 때 모든 플레이어를 AEM에 수동으로 등록하는 것은 지루해집니다. 다음과 같은 EMM(엔터프라이즈 모빌리티 관리) 솔루션을 사용하는 것이 좋습니다. `VMWare Airwatch`, `MobileIron`, 또는 `Samsung Knox` 배포를 원격으로 프로비저닝하고 관리합니다. AEM Screens Android™ 플레이어는 원격 프로비저닝을 허용하도록 업계 표준 EMM AppConfig를 지원합니다.

  다음을 참조하십시오 [Enterprise Mobility Management를 사용한 Android™ Player 일괄 프로비저닝](/help/user-guide/implementing-android-player.md#implementation) 을 참조하십시오.


### 버그 수정 {#bug-fixes}

* 향상된 컴퓨팅 성능 `clientlib` 및 `asset hashes`.

* 캐시가 무효화되지 않은 경우 SmartSync 마이그레이션으로 플레이어가 중단됩니다.

* 할당에 오프라인 캐시가 있는 경우 생성되지 않음 *OfflineConfig*.

* 업데이트 대상: `Tizen` 레퍼러 정책의 strict-origin-when-cross-origin이 지원되지 않아 중단된 플레이어.

* 할당된 채널의 일정 변경 *반복* 필드가 UI를 손상시키고 있습니다.

* 쿼리 예외로 인해 오프라인 콘텐츠를 업데이트하지 못했습니다.

* 이제 대화형 경험의 상호 작용 중 전환 간 시간 지연이 수정되었습니다.

* 구성 업데이트 요청 실패로 인해 빈 화면이 발생했습니다.

### 릴리스된 AEM Screens 플레이어

AEM 6.5 기능 팩 7용으로 출시된 AEM Screens 플레이어는 다음과 같습니다.

* 크롬 OS
* Windows
* Linux®

#### AEM Screens 플레이어 다운로드

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 를 참조하십시오. **[AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/index.html)**.
