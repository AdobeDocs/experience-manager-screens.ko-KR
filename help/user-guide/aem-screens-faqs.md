---
title: AEM Screens FAQ
seo-title: AEM Screens FAQs
description: AEM Screens 프로젝트와 관련된 FAQ에 대한 답변을 보려면 이 페이지를 따르십시오.
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: a3bed3baf7e825299a82ccf624c3cdf876830cd0
workflow-type: tm+mt
source-wordcount: '2119'
ht-degree: 1%

---

# AEM Screens FAQ {#aem-screens-faqs}

다음 섹션에서는 AEM Screens 프로젝트와 관련하여 자주 묻는 몇 가지 FAQ에 대한 답변을 제공합니다.

## 빈 화면 문제 {#blank-screen}

>[!NOTE]
>문제가 발생하기 전에 기본 지원 또는 고객 측 지원에 의해 시도해야 하는 나열된 필수 확인입니다.

### 1. 검정색 화면 또는 재생되지 않는 컨텐츠에 직면하는 고객을 위한 AID 문제 해결 단계는 무엇입니까? {#troubleshooting-blank-screen}

* 채널 미리 보기가 작동하는지 확인합니다.
* 디스플레이 미리 보기가 작동하는지 확인
* 동일한 디스플레이에 플레이어를 시스템의 브라우저 확장으로 등록하고 제대로 작동하는지 확인하십시오.
* 시스템에서 실행 중인 플레이어를 사용하여 `http://localhost:24502`. 모든 컨텐츠가 올바르게 다운로드되었는지 확인합니다.
* 적절한 표현물이 만들어지고 올바른 표현물이 재생되고 있는지 자산을 확인합니다.
* 예약된 컨텐츠와 시간이 올바른지 확인합니다. 플레이어에서 설정된 시간이 올바른지 확인합니다.
* Inspect 플레이어 콘솔이 로그인하고 오류를 확인합니다. 마우스 오른쪽 단추를 클릭하고 검사하여 콘솔 로그를 확인합니다. windows 플레이어를 사용하는 경우 `CTRL + ALT +I` 로그를 볼 개발 콘솔을 표시합니다.

### 2. 기본 채널 또는 일정을 만들어 AEM Screens에서 회색 화면 문제를 해결하는 방법

필드의 빈 화면이나 회색 화면을 사용하지 않으려면 우선 순위가 가장 낮은 모든 디스플레이에 할당된 기본 전역 채널 또는 일정을 만드십시오. 플레이어에 이 컨텐츠가 이미 디스크에 캐시되어 있으므로 컨텐츠 업데이트(네트워크, 플레이어, 서버 또는 복제로 인해)에 문제가 발생하는 경우 제대로 재생되고 회색 화면이 표시되지 않습니다.

채널 또는 일정과 같은 다른 모든 컨텐츠는 우선 순위가 1보다 높으므로 다른 컨텐츠는 우선 순위를 가지며 글로벌 채널 또는 예약 컨텐츠(우선 순위 1이 있음)는 폴백 옵션으로만 재생됩니다.

## 채널 관리 {#channel-management}

### 1. 온라인 채널과 오프라인 채널의 차이점은 무엇입니까? {#what-is-the-difference-between-an-online-and-an-offline-channel}

***온라인 채널***&#x200B;은 실시간 환경에서 업데이트된 컨텐츠를 표시하는 반면, ***오프라인 채널***&#x200B;은 캐시된 컨텐츠를 보여줍니다.

### 2. 온라인으로 채널을 만들려면 어떻게 해야 합니까? {#how-do-i-make-a-channel-online}

채널을 선택하고 작업 표시줄에서 채널 속성으로 이동합니다. 확인 **개발자 모드(채널이 온라인 상태가 되도록 강제)** 아래에 **채널** 탭을 클릭하여 채널을 온라인으로 만듭니다.

### 3. 채널 역할 필드의 사용 방법 {#what-is-the-use-of-the-channel-role-field}

채널 역할 은 작성자가 일반 경험에 직접 집중할 수 있도록 실행되는 실제 채널을 추상화하는 것입니다. 이를 컨텍스트(표시 또는 예약)에서 채널을 고유하게 식별하는 태그의 종류로 생각할 수 있습니다.

### 4. 실제 채널 해상도는 어떻게 발생합니까? {#how-does-actual-channel-resolution-happen}

대상 *정적 참조*&#x200B;를 설정하는 경우 해상도는 지정된 경로를 따릅니다.

