---
title: AEM SCREENS FAQ
description: AEM Screens 프로젝트 관련 FAQ에 대한 답변을 살펴보십시오.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# AEM SCREENS FAQ {#aem-screens-faqs}

이 주제에서는 AEM Screens 프로젝트와 관련하여 자주 묻는 FAQ에 대한 답변을 제공합니다.

## 빈 화면 문제 {#blank-screen}

>[!NOTE]
>문제를 제기하기 전에 기본 지원이나 고객 측 지원에서 시도해야 하는 나열된 필수 확인 사항입니다.

### 1. 검은색 화면이나 재생되지 않는 콘텐츠가 있는 고객을 위한 응급 처치 문제 해결 단계는 무엇입니까? {#troubleshooting-blank-screen}

* 채널 미리 보기가 작동하는지 확인합니다.
* 디스플레이 미리 보기가 작동하는지 확인
* 플레이어를 동일한 디스플레이에 시스템의 브라우저 확장으로 등록하고 제대로 작동하는지 확인하십시오.
* 시스템에서 실행 중인 플레이어로 다음 위치로 이동합니다. `http://localhost:24502`. 모든 콘텐츠가 올바르게 다운로드되었는지 확인합니다.
* 에셋을 검사하여 적절한 렌디션이 만들어지고 올바른 렌디션이 재생되는지 확인합니다.
* 예약된 컨텐츠가 있는지 확인하고 시간이 올바른지 확인합니다. 플레이어에서 설정한 시간이 올바른지 확인합니다.
* Inspect 플레이어 콘솔이 로그인하여 오류가 있는지 확인합니다. 마우스 오른쪽 버튼을 클릭하고 을 검사하여 콘솔 로그를 확인합니다. Windows 플레이어를 사용하는 경우 `CTRL + ALT +I` 로그를 볼 수 있도록 개발 콘솔을 표시합니다.

### 2. 기본 채널 또는 일정을 만들어 AEM Screens의 회색 화면 문제를 해결하는 방법

필드에 빈 화면이나 회색 화면을 표시하지 않으려면 우선 순위가 가장 낮은 모든 디스플레이에 할당된 기본 전역 채널 또는 일정을 만듭니다. 재생기에 이 콘텐츠가 디스크에 이미 캐시되어 있기 때문에(네트워크, 플레이어, 서버 또는 복제 때문에) 콘텐츠 업데이트에 문제가 발생하는 경우 제대로 재생되고 회색 화면을 피해야 합니다.

채널 또는 일정과 같은 다른 모든 콘텐츠는 우선 순위가 1보다 크므로 다른 콘텐츠는 우선 순위를 취하고 전역 채널 또는 일정 콘텐츠(우선 순위 1을 가진)는 폴백 옵션으로만 재생됩니다.

## 채널 관리 {#channel-management}

### 1. 온라인 채널과 오프라인 채널의 차이점은 무엇입니까? {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***온라인 채널*** 은 업데이트된 콘텐츠를 실시간 환경에 표시하지만 은 ***오프라인 채널*** 캐시된 콘텐츠를 표시합니다.

### 2. 온라인으로 채널을 만들려면 어떻게 해야 합니까? {#how-do-i-make-a-channel-online}

채널을 선택하고 작업 표시줄에서 채널 속성으로 이동합니다. 확인 **개발자 모드(온라인 채널 강제 설정)** 아래에 **채널** 탭을 클릭하여 채널을 온라인 상태로 만듭니다.

### 3. 채널 역할 필드의 용도는 무엇입니까? {#what-is-the-use-of-the-channel-role-field}

채널 역할은 작성자가 일반 경험에 직접 집중할 수 있도록 실행되는 실제 채널의 추상화입니다. 컨텍스트에서 채널을 고유하게 식별하는 일종의 태그(표시 또는 예약)로 생각할 수 있습니다.

### 4. 실제 채널 확인은 어떻게 수행됩니까? {#how-does-actual-channel-resolution-happen}

대상 *정적 참조*, 해상도는 지정된 경로를 따릅니다.

대상 *동적 참조*, 채널이 디스플레이에 할당되면(일정이 아님) 해결이 발생합니다. 표시 경로는 채널의 컨텍스트가 되며 해상도는 다음과 같이 발생합니다(최고 우선 순위에서 최저 우선 순위).

1. 디스플레이에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이에는 참조된 채널 이름과 일치하는 형제 노드가 있습니다
1. 디스플레이의 상위 위치에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이의 부모 위치에 참조된 채널 이름과 일치하는 자식 노드가 있습니다.

따라서 위치 폴더에 도달하고 현재 해당 폴더에서 중지합니다. 예를 들어 채널 폴더에 있는 채널은 참조할 수 없으며 위치 하위 트리의 채널만 참조하게 됩니다.

