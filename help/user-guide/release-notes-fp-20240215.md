---
title: Screens 기능 팩 릴리스에 대한 릴리스 20240215
description: 2024년 2월 15일에 릴리스된 AEM Screens 기능 팩 20240215에 대한 자세한 내용을 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e4149f5b-42c0-43c8-b275-ecbe90104a98
source-git-commit: fe4f7d593ccea91f6109a0c759aea3faa37ae471
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 5%

---

# 기능 팩 20240215 릴리스 정보 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe 최신 버전의 6.5 Adobe Experience Manager(AEM 6.5)로 업그레이드하는 것이 좋습니다. 에서 최신 버전 정보를 가져올 수 있습니다. [여기](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/release-notes/release-notes).

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 11.3을 출시했습니다.

AEM Screens 6.5.11.3용 최신 기능 팩 릴리스를 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe ID 사용. 다음 위치로 이동 **Adobe Experience Manager** 탭 및 검색 **스크린** 이라는 최신 기능 팩을 가져오려면 **AEM 6.5 Screens FP11.3**.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 20240215의 릴리스 날짜는 2024년 2월 15일입니다.

### 새로운 기능 {#what-is-new}

이 릴리스에는 보안 수정 사항만 포함됩니다.

### 버그 수정 {#bug-fixes}

* XSS에 대한 FP11.1의 앞에 제공된 수정 사항에서 토글 검사를 제거했습니다. `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* 의 XSS 문제 `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js`. (SCRNS-3973)