대상 *동적 참조*&#x200B;의 경우 채널이 표시(스케줄이 아님)에 할당되면 해결됩니다. 표시 경로가 채널의 컨텍스트가 되고 해상도는 다음과 같이 발생합니다(최고 - 최저 우선순위).

1. 디스플레이에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이에는 참조된 채널 이름과 일치하는 동위 노드가 있습니다
1. 디스플레이의 상위 위치에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이의 그랜드 상위 위치에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다

따라서 위치 폴더에 도달하여 그 시점에서 중지될 때까지(따라서 위치 하위 트리의 채널만, 예를 들어 채널 폴더에 있는 채널을 참조할 수 없습니다).

### 5. AEM Screens 채널에서 Custom clientlib 오프라인 구성을 설정하는 방법

빌드된 사용자 지정 클라이언트측 코드를 사용하는 경우 `clientlib` AEM Screens 채널에서 다음 단계를 수행하여 `clientlib` 파일이 채널에 로드되었습니다(`manifest.json`) 및에 의 경로가 포함됩니다. `clientlib`.

채널 편집기에서 아래 절차를 따르십시오.

1. 채널을 선택하고 을(를) 클릭합니다. **편집** 작업 표시줄에서 채널 편집기를 엽니다.
1. 사용자 지정 항목을 추가할 구성 요소를 선택합니다 `clientlib`.
1. 구성 단추(공구모양 아이콘)를 클릭합니다.
1. 로 이동합니다 **오프라인 구성** 탭에서 사용자 지정 clientlib에 대한 경로를 추가합니다. **클라이언트 측 라이브러리**.

## 장치 등록 {#device-registration}

### 1. 장치 온보딩 및 등록 요청과 같은 끝점을 발견하면 많은 장치를 스크립팅하여 이러한 장치를 등록할 수 있습니다. 이를 분기 Wi-Fi에 잠그는 것 외에도 이러한 요청을 보호할 수 있습니까? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

현재 등록은 작성자 인스턴스에서만 사용할 수 있습니다. 등록 서비스가 인증되지 않았지만 AEM에 보류 중인 장치만 만들고 실제로 장치를 등록하거나 디스플레이를 할당하지 않습니다.

장치를 등록하려면(AEM에서 장치에 대한 사용자를 만드는 것을 의미) AEM에 인증해야 하며 현재 등록 마법사를 수동으로 수행하여 등록을 완료해야 합니다. 이론적으로는 악성 사용자가 몇 개의 보류 중인 장치를 만들 수 있지만 AEM 로그인 없이 등록할 수 없습니다.

### 2. HTTP GET 요청을 인증 형태를 사용하여 HTTP POST으로 변환하는 방법이 있습니까? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

등록 요청은 POST 요청입니다.

매개 변수로 전달되지 않고 세션에서 장치 ID를 가져오는 것이 좋습니다. 이렇게 하면 서버 로그, 브라우저 캐시 등이 정리됩니다. 현재 보안 문제가 아닙니다. 서버에서 상태 변경이 없는 경우 의미상 GET이 사용되고 상태가 변경될 때 POST이 사용됩니다.

### 3. 장치 등록 요청을 거절할 방법이 있습니까? {#is-there-a-way-to-decline-a-device-registration-request}

등록 요청은 거절할 수 없습니다. 대신, 등록 요청은에 구성된 시간 제한 후에 만료됩니다. `Adobe Experience Manager Web Console`. 기본적으로 이 값은 하루로 설정되고 메모리 캐시에 저장됩니다.

## 장치 모니터링 및 상태 보고서 {#device-monitoring-and-health-reports}

### 1. AEM Screens 플레이어에 빈 화면이 표시되는 경우 문제를 어떻게 해결합니까? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

빈 화면 문제를 해결하려면 다음 가능성을 확인하십시오.

* AEM에서 오프라인 콘텐츠를 푸시할 수 없습니다.
* 채널에 컨텐츠가 없습니다
* 현재 시간에 표시하도록 예약된 자산이 없습니다

### 2. AEM Screens 플레이어를 등록할 수 없고 해당 상태가 실패로 표시되면 어떻게 해야 합니까? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Apache Sling 레퍼러 필터 Allow Empty 를 활성화해야 합니다. 이 단계는 AEM Screens Player와 AEM Screens 서버 간의 제어 프로토콜을 최적의 상태로 운영하기 위해 필요합니다.

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성**
1. 을(를) 확인합니다. **allow.empty** 선택 사항입니다.
1. **저장**&#x200B;을 클릭합니다.

### 3. AEM Screens 플레이어를 등록하는 동안 장치에 FAILURE가 표시되고 콘솔 로그에 ENAME_NOT_FOUND 오류가 표시되는 경우 문제를 해결하는 방법 {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

