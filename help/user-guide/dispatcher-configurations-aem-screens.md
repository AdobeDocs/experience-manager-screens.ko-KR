---
title: AEM Screens용 Dispatcher 구성
seo-title: AEM Screens용 Dispatcher 구성
description: 이 페이지에서는 AEM Screens 프로젝트용 디스패처를 구성하기 위한 지침을 집중적으로 살펴봅니다.
seo-description: 이 페이지에서는 AEM Screens 프로젝트용 디스패처를 구성하기 위한 지침을 집중적으로 살펴봅니다.
feature: 스크린 관리
role: 개발자, 비즈니스 전문가
level: 중간
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---


# AEM Screens{#dispatcher-configurations-for-aem-screens}용 발송자 구성

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다.

다음 페이지에서는 AEM Screens 프로젝트에 대한 디스패처를 구성하기 위한 지침을 제공합니다.

>[!NOTE]
>
>디스패처가 사용 가능한 경우 디스패처 규칙에서 필터링하여 등록 서블릿에 대한 연결을 방지할 수 있습니다.
>
>디스패처가 없으면 OSGi 구성 요소 목록에서 등록 서블릿을 비활성화합니다.

## 전제 조건 {#pre-requisites}

AEM Screens 프로젝트에 대한 디스패처를 구성하려면 먼저 Dispatcher에 대해 알고 있어야 합니다.

자세한 내용은 [Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 구성을 참조하십시오.

## Dispatcher 구성 {#configuring-dispatcher}

AEM Screens 플레이어/장치는 인증된 세션을 사용하여 게시 인스턴스의 리소스에 액세스할 수도 있습니다. 따라서 여러 게시 인스턴스가 있는 경우 인증된 세션이 AEM Screens 플레이어/장치에서 들어오는 모든 요청에 대해 유효하도록 항상 동일한 게시 인스턴스로 이동되어야 합니다.

AEM Screens 프로젝트에 대한 디스패처를 구성하려면 아래 절차를 따르십시오.

### 고정 세션 활성화 {#enable-sticky-session}

단일 디스패처가 앞에 두고 있는 여러 게시 인스턴스를 사용하려면 `dispatcher.any` 파일을 업데이트하여 설정 지연을 활성화해야 합니다

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

한 디스패처가 앞에 하나의 게시 인스턴스를 두고 있는 경우, 로드 밸런서가 각 요청을 디스패처에 보낼 수 있으므로 디스패처의 설정 지연을 활성화해도 도움이 되지 않습니다. 이 경우, 아래 그림과 같이 **스티커** 필드에서 **활성화** 필드를 클릭하여 부하 균형 조정기 수준에서 활성화합니다.

![이미지](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

예를 들어, AWS ALB를 사용하는 경우, ALB 수준에서 고착성을 활성화하려면 애플리케이션 로드 밸런서에 대한 [타겟 그룹](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)을 참조하십시오. 1일 동안 고착성을 활성화합니다.

### 1단계:클라이언트 헤더 구성 중 {#step-configuring-client-headers}

`/clientheaders`섹션에 다음을 추가합니다.

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 2단계:스크린 필터 구성 {#step-configuring-screens-filters}

스크린 필터를 구성하려면 ***/filter***&#x200B;에 다음을 추가하십시오.

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

***/content/screens 경로***&#x200B;에 대해 디스패처 캐싱을 비활성화합니다.

스크린 플레이어는 인증된 세션을 사용하므로 디스패처는 플레이어가 `channels/assets`에 대한 스크린 요청을 캐시하지 않습니다.

디스패처 캐시에서 에셋이 제공되도록 에셋에 대한 캐시를 활성화하려면 다음을 수행해야 합니다.

* `/cache` 섹션에 `/allowAuthorization 1` 추가
* `/cache`의 `/rules` 섹션에 아래 규칙을 추가합니다.

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
