---
title: AEM Screens을 위한 Dispatcher 구성
description: 이 페이지에서는 AEM Screens 프로젝트용 Dispatcher 구성에 대한 지침을 중점적으로 다룹니다.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# AEM Screens을 위한 Dispatcher 구성{#dispatcher-configurations-for-aem-screens}

Dispatcher은 Adobe Experience Manager의 캐싱 또는 로드 밸런싱 도구 또는 둘 다입니다.

다음 페이지에서는 AEM Screens 프로젝트용 Dispatcher을 구성하기 위한 지침을 제공합니다.

>[!NOTE]
>
>Dispatcher을 사용할 수 있는 경우 Dispatcher 규칙의 필터링을 통해 등록 서블릿에 대한 연결을 방지할 수 있습니다.
>
>Dispatcher이 없는 경우 OSGi 구성 요소 목록에서 등록 서블릿을 비활성화합니다.

AEM Screens 프로젝트에 대해 Dispatcher을 구성하기 전에 Dispatcher에 대해 알고 있어야 합니다.
자세한 내용은 [Dispatcher 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration)을 참조하십시오.

## 매니페스트 버전 v2에 대해 Dispatcher 구성 {#configuring-dispatcher}

>[!IMPORTANT]
>다음 Dispatcher 구성은 매니페스트 버전 v2에만 적용됩니다. 매니페스트 버전 v3의 [매니페스트 버전 v3에 대한 Dispatcher 구성](#configuring-dispatcherv3)을(를) 참조하십시오.

AEM Screens 플레이어 또는 장치는 인증된 세션을 사용하여 게시 인스턴스의 리소스에도 액세스합니다. 게시 인스턴스가 여러 개 있는 경우 인증된 세션이 AEM Screens 플레이어 또는 장치에서 발생하는 모든 요청에 대해 유효하도록 요청이 항상 동일한 게시 인스턴스로 이동해야 합니다.

AEM Screens 프로젝트용 Dispatcher을 구성하려면 아래 단계를 따르십시오.

### 고정 세션 활성화 {#enable-sticky-session}

단일 Dispatcher으로 이어지는 여러 게시 인스턴스를 사용하려면 `dispatcher.any` 파일을 업데이트하여 연결 기능을 사용하도록 설정하십시오.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

하나의 Dispatcher 앞에 하나의 게시 인스턴스가 있는 경우 로드 밸런서가 각 요청을 Dispatcher에 보낼 수 있으므로 Dispatcher에서 고착성을 활성화해도 도움이 되지 않습니다. 이 경우 아래 그림과 같이 로드 밸런서 수준에서 켜려면 **연결** 필드의 **사용**&#x200B;을(를) 클릭합니다.

![이미지](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

예를 들어 AWS ALB를 사용하는 경우 ALB 수준에서 연결 기능을 사용하려면 [응용 프로그램 로드 밸런서에 대한 Target 그룹](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)을 참조하십시오. 하루 동안 고착성을 활성화합니다.

### 1단계: 클라이언트 헤더 구성 {#step-configuring-client-headers}

`/clientheaders`섹션에 다음 내용을 추가하십시오.

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 2단계: Screens 필터 구성 {#step-configure-screens-filters}

Screens 필터를 구성하려면 ***`/filter`***에 다음을 추가하십시오.

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

***/content/screens 경로***&#x200B;에 대해 Dispatcher 캐싱을 사용하지 않도록 설정하십시오.

Screens 플레이어는 인증된 세션을 사용하므로 Dispatcher은 `channels/assets`에 대한 screens 플레이어 요청을 캐싱하지 않습니다.

에셋이 Dispatcher 캐시에서 제공하도록 에셋에 대한 캐시를 활성화하려면 다음을 수행합니다.

* `/cache` 섹션에 `/allowAuthorization 1` 추가
* `/cache`의 `/rules` 섹션에 아래 규칙 추가

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

## 매니페스트 버전 v3에 대해 Dispatcher 구성{#configuring-dispatcherv3}

Screens의 기능을 위해 게시 인스턴스 앞에 있는 디스패처에서 이러한 필터 및 캐시 규칙을 허용해야 합니다.

### 매니페스트 버전 v3의 필수 구성 요소{#prerequisites3}

AEM Screens용 Dispatcher(매니페스트 버전 v3)를 구성하기 전에 다음 두 가지 전제 조건을 따르십시오.

* `v3 manifests`을(를) 사용하고 있는지 확인하십시오. `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`(으)로 이동하여 `Enable ContentSync Cache`이(가) 선택 취소되었는지 확인합니다.

* 게시 인스턴스의 `/etc/replication/agents.publish/dispatcher1useast1Agent`에 Dispatcher 플러시 에이전트가 구성되어 있는지 확인하십시오.

  ![이미지](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![이미지](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 필터 {#filter-v3}

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

* `publish_farm.any`의 `/cache` 섹션에 `/allowAuthorized "1"`을(를) 추가합니다.

* 모든 AEM Screens 플레이어는 인증된 세션을 사용하여 AEM(작성자/게시)에 연결합니다. 기본적으로 Dispatcher은 이러한 URL을 캐시하지 않으므로 이를 활성화해야 합니다.

* `publish_farm.any`의 `/cache` 섹션에 `statfileslevel "10"` 추가
이 규칙은 캐시 docroot에서 최대 10개 수준까지 캐싱을 지원하고 모든 것을 무효화하지 않고 콘텐츠가 게시될 때 그에 따라 무효화합니다. 콘텐츠 구조의 깊이에 따라 이 수준을 자유롭게 변경할 수 있습니다.

* `/invalidate section in publish_farm.any`에 다음 추가

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* `publish_farm.any`의 `/cache` 또는 `publish_farm.any`에서 포함된 파일의 `/rules` 섹션에 다음 규칙을 추가하십시오.

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

AEM Screens에서 타깃팅된 캠페인을 사용하는 경우 AEM에 새 세그먼트를 추가하고 게시할 때 Dispatcher에서 제공하는 `segments.js file`을(를) 무효화해야 합니다. 이 무효화 규칙이 없으면 새 타겟팅된 캠페인이 AEM Screens 플레이어에서 작동하지 않습니다(대신 기본 콘텐츠가 표시됨).

* `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`에 무효화 규칙을 추가합니다. 추가할 규칙은 다음과 같습니다.

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

* 이 규칙을 사용하면 `segments.js` 파일이 무효화되고 수정 시 최신 파일을 가져올 수 있습니다.
