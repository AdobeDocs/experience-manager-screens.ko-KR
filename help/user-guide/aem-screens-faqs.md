---
title: AEM Screens FAQ
seo-title: AEM Screens FAQ
description: AEM Screens 프로젝트와 관련된 FAQ에 대한 답변을 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Screens 프로젝트와 관련된 FAQ에 대한 답변을 얻으려면 이 페이지를 따르십시오.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 3c78dd2f2f5cff421917eb5d657d8fd6fb2e3229
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 1%

---


# AEM Screens FAQ {#aem-screens-faqs}

다음 섹션에서는 AEM Screens 프로젝트와 관련하여 자주 묻는 FAQ 중 일부에 대한 답변을 제공합니다.

## 빈 화면 문제 {#blank-screen}

>[!NOTE]
>문제가 발생하기 전에 기본 지원 또는 고객 측 지원에 의해 시도해야 하는 필수 확인 사항입니다.

### 1. 블랙 스크린 또는 재생되지 않는 컨텐츠에 직면하는 모든 고객에 대해 최초 지원 문제 해결 단계는 무엇입니까?{#troubleshooting-blank-screen}

* 채널 미리 보기가 작동하는지 확인합니다.
* 표시 미리 보기가 작동하는지 확인
* 동일한 디스플레이에 플레이어를 브라우저 익스텐션으로 등록하고 이 기능이 작동하는지 확인하십시오.
* 시스템에서 실행 중인 플레이어에서 `http://localhost:24502`으로 이동합니다. 모든 콘텐츠가 올바르게 다운로드되었는지 확인합니다.
* 적절한 변환이 만들어지고 올바른 변환이 재생되는지 자산을 확인합니다.
* 예약된 컨텐츠가 있는지, 그리고 시간이 올바른지 확인하십시오. 플레이어에서 설정한 시간이 올바른지 확인합니다.
* Inspect 플레이어 콘솔 로그가 기록되고 오류가 있는지 확인합니다. 마우스 오른쪽 단추를 클릭하고 검사하여 콘솔 로그를 확인합니다. windows 플레이어를 사용하는 경우 `CTRL + ALT +I`을 눌러 개발 콘솔을 표시하여 로그를 봅니다.

### 2. 기본 채널 또는 일정을 만들어 AEM Screens의 회색 화면 문제를 해결하는 방법?

필드의 빈 화면이나 회색 화면을 피하려면 우선 순위가 가장 낮은 모든 디스플레이에 지정된 기본 전역 채널 또는 일정을 만드십시오. 네트워크, 플레이어, 서버 또는 복제로 인해 컨텐츠 업데이트(네트워크, 플레이어, 서버 또는 복제)에 문제가 있는 경우 플레이어는 이 컨텐츠를 이미 디스크에 캐시하므로 제대로 재생되고 회색 스크린은 표시되지 않습니다.

채널 또는 일정과 같은 기타 모든 컨텐츠의 우선 순위가 1보다 높으므로 다른 컨텐츠는 우선 순위를 차지하며 글로벌 채널 또는 스케줄 컨텐츠(우선 순위 1)는 대안 옵션으로만 재생됩니다.

## 채널 관리 {#channel-management}

### 1. 온라인 채널과 오프라인 채널의 차이점은 무엇입니까?{#what-is-the-difference-between-an-online-and-an-offline-channel}

***온라인 채널***&#x200B;은 실시간 환경에서 업데이트된 컨텐츠를 표시하는 반면, ***오프라인 채널***&#x200B;은 캐시된 컨텐츠를 보여줍니다.

### 2. 온라인으로 채널을 만들려면 어떻게 해야 합니까?{#how-do-i-make-a-channel-online}

채널을 선택하고 작업 표시줄에서 채널 속성으로 이동합니다. 채널을 온라인 상태로 만들려면 **채널** 탭에서 **개발자 모드(온라인 채널을 강제 설정)**&#x200B;를 선택합니다.

### 3. 채널 역할 필드의 사용 방법{#what-is-the-use-of-the-channel-role-field}

