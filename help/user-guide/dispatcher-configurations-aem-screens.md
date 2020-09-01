---
title: AEM Screens용 발송자 구성
seo-title: AEM Screens용 발송자 구성
description: 이 페이지에서는 AEM Screens 프로젝트용 디스패처를 구성하기 위한 지침을 집중적으로 설명합니다.
seo-description: 이 페이지에서는 AEM Screens 프로젝트용 디스패처를 구성하기 위한 지침을 집중적으로 설명합니다.
translation-type: tm+mt
source-git-commit: 8e8413221d0f79f8e46e15d0f00a710296883739
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 6%

---


# AEM Screens용 발송자 구성{#dispatcher-configurations-for-aem-screens}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다.

다음 페이지에서는 AEM Screens 프로젝트에 대해 발송자를 구성하기 위한 지침을 제공합니다.

>[!NOTE]
>
>발송자를 사용할 수 있는 경우 발송자 규칙에서 필터링하여 등록 서블릿에 대한 연결을 방지할 수 있습니다.
>
>디스패처가 없으면 OSGi 구성 요소 목록에서 등록 서블릿을 비활성화합니다.

## 전제 조건 {#pre-requisites}

AEM Screens 프로젝트에 대한 디스패처를 구성하려면 먼저 Dispatcher에 대해 알고 있어야 합니다.

자세한 내용은 [발송자](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 구성을 참조하십시오.

## Dispatcher 구성 {#configuring-dispatcher}

아래 절차에 따라 AEM Screens 프로젝트에 대한 디스패처를 구성합니다.

### 1단계:클라이언트 헤더 구성 {#step-configuring-client-headers}

섹션에 다음을 `/clientheaders`추가합니다.

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 2단계:스크린 필터 구성 {#step-configuring-screens-filters}

스크린 필터를 구성하려면 다음을 추가 ***/필터링합니다***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 3단계:발송자 캐시 비활성화 {#step-disabling-dispatcher-cache}

/content/screens 경로에 대한 발송자 캐싱 ***을 비활성화합니다***.

스크린 플레이어는 인증된 세션을 사용하므로 디스패처는 플레이어에서 요구하는 모든 스크린 세트를 캐시하지 않습니다 `channels/assets`.

에셋이 디스패처 캐시에서 제공되도록 에셋의 캐시를 활성화하려면 다음을 수행해야 합니다.

* 섹션 `/allowAuthorization 1` 에 `/cache` 추가
* 아래의 규칙 `/rule`을 `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
