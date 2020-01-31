---
title: AEM Screens용 발송자 구성
seo-title: AEM Screens용 발송자 구성
description: 이 페이지에서는 AEM Screens 프로젝트에 대한 발송자 구성에 대한 지침을 설명합니다.
seo-description: 이 페이지에서는 AEM Screens 프로젝트에 대한 발송자 구성에 대한 지침을 설명합니다.
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: 9bee12b69ae85e84572b6f9e8c70f792895d9a32

---


# AEM Screens용 발송자 구성{#dispatcher-configurations-for-aem-screens}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다.

다음 페이지에서는 AEM Screens 프로젝트에 대한 발송자 구성 지침을 제공합니다.

>[!NOTE]
>디스패처가 사용 가능한 경우 디스패처 규칙에서 필터링하여 등록 서블릿에 대한 연결을 방지할 수 있습니다.
>발송자가 없는 경우 OSGi 구성 요소 목록에서 등록 서블릿을 비활성화합니다.

## 전제 조건 {#pre-requisites}

AEM Screens 프로젝트에 대한 디스패처를 구성하려면 먼저 디스패처에 대해 알고 있어야 합니다.

자세한 내용은 [Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 구성을 참조하십시오.

## Dispatcher 구성 {#configuring-dispatcher}

아래 절차에 따라 AEM Screens 프로젝트에 대한 디스패처를 구성합니다.

### 1단계:클라이언트 헤더 구성 {#step-configuring-client-headers}

다음 `/clientheaders`섹션을 추가합니다.

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 2단계:스크린 필터 구성 {#step-configuring-screens-filters}

스크린 필터를 구성하려면 다음을 추가 ***/필터링하십시오&#x200B;***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 3단계:발송자 캐시 비활성화 {#step-disabling-dispatcher-cache}

/content/screens 경로에 ******대해 디스패처 캐시를 비활성화합니다.
