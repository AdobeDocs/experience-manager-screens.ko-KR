---
title: AEM Screens에 대한 Dispatcher 구성
seo-title: Dispatcher Configurations for AEM Screens
description: 이 페이지에서는 AEM Screens 프로젝트에 대한 Dispatcher 구성 지침을 중점적으로 다룹니다.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 3%

---

# AEM Screens에 대한 Dispatcher 구성{#dispatcher-configurations-for-aem-screens}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다.

다음 페이지에서는 AEM Screens 프로젝트에 대한 Dispatcher 구성을 위한 지침을 제공합니다.

>[!NOTE]
>
>Dispatcher를 사용할 수 있는 경우 Dispatcher 규칙에서 필터링하여 등록 서블릿에 대한 연결을 방지할 수 있습니다.
>
>Dispatcher가 없는 경우 OSGi 구성 요소 목록에서 등록 서블릿을 비활성화합니다.

AEM Screens 프로젝트에 대한 Dispatcher를 구성하려면 먼저 Dispatcher에 대한 사전 지식이 있어야 합니다.
을(를) 참조하십시오 [Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=ko-KR) 을 참조하십시오.

## 매니페스트 버전 v2에 대한 Dispatcher 구성 {#configuring-dispatcher}

>[!IMPORTANT]
>다음 Dispatcher 구성은 매니페스트 버전 v2에만 적용됩니다. 을(를) 참조하십시오 [매니페스트 버전 v3에 대한 Dispatcher 구성](#configuring-dispatcherv3) 매니페스트 버전 v3용

AEM Screens 플레이어 또는 장치는 인증된 세션을 사용하여 게시 인스턴스의 리소스에도 액세스합니다. 따라서 게시 인스턴스가 여러 개 있는 경우 인증된 세션이 AEM Screens 플레이어/장치에서 발생하는 모든 요청에 대해 유효하도록 요청이 항상 동일한 게시 인스턴스로 이동해야 합니다.

AEM Screens 프로젝트에 대한 Dispatcher를 구성하려면 아래 단계를 따르십시오.

### 고정 세션 활성화 {#enable-sticky-session}

단일 Dispatcher가 주도하는 여러 게시 인스턴스를 사용하려면 를 업데이트해야 합니다. `dispatcher.any` 고착성을 활성화하는 파일

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

한 개의 Dispatcher에 의해 앞에 하나의 게시 인스턴스가 있는 경우 로드 밸런서가 각 요청을 Dispatcher로 보낼 수 있으므로 Dispatcher에서 고착성을 활성화하는 것은 도움이 되지 않습니다. 이 경우 다음을 클릭합니다. **사용** 위치: **끈적임** 아래 그림과 같이 로드 밸런서 수준에서 활성화하기 위한 필드입니다.

![이미지](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

예를 들어 AWS ALB를 사용하는 경우 다음을 참조하십시오. [응용 프로그램 로드 밸런서의 대상 그룹](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) ALB 레벨에서 고착성을 활성화합니다. 1일 동안 고착성을 활성화합니다.

### 1단계: 클라이언트 헤더 구성 {#step-configuring-client-headers}

다음에 추가 `/clientheaders`섹션:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-명령**

### 2단계: 화면 필터 구성 {#step-configuring-screens-filters}

Screens 필터를 구성하려면 다음을 추가하십시오. ***/filter***.

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

### 3단계: Dispatcher 캐시 비활성화 {#step-disabling-dispatcher-cache}

다음에 대한 Dispatcher 캐싱 비활성화 ***/content/screens 경로***.

Screens 플레이어는 인증된 세션을 사용하므로 Dispatcher는 Screens 플레이어 요청을 캐시하지 않습니다. `channels/assets`.

자산이 Dispatcher 캐시에서 제공되도록 자산에 대한 캐시를 활성화하려면 다음을 수행해야 합니다.

* 추가 `/allowAuthorization 1` 위치: `/cache` 섹션
* 아래 규칙 추가 `/rules` 섹션 / `/cache`

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

## 매니페스트 버전 v3에 대한 Dispatcher 구성{#configuring-dispatcherv3}

Screens의 작동을 위해 게시 인스턴스를 앞에 두고 있는 디스패처에서는 이러한 필터 및 캐시 규칙을 허용해야 합니다.

### 매니페스트 버전 v3의 필수 구성 요소{#prerequisites3}

AEM Screens에 대해 Dispatcher(매니페스트 버전 v3)를 구성하기 전에 다음 두 가지 전제 조건을 따르는지 확인하십시오.

* 을(를) 사용하고 있는지 확인합니다. `v3 manifests`. 다음으로 이동 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` 및 다음을 확인합니다. `Enable ContentSync Cache` 이(가) 선택되지 않았습니다.

* Dispatcher 플러시 에이전트가 다음 위치에 구성되었는지 확인합니다. `/etc/replication/agents.publish/dispatcher1useast1Agent` 게시 인스턴스.

   ![이미지](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![이미지](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 필터  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### 캐시 규칙 {#cache-rules-v3}

* 추가 `/allowAuthorized "1"` 끝 `/cache` 의 섹션 `publish_farm.any`.

* 모든 Screens 플레이어는 인증된 세션을 사용하여 AEM(작성자/게시)에 연결합니다. 기본 Dispatcher는 이러한 URL을 캐시하지 않으므로 활성화해야 합니다.

* 추가 `statfileslevel "10"` 끝 `/cache` 의 섹션 `publish_farm.any`
이렇게 하면 캐시 docroot에서 최대 10개 수준의 캐싱을 지원하고 모든 것을 무효화하지 않고 콘텐츠가 게시될 때 그에 따라 무효화됩니다. 콘텐츠 구조의 깊이에 따라 이 수준을 자유롭게 변경할 수 있습니다.

* 다음에 추가 `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 에 다음 규칙 추가 `/rules` 의 섹션 `/cache` 위치: `publish_farm.any` 또는 다음을 포함하는 파일에 포함 `publish_farm.any`:

   ```
   ## Don't cache CSRF login tokens
   /0001
       {
       /glob "/libs/granite/csrf/token.json"
       /type "deny"
       }
   ## Allow Dispatcher Cache for Screens channels
   /0002
       {
           /glob "/content/screens/*.html"
           /type "allow"
       }
   ## Allow Dispatcher Cache for Screens offline manifests
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   ## Allow Dispatcher Cache for Assets
   /0004
       {
   
       /glob "/content/dam/*"
       /type "allow"
       }
   ## Disable Dispatcher Cache for Screens devices json
   /0005
       {
       /glob "/home/users/screens/*.json"
       /type "deny"
       }
   ## Disable Dispatcher Cache for Screens svc json
   /0006
       {
       /glob "/content/screens/svc.json"
       /type "deny"
       }
   ```

### segments.js에 대한 무효화 규칙 추가 {#invalidsegmentjs}

AEM Screens에서 타겟팅된 캠페인을 사용하는 경우 `segments.js file` AEM에 새 세그먼트를 추가하고 게시할 때 dispatcher에서 제공하는 를 무효화해야 합니다. 이 무효화 규칙이 없으면 새 타겟팅된 캠페인이 Screens 플레이어에서 작동하지 않습니다(대신 기본 콘텐츠가 표시됨).

* 무효화 규칙 추가 `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. 추가할 규칙은 다음과 같습니다.

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* 이 규칙은 다음을 확인합니다. `segments.js` 수정 시 파일이 무효화되고 최신 파일을 가져옵니다.