### 5. AEM Screens 채널에서 사용자 지정 clientlib 오프라인 구성을 설정하는 방법

빌드된 사용자 지정 클라이언트측 코드를 사용하는 경우 `clientlib` AEM Screens 채널에서는 다음 절차를 수행하여 `clientlib` 파일이 채널에 성공적으로 로드되었습니다. (`manifest.json`) 및 의 경로를 포함합니다. `clientlib`.

채널 편집기에서 아래 단계를 수행합니다.

1. 채널을 선택한 다음 을 선택합니다. **편집** 작업 표시줄에서
1. 사용자 지정을 추가할 구성 요소 선택 `clientlib`.
1. 구성 단추(렌치 아이콘)를 선택합니다.
1. 다음 위치로 이동 **오프라인 구성** 을(를) 탭하고에서 사용자 지정 clientlib에 대한 경로를 추가합니다. **클라이언트 측 라이브러리**.

## 장치 등록 {#device-registration}

### 1. 장치 온보딩 및 등록 요청과 같은 끝점을 찾으면 많은 장치를 스크립팅하고 이러한 장치를 등록할 수 있습니다. 이것을 분기 Wi-Fi에 고정하는 것 외에 이러한 요청을 보호할 수 있습니까? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

현재 등록은 작성자 인스턴스에서만 가능합니다. 등록 서비스는 인증되지 않지만 AEM에서 보류 중인 장치만 만들고 실제로 장치를 등록하거나 디스플레이를 할당하지 않습니다.

장치를 등록하려면(AEM에서 장치에 대한 사용자 만들기) AEM에 인증하고 현재 등록 마법사에 따라 수동으로 등록을 완료합니다. 이론적으로 악의적인 사용자는 여러 개의 보류 중인 장치를 만들 수 있지만 AEM 로그인이 없으면 어떤 장치도 등록할 수 없습니다.

### 2. 일부 인증 형식을 사용하여 HTTP GET 요청을 HTTP POST으로 변환하는 방법이 있습니까? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

등록 요청은 POST 요청입니다.

매개 변수로 전달되지 않고 세션에서 장치 ID를 가져오는 것이 좋습니다. 이렇게 하면 서버 로그, 브라우저 캐시 등이 정리됩니다. 보안 문제가 아닙니다. 의미상. GET은 서버에서 상태 변경이 없을 때 사용되고 POST은 상태 변경이 있을 때 사용됩니다.

### 3. 디바이스 등록 요청을 거절할 방법이 있습니까? {#is-there-a-way-to-decline-a-device-registration-request}

등록 요청을 거부할 수 없습니다. 대신 등록 요청은에 구성된 시간 제한 후에 만료되어야 합니다. `Adobe Experience Manager Web Console`. 기본적으로 이 값은 하루로 설정되고 메모리 캐시에 저장됩니다.

## 장치 모니터링 및 상태 보고서 {#device-monitoring-and-health-reports}

### 1. AEM Screens 플레이어에서 빈 화면이 표시되는 경우 어떻게 문제를 해결합니까?

빈 화면 문제를 해결하기 위해 다음 가능성을 확인하십시오.

* AEM에서 오프라인 콘텐츠를 푸시할 수 없음
* 채널에 콘텐츠가 없습니다.
* 현재 예약된 자산 중 어느 것도 표시되지 않습니다

### 2. AEM Screens 플레이어를 등록할 수 없고 해당 상태가 실패로 표시되면 어떻게 해야 합니까?

Apache Sling Referrer 필터 허용 을 활성화합니다. 이는 AEM Screens Player와 AEM Screens 서버 간 제어 프로토콜의 최적 작동을 위해 필요하다.

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성**
1. 다음 확인: **allow.empty** 옵션을 선택합니다.
1. **저장**&#x200B;을 선택합니다.

### 3. AEM Screens 플레이어를 등록하는 동안 장치에 FAILURE가 표시되고 콘솔 로그에 ENAME_NOT_FOUND 오류가 표시되는 경우 문제를 해결하는 방법

플레이어가 AEM Screens 서버 DNS를 찾을 수 없는 경우 이 문제가 발생할 수 있습니다. IP 주소를 사용하여 연결을 시도할 수 있습니다. 서버의 IP를 가져오려면 다음을 사용합니다. *arp &lt;server_dns_name>*.

### 4. AMS가 모든 장치에서 Android™ Watchdog를 구현하는 것을 권장합니까? Watchdog (Cordova) 플러그인이 APK의 일부로 포함됩니까? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