채널 역할은 작성자가 일반적인 경험에 직접 집중할 수 있도록 실행되는 실제 채널의 추상화입니다. 컨텍스트(표시 또는 일정)에서 채널을 고유하게 식별하는 일종의 태그로 생각할 수 있습니다.

### 4. 실제 채널 해상도는 어떻게 됩니까?{#how-does-actual-channel-resolution-happen}

*정적 참조*&#x200B;의 경우 해상도는 지정된 경로를 따릅니다.

*동적 참조*&#x200B;의 경우 채널이 디스플레이에 지정되면(일정이 아님) 해상도가 발생합니다. 표시 경로는 채널의 컨텍스트가 되고 해상도는 다음과 같이 발생합니다(가장 높은 우선 순위에서 가장 낮은 우선 순위).

1. 디스플레이에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다.
1. 디스플레이에 참조된 채널 이름과 일치하는 동위 노드가 있습니다.
1. 디스플레이의 상위 위치에 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이의 상위 위치에 참조된 채널 이름과 일치하는 하위 노드가 있습니다

따라서 위치 폴더에 도달하고 그 자리에서 바로 중지할 때까지(따라서 위치 하위 트리의 채널만 해당 채널 폴더의 채널을 참조할 수 없음).

## 장치 등록 {#device-registration}

### 1. 장치 온보딩 및 등록 요청과 같은 끝점을 발견하는 경우, 많은 수의 장치를 스크립팅하고 이러한 장치를 등록할 수 있습니다. 이를 분기 Wi-Fi에 잠그는 것 외에도 이러한 요청을 안전하게 보호할 수 있습니까?{#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

현재 등록은 작성자 인스턴스에서만 가능합니다. 등록 서비스가 인증되지 않았지만 AEM에 보류 중인 장치만 만들고 실제로 장치를 등록하거나 디스플레이를 할당하지 않습니다.

장치를 등록하려면(AEM에서 장치에 대한 사용자를 만드는 것을 의미) AEM에 인증해야 하며 현재 수동으로 등록 마법사를 따라 등록을 완료해야 합니다. 이론적으로 악의적인 사용자가 여러 개의 보류 중인 장치를 만들 수 있지만 AEM 로그인 없이는 등록할 수 없습니다.

### 2. HTTP GET 요청을 인증 형식으로 HTTP POST으로 변환할 수 있는 방법이 있습니까?{#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

등록 요청은 POST 요청입니다.

매개 변수로 전달되지 않고 세션에서 장치 ID를 가져오는 것이 좋습니다. 이렇게 하면 서버 로그, 브라우저 캐시 등이 정리됩니다. 현재 보안 문제가 아닙니다. 상태 변경이 있을 때 서버에 상태 변경이 없고 POST이 사용될 때 중간 GET이 사용됩니다.

### 3. 디바이스 등록 요청을 거절할 수 있는 방법이 있습니까?{#is-there-a-way-to-decline-a-device-registration-request}

등록 요청은 거절할 수 없습니다. 대신 등록 요청은 [Adobe Experience Manager 웹 콘솔](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)에 구성된 시간 초과 후 만료됩니다. 기본적으로 이 값은 하루로 설정되며 메모리 캐시에 저장됩니다.

## 장치 모니터링 및 상태 보고서 {#device-monitoring-and-health-reports}

### 1. AEM Screens 플레이어에 빈 화면이 표시되는 경우 어떻게 문제를 해결합니까?{#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

빈 화면 문제를 해결하려면 다음 옵션을 확인하십시오.

* AEM에서 오프라인 콘텐츠를 푸시할 수 없습니다.
* 채널에 콘텐츠가 없습니다.
* 현재 시간에 표시하도록 예약된 에셋 없음

### 2. AEM Screens 플레이어를 등록할 수 없고 해당 상태가 오류로 표시된 경우 어떻게 해야 합니까?{#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Apache Sling 레퍼러 필터가 [비어 있음 허용]을 활성화해야 합니다. AEM Screens Player와 AEM Screens 서버 간의 제어 프로토콜을 최적화하기 위해 필요합니다.

