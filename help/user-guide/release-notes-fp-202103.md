---
title: 기능 팩 202103 릴리스 노트
description: '"2021년 3월 5일에 릴리스된 AEM Screens 기능 팩 202103에 대한 정보를 보려면 이 페이지를 따르십시오."'
feature: 기능 팩
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 4%

---

# 기능 팩 202103 릴리스 노트 {#release-notes-for-feature-pack}

>[!CAUTION]
>최신 버전의 Adobe Experience Manager(AEM)으로 업그레이드하는 것이 좋습니다. Screens에서는 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 7을 출시했습니다.

AEM Screens 6.5.7 릴리스의 최신 기능 팩은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 Adobe ID을 사용하여 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;에서 **AEM 6.5 Screens FP7**&#x200B;라는 최신 기능 팩을 가져옵니다.

## 릴리스 날짜 {#release-date}

AEM Screens 기능 팩 202103의 릴리스 날짜는 2021년 3월 5일입니다.

### 새로운 기능 {#what-is-new}

* **플레이어의 AEM Screens 자동 등록**

   수천 명의 선수를 수동으로 등록하는 것은 매우 번거롭고 시간과 비용을 더합니다. 이 프로세스를 단순화하기 위해 플레이어 자동 등록 기능을 사용하면 구성 파일 또는 MDM(Mobile Device Management) 솔루션을 통해 플레이어로 프로비저닝할 수 있는 AEM에서 미리 공유된 키를 지정할 수 있습니다.

   자세한 내용은 [플레이어의 자동 등록](/help/user-guide/auto-registration-players.md)을 참조하십시오.


* **Enterprise Mobility Management를 사용하여 Android Player의 벌크 프로비저닝**

   Android 플레이어를 일괄적으로 배포할 때 모든 단일 플레이어를 AEM에 수동으로 등록하는 것은 번거롭습니다. VMWare Airwatch, MobileIron 또는 Samsung Knox와 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 원격으로 배포를 프로비저닝하고 관리하는 것이 좋습니다. AEM Screens Android 플레이어는 원격 프로비저닝을 허용하도록 업계 표준 EMM AppConfig 를 지원합니다.

   자세한 내용은 [Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation)를 사용하여 Android Player의 벌크 프로비저닝 을 참조하십시오.


### 버그 수정 {#bug-fixes}

* `clientlib` 및 `asset hashes` 컴퓨팅 성능이 개선되었습니다.

* 캐시가 무효화되지 않은 경우 SmartSync 마이그레이션이 플레이어를 중단합니다.

* 할당에 *OfflineConfig*&#x200B;가 있는 경우 오프라인 캐시가 생성되지 않았습니다.

* 레퍼러 정책 strict-origin-when-cross-origin이 지원되지 않으므로 중단된 타이젠 플레이어에 대한 업데이트입니다.

* 지정된 채널의 예약 *반복* 필드를 변경하면 UI가 중단됩니다.

* 쿼리 예외로 인해 오프라인 콘텐츠 업데이트가 실패했습니다.

* 이제 대화형 경험에서 상호 작용 중 전환 간 시간 지연이 해결되었습니다.

* 구성 업데이트 요청에 실패하면 빈 화면이 나타납니다.

### 릴리스된 AEM Screens 플레이어 {#released-aem-screens-players}

다음 AEM Screens Players가 AEM 6.5 기능 팩 7용으로 출시되었습니다.

* Chrome OS
* Windows
* Linux

#### AEM Screens 플레이어 다운로드 {#aem-screens-player-downloads}

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 **[AEM Screens Player 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