이 문제는 플레이어가 AEM Screens 서버 DNS를 찾을 수 없는 경우 발생할 수 있습니다. IP 주소를 사용하여 연결할 수 있습니다. 서버의 IP를 얻으려면 다음을 사용하십시오. *arp &lt;server_dns_name>*.

### 4. AMS는 모든 장치에서 Android Watchdog를 구현하는 것을 권장합니까? Cordova(Watchdova) 플러그인이 APK의 일부로 포함됩니까? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

순수 Android API를 사용하는 교차 플랫폼 Android 감시는 이미 앱의 일부입니다. 추가 소프트웨어는 필요하지 않지만 사용 중인 장치에 따라 전체 전원 주기(Powermanager api)에 대한 시스템 권한을 얻기 위해 앱을 사임해야 할 수도 있습니다. 제조업체 키를 사용하여 포기하지 않으면 애플리케이션을 종료하고 다시 시작하지만 전원 사이클은 아닙니다.

Android Player 구현 방법에 대한 자세한 내용은 다음을 참조하십시오. [**Android Player 구현**](implementing-android-player.md).

### 5. Adobe/AMS가 각 장치를 모니터링하기 위해 권장하는 타사 원격 모니터링 및 경고 도구(소프트웨어)는 무엇입니까?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

모니터링 및 경고에서 원하는 내용에 따라 새 기능 AEM Screens 알림 서비스가 잠시 후 장치가 ping되지 않았는지 알려줍니다. 타사 도구는 운영 체제(OS), 기능 및 고객의 특정 요구 사항에 따라 다릅니다.

장치 활동을 모니터링할 수 있는 위치에 대한 자세한 내용은 [**AEM Screens 알림 서비스**](screens-notifications-service.md).

## AEM 스크린 플레이어 {#aem-screens-player}

### 1. Chrome 브라우저 플러그인으로 ChromeOS 플레이어를 설치하는 방법 {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS 플레이어는 실제 chrome 플레이어 장치가 필요 없는 개발자 모드에서 Chrome Browser 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 수행하십시오.