1. **Adobe Experience Manager 웹 콘솔 구성**&#x200B;으로 이동합니다.
1. **allow.empty** 옵션을 선택합니다.
1. **저장**&#x200B;을 클릭합니다.

### 3. AEM Screens 플레이어를 등록하는 동안 장치에 오류가 표시되고 콘솔 로그에 ENAME_NOT_FOUND 오류가 표시되는 경우 문제를 해결하는 방법?{#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

플레이어에서 AEM Screens 서버 DNS를 찾을 수 없는 경우 이 문제가 발생할 수 있습니다. IP 주소를 사용하여 연결할 수 있습니다. 서버의 IP를 얻으려면 다음을 사용합니다.*arp &lt;server_dns_name>*.

### 4. AMS는 모든 장치에서 Android Watchdog를 구현할 것을 권장합니까? Watchdova(Cordova) 플러그인이 APK의 일부로 포함되어 있습니까?{#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

순수 Android API를 사용하는 크로스 플랫폼 Android 감시기는 이미 앱의 일부입니다. 추가 소프트웨어는 필요하지 않지만 사용하는 장치에 따라 전체 전원 주기에 대한 시스템 권한을 얻기 위해 앱을 사임해야 할 수 있습니다(Powermanager api). 제조업체 키를 사용하여 작업을 중단하지 않으면 애플리케이션을 종료하고 다시 시작하지만 전원 사이클은 하지 않습니다.

Android Player 구현 방법에 대한 자세한 내용은 [**Android Player 구현**](implementing-android-player.md)&#x200B;을 참조하십시오.

### 5. Adobe/AMS가 각 장치를 모니터링하기 위해 추천하는 제3자 원격 모니터링 및 경고 도구(소프트웨어)는 무엇입니까? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

모니터링 및 경고에서 원하는 내용에 따라, 새로운 기능 AEM Screens 알림 서비스는 장치가 잠시 동안 핑되지 않았으면 사용자에게 알립니다. 제3자 도구는 운영 체제(OS), 기능 및 고객의 특정 요구 사항에 따라 다릅니다.

장치 활동을 모니터링할 수 있는 위치에 대한 자세한 내용은 [**AEM Screens 알림 서비스**](screens-notifications-service.md)&#x200B;를 참조하십시오.

## AEM 스크린 플레이어 {#aem-screens-player}

### 1. Chrome 브라우저 플러그인으로 ChromeOS 플레이어를 설치하는 방법?{#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS 플레이어는 실제 크롬 플레이어 장치가 없어도 개발자 모드에서 Chrome Browser 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 수행하십시오.

