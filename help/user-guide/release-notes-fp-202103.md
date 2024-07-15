---
title: 기능 팩 202103 릴리스 정보
description: 2021년 3월 5일에 릴리스된 AEM Screens 기능 팩 202103에 대해 자세히 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---

# 기능 팩 202103 릴리스 정보 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe 최신 버전의 Adobe Experience Manager(AEM)로 업그레이드하는 것이 좋습니다. AEM Screens은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 7을 출시했습니다.

Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens 6.5.7 릴리스용 최신 기능 팩을 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;을(를) 검색하여 **AEM 6.5 Screens FP7**(으)로 제목이 지정된 최신 기능 팩을 가져옵니다.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 202103의 릴리스 날짜는 2021년 3월 5일입니다.

### 새로운 기능 {#what-is-new}

* **플레이어의 AEM Screens 자동 등록**

  수천 명의 플레이어를 수동으로 일괄 등록하는 것은 번거롭고 시간과 비용을 추가한다. 이 프로세스를 단순화하기 위해 플레이어 자동 등록 기능을 사용하여 AEM에 미리 공유한 키를 지정할 수 있습니다. 이 키는 구성 파일 또는 MDM(모바일 장치 관리) 솔루션을 통해 플레이어에 제공할 수 있습니다.

  자세한 내용은 [플레이어 자동 등록](/help/user-guide/auto-registration-players.md)을 참조하십시오.


* **Enterprise Mobility Management를 사용하는 Android™ Player 일괄 프로비저닝**

  Android™ 플레이어를 대량으로 배포할 때 AEM에 모든 플레이어를 수동으로 등록하는 것은 번거로워집니다. `VMWare Airwatch`, `MobileIron` 또는 `Samsung Knox`과(와) 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 원격으로 배포를 프로비전 및 관리하는 것이 좋습니다. AEM Screens Android™ player는 원격 프로비저닝이 가능하도록 업계 표준 EMM AppConfig를 지원합니다.

  자세한 내용은 [Enterprise Mobility Management를 사용한 Android™ Player 일괄 프로비전](/help/user-guide/implementing-android-player.md#implementation)을 참조하십시오.


### 버그 수정 {#bug-fixes}

* `clientlib` 및 `asset hashes` 컴퓨팅에 대한 성능이 개선되었습니다.

* 캐시가 무효화되지 않은 경우 SmartSync 마이그레이션으로 플레이어가 중단됩니다.

* 할당에 *OfflineConfig*&#x200B;이(가) 있는 경우 오프라인 캐시가 만들어지지 않았습니다.

* 레퍼러 정책의 엄격한 원본-교차 원본이 지원되지 않으므로 중단된 `Tizen` 플레이어에 대한 업데이트가 지원되지 않습니다.

* 할당된 채널의 일정 *반복* 필드를 변경하면 UI가 손상됩니다.

* 쿼리 예외로 인해 오프라인 콘텐츠를 업데이트하지 못했습니다.

* 이제 대화형 경험에서 상호 작용 중 전환 간 시간 지연이 수정되었습니다.

* 구성 업데이트 요청에 실패하여 빈 화면이 표시되었습니다.

### 릴리스된 AEM Screens 플레이어

AEM 6.5 기능 팩 7용으로 출시된 AEM Screens 플레이어는 다음과 같습니다.

* Chrome
* Windows
* Linux®

#### AEM Screens 플레이어 다운로드

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 **[AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