순수 Android™ API를 사용하는 교차 플랫폼 Android™ 워치독은 이미 APK의 일부입니다. 추가 소프트웨어가 필요하지 않습니다. 그러나 사용하는 장치에 따라 APK를 종료하여 전체 전원 주기에 대한 시스템 권한을 얻을 수 있습니다(`Powermanager` api), 필요한 경우. 제조업체 키를 사용하여 종료하지 않으면 애플리케이션이 종료되고 다시 시작되지만 전원 사이클은 켜지지 않습니다.

Android™ Player 구현 방법에 대한 자세한 내용은 [**Android™ Player 구현**](implementing-android-player.md).

### 5. Adobe/AMS는 각 장치를 모니터링하기 위해 권장하는 타사 원격 모니터링 및 경고 도구(소프트웨어)를 선택하십시오. {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

모니터링 및 경고에서 원하는 내용에 따라 새로운 기능 AEM Screens 알림 서비스는 장치가 잠시 동안 핑되지 않았을 때 알려줍니다. 타사 도구는 운영 체제(OS), 해당 기능 및 고객의 특정 요구 사항에 따라 다릅니다.

장치 활동을 모니터링할 수 있는 위치에 대한 자세한 내용은 [**AEM 화면 알림 서비스**](screens-notifications-service.md).

## AEM 스크린 플레이어

### 1. Chrome 브라우저 플러그인으로 ChromeOS 플레이어를 설치하는 방법? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS 플레이어는 실제 Chrome 플레이어 장치 없이 개발자 모드에서 Chrome 브라우저 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 따르십시오.