1. 최신 Chrome Player를 다운로드하려면 [여기](https://download.macromedia.com/screens/)를 클릭합니다.
1. 압축을 풀고 디스크에 저장합니다.
1. Chrome 브라우저를 열고 메뉴에서 **확장**&#x200B;을 선택하거나 ***chrome://extensions***&#x200B;으로 직접 이동합니다.
1. 오른쪽 위 모서리에서 **개발자 모드**&#x200B;로 전환합니다.
1. 왼쪽 위 모서리에서 **Load Unpack**&#x200B;을 클릭하고 압축을 푼 Chrome Player를 로드합니다.
1. 확장 목록 목록에 있는 경우 **AEM Screens Chrome Player** 플러그인을 확인하십시오.
1. 새 탭을 열고 왼쪽 위 모서리의 **Apps** 아이콘을 클릭하거나 ***chrome://apps***&#x200B;로 직접 이동합니다.
1. **AEM Screens** 플러그인을 클릭하여 Chrome Player를 실행합니다. 기본적으로 플레이어가 전체 화면 모드로 실행됩니다. 전체 화면 모드를 종료하려면 **esc**&#x200B;을 누릅니다.

### 2. Screens 플레이어가 사용자 지정 오류 처리기로 게시 인스턴스를 통해 인증할 수 없는 경우 문제를 어떻게 해결합니까?{#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens 플레이어가 시작되면 플레이어가 404 오류가 발생하는 경우 ***/content/screens/svc.ping.json***&#x200B;에 요청을 합니다. 플레이어는 게시 인스턴스에 대해 인증하도록 인증 요청을 시작합니다. 게시 인스턴스에 사용자 지정 오류 처리기가 있는 경우 ***/content/screens/svc.ping.json***&#x200B;에서 익명 사용자의 404 상태 코드를 반환해야 합니다.

### 3. Android Player에서 장치 화면을 설정하는 방법은 무엇입니까?{#how-to-set-the-device-screen-stay-on-in-an-android-player}

아래의 단계에 따라 모든 Android 플레이어에서 깨어 있으십시오.

1. Android 플레이어 설정 —> **정보**
1. 빌드 번호를 7번 눌러 **설정**&#x200B;에서 **개발자 옵션**&#x200B;을 활성화합니다.
1. **개발자 옵션**&#x200B;으로 이동합니다.
1. **깨어 있으십시오**

### 4. Windows 플레이어에 대해 윈도우 모드를 활성화하는 방법?{#enable-player}

Windows Player에는 윈도우 모드가 없습니다. 항상 전체 화면 모드입니다.

### 5. AEM Screens 플레이어에서 로그인 요청을 계속 보내는 경우 어떻게 문제를 해결합니까?{#requests-login}

아래 절차에 따라 `/content/screens/svc.json` 및 `/libs/granite/core/content/login.validate/j_security_check`에 요청을 지속적으로 전송하는 AEM Screens 플레이어의 문제를 해결하십시오.

1. AEM Screens 플레이어가 시작되면 `/content/screens/svc.json`에 요청합니다. 플레이어가 응답에서 404 상태 코드를 받으면 *publish* 인스턴스에 대해 `/libs/granite/core/content/login.validate/j_security_check`을 사용하여 인증 요청을 시작합니다. *publish* 인스턴스에 사용자 지정 오류 처리기가 있는 경우 `/content/screens/svc.json` 또는 `/content/screens/svc.ping.json`에서 익명 사용자의 404 상태 코드를 반환해야 합니다.

1. 디스패처 구성에서 `/filters`에서 이러한 요청을 허용하는지 확인합니다.

   자세한 내용은 [스크린 필터 구성](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters)을 참조하십시오.

1. 디스패처 다시 작성 규칙이 스크린 경로를 다른 경로로 재작성하는지 확인합니다.

1. *author* 또는 *publish* 인스턴스와 화면 경로가 `sling:match`에 일치하고 내부적으로 다른 경로로 리디렉션되었는지 확인합니다. `/etc/map` `/system/console/jcrresolver`의 정확한 URL을 확인하면 *publish* 인스턴스가 이러한 URL을 다른 경로로 재작성하고 있는지 확인할 수 있습니다.

1. Apache Sling 리소스 확인자 팩토리 구성 때문에 내부 다시 쓰기가 발생하는지 확인하십시오.

## 일반 문제 해결 팁 {#general-troubleshooting-tips}

### 1. A/P 스크린 오류를 방지하기 위해 Livefyre를 비활성화하는 방법?{#how-to-disable-livefyre-to-avoid-a-p-screens-error}

로그 오류를 방지하기 위해 Livefyre를 비활성화하려면:

1. ***Livefyre 번들 비활성화:***

   * 다음으로 이동 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * AEM Livefyre 번들 검색:`com.adobe.cq.social.cq-social-livefyre`
   * **중지**&#x200B;를 클릭합니다.

1. ***Livefyre 폴러 비활성화:***

   * CRXDE Lite에서 `/etc/importers/polling/livefyre-poller/jcr:content`으로 이동합니다.
   * 새 속성 *enabled* 유형 *Boolean* 추가
   * **enabled 속성**&#x200B;을 **false**&#x200B;로 설정합니다.

### 2. Oak 색인 정보를 추가하는 방법?{#add-oak-index-info}

AEM Screens은 제품이 사용하는 쿼리에 대한 색인 정의를 만듭니다.
`error.log`에 *쿼리 순회 WARN*&#x200B;이 있는 경우 쿼리에 대한 사용자 지정 인덱스를 만듭니다. 자세한 내용은 [인덱스 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes)을 참조하십시오.

[Oak 설명서](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에 대한 추가 리소스를 참조할 수도 있습니다.


