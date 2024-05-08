---
title: Screens 기능 팩 릴리스에 대한 릴리스 202401
description: 2024년 1월 2일에 릴리스된 AEM Screens 기능 팩 202401에 대해 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: fe4f7d593ccea91f6109a0c759aea3faa37ae471
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 4%

---

# 기능 팩 202401 릴리스 정보 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe 최신 버전의 6.5 Adobe Experience Manager(AEM 6.5)로 업그레이드하는 것이 좋습니다. 에서 최신 버전 정보 가져오기 [여기](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/release-notes/release-notes).

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 11.1을 출시했습니다.

AEM Screens 6.5.11.1용 최신 기능 팩 릴리스를 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe ID 사용. 다음 위치로 이동 **Adobe Experience Manager** 탭 및 검색 **스크린** 이라는 최신 기능 팩을 가져오려면 **AEM 6.5 Screens FP11.1**.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 202204의 릴리스 날짜는 2024년 1월 2일입니다.

### 새로운 기능 {#what-is-new}

이 릴리스에는 보안 수정 사항만 포함됩니다.

### 버그 수정 {#bug-fixes}

* AEM Screens 장치 &quot;유휴 텍스트&quot; 필드의 XSS 문제 (SCRNS-2614)

* 의 XSS 문제 `screens/dashboard/device.html` 를 통해 `Clear cache` 작업 대화 상자. (SCRNS-2632)

* 의 화면 플레이어 구성에서 XSS 문제 `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* 장치가 삭제되면 장치 제목 트리거에 저장된 XSS가 발생합니다. (SCRNS-2653)

* 의 XSS 문제 `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* 매개변수가 있는 반영된 XSS `item` 위치: `/screens/register-device-wizard.html`. (SCRNS-2670)

* 에 반영된 XSS `screens/dashboard/device.html` 를 통해 `returnPage` 매개 변수. (SCRNS-3056)

* assign-device-wizard.html에서 리디렉션을 엽니다. (SCRNS-3444)

* 장치 대시보드에서 리디렉션을 엽니다. (SCRNS-3443)

* 의 XSS 문제 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* 반복 일정 및 일정 추가 단추가 표시되지 않는 문제를 해결했습니다. 채널 예약에서 문제가 발견되었습니다. (SCRNS-2739)