1. 선택 [여기](https://download.macromedia.com/screens/) 최신 Chrome 플레이어를 다운로드하려면 다음을 수행하십시오.
1. 압축을 풀고 디스크에 저장합니다.
1. Chrome 브라우저를 열고 을 선택합니다. **확장** 메뉴에서 선택하거나 을(를) 직접 탐색하여 ***chrome://extensions***.
1. 전환 **개발자 모드** 오른쪽 상단 모서리에서
1. 선택 **로드 압축 해제됨** 왼쪽 상단 모서리에서 압축을 푼 Chrome Player를 로드합니다.
1. 확장 목록에서 사용할 수 있는 경우 다음을 확인하십시오 **AEM Screens Chrome 플레이어** 플러그인입니다.
1. 새 탭을 열고 다음을 선택합니다. **앱** 아이콘 을 왼쪽 상단 모서리에서 찾거나 ***chrome://apps***.
1. 다음 항목 선택 **AEM Screens** 플러그인. 기본적으로 플레이어는 전체 화면 모드로 실행됩니다. 누르기 **Esc** 전체 화면 모드를 종료합니다.

### 2. Screens 플레이어가 사용자 지정 오류 처리기로 게시 인스턴스를 통해 인증할 수 없는 경우 문제를 해결하는 방법

AEM Screens 플레이어가 시작되면 (으)로 요청을 수행합니다. ***/content/screens/svc.ping.json***: 플레이어에 404 오류가 발생하는 경우입니다. 플레이어는 게시 인스턴스에 대해 인증하기 위한 인증 요청을 시작합니다. 게시 인스턴스에 사용자 지정 오류 처리기가 있는 경우 익명 사용자에 대한 404 상태 코드가 반환되는지 확인하십시오. ***/content/screens/svc.ping.json***.

### 3. Android™ Player에서 장치 화면 상태를 설정하는 방법 {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Android™ 플레이어에서 Stay Awake를 켜려면 아래 단계를 따르십시오.

1. Android™ 플레이어 설정 > **정보**.
1. 활성화하려면 빌드 번호를 7번 탭하세요. **개발자 옵션** 위치: **설정**.
1. 다음으로 이동 **개발자 옵션**.
1. 사용 **깨어 있어라**.

### 4. Windows 플레이어에 대해 창 모드를 활성화하는 방법{#enable-player}

Windows 플레이어에는 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### 5. AEM Screens 플레이어가 로그인 요청을 계속 보내는 경우 문제를 해결하는 방법

에 요청을 지속적으로 보내는 AEM Screens 플레이어의 문제를 해결하려면 아래 단계를 따르십시오. `/content/screens/svc.json` 및 `/libs/granite/core/content/login.validate/j_security_check`:

1. AEM Screens 플레이어가 시작되면 다음을 요청합니다. `/content/screens/svc.json`. 플레이어가 응답에서 404 상태 코드를 받으면 를 사용하여 인증 요청을 시작합니다. `/libs/granite/core/content/login.validate/j_security_check` 에 대해 *게시* 인스턴스. 에 사용자 지정 오류 처리기가 있는 경우 *게시* 예를 들어 의 익명 사용자에 대한 404 상태 코드를 반환해야 합니다. `/content/screens/svc.json` 또는 `/content/screens/svc.ping.json`.

1. Dispatcher 구성에서 이러한 요청이 허용되는지 확인 `/filters`.

   다음을 참조하십시오 [화면 필터 구성](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) 을 참조하십시오.

1. Dispatcher 재작성 규칙이 화면 경로를 다른 경로로 다시 쓰고 있는지 확인합니다.

1. 다음을 보유한 경우 확인 `/etc/map` 에 대한 규칙 *작성자* 또는 *게시* 인스턴스 및 스크린 경로가 일치하는 대상 `sling:match` 내부적으로 다른 경로로 리디렉션되었습니다. 의 정확한 URL 확인 `/system/console/jcrresolver` 는 다음을 식별하는 데 도움이 됩니다. *게시* 인스턴스가 이러한 URL을 다른 경로에 다시 쓰고 있습니다.

1. Apache Sling Resource Resolver Factory 구성으로 인해 내부 재쓰기가 발생하는지 확인하십시오.

### 6. 플레이어 API에서 디스플레이 및 장치의 세부 정보를 가져오는 방법

다음을 통해 디스플레이 및 장치에 대한 세부 정보를 가져올 수 있습니다.

* **내부 JS API**
* **ContextHub 저장소**: 세 개의 ContextHub 저장소가 `/libs/screens/clientlibs/contexthub` 채널, 장치 및 정보를 표시합니다.

  다음 ContentHub 저장소 값을 사용하려면 아래 단계를 따르십시오.

   * 채널 속성을 편집하고 개인화 탭의 ContextHub 경로를 값으로 설정합니다(위에 언급).
   * 채널 JS에서 다음을 사용할 수 있습니다.

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## 일반 문제 해결 팁 {#general-troubleshooting-tips}

### 1. A/P 화면 오류를 방지하기 위해 Livefyre를 비활성화하는 방법

다음을 수행하여 로그 오류가 발생하지 않도록 Livefyre를 비활성화합니다.

1. ***Livefyre 번들 비활성화:***

   * 다음으로 이동 `https://<host>:<port>/system/console/bundles`.
   * AEM Livefyre 번들 검색: `com.adobe.cq.social.cq-social-livefyre`.
   * 선택 **중지**.

1. ***Livefyre Poller 비활성화:***

   * CRXDE Lite에서 다음으로 이동 `/etc/importers/polling/livefyre-poller/jcr:content`.
   * 속성 추가 *활성화됨* 유형 *부울*.
   * 설정 **enabled 속성** 끝 **false**.

### 2. Oak 색인 정보를 추가하는 방법 {#add-oak-index-info}

AEM Screens은 제품에서 사용하는 쿼리에 대한 색인 정의를 만듭니다.
있는 경우 *쿼리 순회 WARN* 다음에서 `error.log`를 클릭하여 쿼리에 대한 사용자 지정 색인을 만듭니다. 다음을 참조하십시오 [인덱스 구성](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) 을 참조하십시오.

에서 추가 리소스를 볼 수도 있습니다. [Oak 설명서](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. v3 매니페스트를 구성하는 데 필요한 사항 {#configure-v3}

v3 Manifest를 활성화하려면 다음을 수행하십시오.

* Dispatcher를 업데이트합니다.
다음을 참조하십시오 [매니페스트 버전 v3에 대한 Dispatcher 구성](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) 을 참조하십시오.

* 사용자 지정 구성 요소를 업데이트합니다.
다음을 참조하십시오 [사용자 지정 처리기용 템플릿](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) 을 참조하십시오.

* 에서 ContentSync 비활성화 `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* 에서 SmartSync 활성화 `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* 편집 `channel/experience fragment/page components`.

* 다음 위치로 이동 **오프라인 구성** 탭.

* 입력 `clientlibs `매니페스트에 추가해야 하는 정적 파일의 및 폴더입니다.

### 4. 패키지 screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 및 screens 코어 번들이 설치되어 있지만 활성화되어 있지 않은 경우 어떻게 해야 합니까?

AMS 커넥터가 작동할 AEM 6.5 기능 팩 8 의 최소 버전을 설치합니다. 다음을 참조하십시오 [사용 가능](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) 따라서 최소 버전의 AEM Screens 기능 팩을 가져올 수 있습니다.

### 5. 화면에서 CQ 링크 외부화 서비스를 구성하는 방법

이 서비스는 작성자 및 게시 인스턴스에 대한 공개 호스트 이름을 정의하는 데 사용되며 값은 장치 서버 URL을 업데이트하고 ContextHub 타겟팅에도 사용됩니다.

Screens의 CQ 링크 외부화 서비스는 다음을 통해 구성할 수 있습니다.

1. 다음으로 이동 `http://localhost:4502/system/console/configMgr`
1. 일별 CQ 링크 외부화
1. 의 호스트 이름 변경 `author/publish` 필요에 따라 항목