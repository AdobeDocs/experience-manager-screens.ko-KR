---
title: 기능 팩 202103에 대한 릴리스 노트
description: '"2021년 3월 5일 릴리스된 AEM Screens 기능 팩 202103에 대한 정보를 보려면 이 페이지를 따르십시오."'
feature: Feature Pack
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: aa1338fad19893e56ead4bb466e4f32a90116b65
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 4%

---


# 기능 팩 202103에 대한 릴리스 노트 {#release-notes-for-feature-pack}

>[!CAUTION]
>AEM(Adobe Experience Manager)의 최신 버전으로 업그레이드하는 것이 좋습니다. 스크린은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 7을 출시했습니다.

Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens 6.5.7 릴리스의 최신 기능 팩을 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;를 검색하여 **AEM 6.5 Screens FP7**&#x200B;이라는 이름의 최신 기능 팩을 가져옵니다.

## 릴리스 날짜 {#release-date}

AEM Screens 기능 팩 202103의 릴리스 날짜는 2021년 3월 5일입니다.

### 새로운 기능 {#what-is-new}

* **AEM Screens 플레이어 자동 등록**

   수천 명의 플레이어를 수동으로 등록하는 것은 매우 번거롭고 시간과 비용을 더합니다. 이 프로세스를 간소화하기 위해 플레이어 자동 등록 기능을 사용하면 AEM에서 구성 파일 또는 MDM(Mobile Device Management) 솔루션을 통해 플레이어로 프로비저닝할 수 있는 사전 공유 키를 지정할 수 있습니다.

   자세한 내용은 [플레이어 자동 등록](/help/user-guide/auto-registration-players.md)을 참조하십시오.


* **Enterprise Mobility Management를 사용하여 Android Player의 대량 프로비저닝**

   Android 플레이어를 일괄 배포할 때 AEM에 모든 단일 플레이어를 수동으로 등록하는 것은 번거롭습니다. VMWare Airwatch, MobileIron 또는 Samsung Knox와 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 원격으로 배포를 준비하고 관리하는 것이 좋습니다. AEM Screens Android 플레이어는 업계 표준 EMM AppConfig를 지원하여 원격 프로비저닝을 허용합니다.

   자세한 내용은 [Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation)를 사용하여 Android Player의 대량 제공을 참조하십시오.


### 버그 수정 {#bug-fixes}

* `clientlib` 및 `asset hashes` 컴퓨팅을 위한 성능이 개선되었습니다.

* 캐시가 무효화되지 않은 경우 SmartSync 마이그레이션이 플레이어를 중단합니다.

* 할당에 *OfflineConfig*&#x200B;이 있는 경우 오프라인 캐시가 생성되지 않았습니다.

* 레퍼러 정책 strict-origin-when-cross-origin이 지원되지 않으므로 오류가 발생한 티젠 플레이어에 대한 업데이트입니다.

* 할당된 채널의 일정 *반복* 필드를 변경하면 UI가 중단되었습니다.

* 쿼리 예외로 인해 오프라인 콘텐츠를 업데이트하지 못했습니다.

* 이제 인터랙티브한 경험의 인터랙션 중 전환 간 시간 지연이 수정되었습니다.

* 구성 업데이트 요청이 실패하여 빈 화면이 표시되었습니다.

### 릴리스된 AEM Screens 플레이어 {#released-aem-screens-players}

다음 AEM Screens 플레이어는 AEM 6.5 기능 팩 7용으로 출시되었습니다.

* Chrome OS
* Windows
* Linux

#### AEM Screens Player 다운로드 {#aem-screens-player-downloads}

최신 AEM Screens 플레이어를 다운로드하여 버그 수정에 대한 자세한 내용은 **[AEM Screens Player 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