1. 클릭 [여기](https://download.macromedia.com/screens/) 최신 Chrome Player를 다운로드하려면 다음을 수행하십시오.
1. 압축을 풀고 디스크에 저장합니다.
1. Chrome 브라우저를 열고 을(를) 선택합니다. **확장** 메뉴에서 또는 직접 ***chrome://extensions***.
1. 켜기 **개발자 모드** 오른쪽 상단 모서리에서
1. 클릭 **압축을 푼 로드** 왼쪽 상단 모서리에서 압축을 푼 Chrome 플레이어를 로드합니다.
1. 확인 **AEM Screens Chrome Player** 확장 목록에서 를 사용할 수 있는 경우 플러그인을 선택합니다.
1. 새 탭을 열고 **앱** 왼쪽 상단 모서리에서 아이콘을 클릭하거나 ***chrome://apps***.
1. 클릭 **AEM Screens** Chrome Player를 실행하는 플러그인입니다. 기본적으로 플레이어가 전체 화면 모드로 실행됩니다. 누르기 **esc** 전체 화면 모드를 종료합니다.

### 2. Screens 플레이어가 사용자 지정 오류 핸들러를 사용하여 게시 인스턴스를 통해 인증할 수 없는 경우 문제를 해결하는 방법 {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens 플레이어가 시작되면 ***/content/screens/svc.ping.json***&#x200B;인 경우, 플레이어에 404 오류가 발생합니다. 플레이어가 게시 인스턴스에 대해 인증하기 위한 인증 요청을 시작합니다. 게시 인스턴스에 사용자 지정 오류 처리기가 있는 경우 익명 사용자에 대한 404 상태 코드를 ***/content/screens/svc.ping.json***.

### 3. Android Player에서 장치 화면을 켜는 방법 {#how-to-set-the-device-screen-stay-on-in-an-android-player}

아래 절차에 따라 모든 Android 플레이어에서 대기 중 을 켜십시오.

1. Android 플레이어 설정 —> 으로 이동합니다. **정보**
1. 빌드 번호를 7번 눌러 **개발자 옵션** in **설정**
1. 다음으로 이동 **개발자 옵션**
1. 활성화 **깨어 있으시오**

### 4. Windows 플레이어에 대해 창 모드를 활성화하는 방법{#enable-player}

Windows Player에 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### 5. AEM Screens 플레이어가 계속해서 로그인 요청을 보내는 경우 문제를 해결하는 방법{#requests-login}

아래 절차에 따라 에 요청을 계속 보내는 AEM Screens 플레이어의 문제를 해결하십시오 `/content/screens/svc.json` 및 `/libs/granite/core/content/login.validate/j_security_check`:

1. AEM Screens 플레이어가 시작되면 다음과 같이 요청합니다. `/content/screens/svc.json`. 플레이어가 응답에 404 상태 코드를 받으면 다음을 사용하여 인증 요청을 시작합니다 `/libs/granite/core/content/login.validate/j_security_check` 반대 *게시* 인스턴스. 에 사용자 지정 오류 처리기가 있는 경우 *게시* 예를 들어 익명 사용자에 대한 404 상태 코드를 `/content/screens/svc.json` 또는 `/content/screens/svc.ping.json`.

1. 디스패처 구성에서 이러한 요청을 허용하는지 확인합니다. `/filters`.

   자세한 내용은 [스크린 필터 구성](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 자세한 내용

1. 디스패처 재작성 규칙이 스크린 경로를 다른 경로에 다시 작성하는지 확인합니다.

1. 확인 `/etc/map` 의 규칙 *작성자* 또는 *게시* 인스턴스 및 화면 경로가 `sling:match` 내부적으로 다른 경로로 리디렉션되었습니다. 에서 정확한 URL 확인 `/system/console/jcrresolver` 은 *게시* 인스턴스가 이러한 URL을 다른 경로에 다시 작성하고 있습니다.

1. Apache Sling Resource Resolver Factory 구성에서 내부 다시 쓰기가 발생하는지 확인합니다.

### 6. 플레이어 API에서 디스플레이 및 장치의 세부 사항을 가져오는 방법

다음을 통해 디스플레이 및 장치의 세부 사항을 가져올 수 있습니다.

* **내부 JS API**
* **ContextHub 저장소**: 세 가지 ContextHub 저장소는 `/libs/screens/clientlibs/contexthub` 채널, 장치 및 디스플레이 정보를 표시하려면

   이러한 ContentHub 저장소 값을 사용하려면 아래 절차를 따르십시오.

   * 채널 속성을 편집하고 개인화 탭의 ContextHub 경로를 값(위에 설명된 대로)으로 설정합니다.
   * 채널 JS에서 다음을 사용할 수 있습니다.

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 일반 문제 해결 팁 {#general-troubleshooting-tips}

### 1. A/P 스크린 오류를 방지하기 위해 Livefyre를 비활성화하는 방법 {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

로그 오류를 방지하기 위해 Livefyre를 비활성화하려면

1. ***Livefyre 번들 비활성화:***

   * 다음으로 이동 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * AEM Livefyre 번들을 검색합니다. `com.adobe.cq.social.cq-social-livefyre`
   * 클릭 **정지**

1. ***Livefyre 폴러를 비활성화합니다.***

   * CRXDE Lite에서 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 새 속성 추가 *활성화됨* 유형 *부울*
   * 설정 **활성화된 속성** to **false**

### 2. Oak 색인 정보를 추가하는 방법 {#add-oak-index-info}

AEM Screens은 제품에서 사용하는 쿼리에 대한 색인 정의를 만듭니다.
있을 경우 *쿼리 순회 경고* 에서 `error.log`를 채울 수 있습니다. 을(를) 참조하십시오. [인덱스 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) 자세한 내용

또한 [Oak 설명서](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. v3 매니페스트를 구성하는 데 필요한 사항은 무엇입니까? {#configure-v3}

v3 매니페스트를 활성화하려면 다음을 수행해야 합니다.

* Dispatcher를 업데이트합니다.
자세한 내용은 [매니페스트 버전 v3에 대한 Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 자세한 내용

* 사용자 지정 구성 요소를 업데이트합니다.
자세한 내용은 [사용자 지정 핸들러용 템플릿](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) 자세한 내용

* ContentSync 사용 안 함 `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* SmartSync 사용 `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* 편집 `channel/experience fragment/page components`.

* 로 이동합니다 **오프라인 구성** 탭.

* Enter 키 `clientlibs `매니페스트에 추가해야 하는 정적 파일에 대한 폴더입니다.

### 4. screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 및 screens 코어 번들이 설치되었지만 활성화되지 않은 경우 어떻게 해야 합니까?

AMS 커넥터가 작동하려면 최소 버전의 AEM 6.5 기능 팩 8을 설치해야 합니다. 자세한 내용은 [사용 가능](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) 최소 버전의 기능 팩을 가져오려면 다음을 수행하십시오.