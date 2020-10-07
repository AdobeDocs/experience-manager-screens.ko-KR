---
title: AEM Screens FAQ
seo-title: AEM Screens FAQ
description: AEM Screens 프로젝트와 관련된 FAQ에 대한 답변을 얻으려면 이 페이지를 따르십시오.
seo-description: AEM Screens 프로젝트와 관련된 FAQ에 대한 답변을 얻으려면 이 페이지를 따르십시오.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: fc923553c3813e6fd659df641f2e4363f0907827
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 2%

---


# AEM Screens FAQ {#aem-screens-faqs}

다음 섹션에서는 AEM Screens 프로젝트와 관련하여 자주 묻는 일부 FAQ에 대한 답변을 제공합니다.

## 채널 관리 {#channel-management}

### 1. 온라인 채널과 오프라인 채널의 차이점은 무엇입니까? {#what-is-the-difference-between-an-online-and-an-offline-channel}

***온라인 채널***&#x200B;은 실시간 환경에서 업데이트된 컨텐츠를 표시하는 반면, ***오프라인 채널***&#x200B;은 캐시된 컨텐츠를 보여줍니다.

### 2. 온라인으로 채널을 만들려면 어떻게 해야 합니까? {#how-do-i-make-a-channel-online}

채널을 선택하고 작업 표시줄에서 채널 속성으로 이동합니다. 채널 **탭 아래에서** 개발자 모드(온라인 채널 강제)를 **확인하여** 채널을온라인 상태로 만듭니다.

### 3. 채널 역할 필드의 사용 방법 {#what-is-the-use-of-the-channel-role-field}

채널 역할은 작성자가 일반 경험에 직접 집중할 수 있도록 실행되는 실제 채널의 추상화입니다. 컨텍스트(표시 또는 일정)에서 채널을 고유하게 식별하는 일종의 태그로 생각할 수 있습니다.

### 4. 실제 채널 해상도는 어떻게 이루어집니까? {#how-does-actual-channel-resolution-happen}

정적 *참조의*&#x200B;경우 해상도는 지정된 경로를 따라가면 됩니다.

동적 참조 **&#x200B;의 경우 채널이 디스플레이에 지정되면(스케줄이 아님) 해상도가 발생합니다. 표시 경로는 채널의 컨텍스트가 되고 해상도는 다음과 같이 이루어집니다(최고 우선 순위에서 최저 우선 순위).

1. 디스플레이에는 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이에 참조된 채널 이름과 일치하는 동위 노드가 있습니다.
1. 디스플레이의 상위 위치에 참조된 채널 이름과 일치하는 하위 노드가 있습니다
1. 디스플레이의 상위 위치에 참조된 채널 이름과 일치하는 하위 노드가 있습니다

따라서 위치 폴더에 도달하고 바로 중지할 때까지(따라서 채널 폴더에 있는 채널을 참조할 수 없으며 하위 트리의 채널만 참조).

## 장치 등록 {#device-registration}

### 1. 장치 온보딩 및 등록 요청 등의 끝점을 발견한 경우 많은 수의 장치를 스크립팅하여 이러한 장치를 등록할 수 있습니다. 이를 분기 Wi-Fi로 잠그는 것 외에도 이러한 요청을 보호할 수 있습니까? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

현재 등록은 작성자 인스턴스에서만 가능합니다. 등록 서비스가 인증되지 않았지만 AEM에 보류 중인 장치만 생성되며 실제로 장치를 등록하거나 디스플레이를 할당하지 않습니다.

장치를 등록하려면(AEM에서 장치의 사용자를 만드는 것을 의미) 여전히 AEM에 인증해야 하며 현재 등록 마법사를 수동으로 수행하여 등록을 완료해야 합니다. 이론적으로 악의적인 사용자가 여러 개의 보류 중인 장치를 만들 수 있지만 AEM 로그인 없이는 등록할 수 없습니다.

### 2. HTTP GET 요청을 인증 형식으로 HTTP POST으로 변환하는 방법이 있습니까? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

등록 요청은 POST 요청입니다.

매개 변수로 전달되지 않고 세션에서 장치 ID를 가져오는 것이 좋습니다. 이렇게 하면 서버 로그, 브라우저 캐시 등이 정리됩니다. 현재 보안 문제가 아닙니다. 상태 변경이 있을 때 서버에 상태 변경이 없고 POST이 사용될 때 중간 GET이 사용됩니다.

### 3. 장치 등록 요청을 거절할 수 있는 방법이 있습니까? {#is-there-a-way-to-decline-a-device-registration-request}

등록 요청은 거부할 수 없습니다. 대신 등록 요청은 [Adobe Experience Manager 웹 콘솔에서 구성된 시간 제한 후 만료됩니다](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). 기본적으로 이 값은 하루로 설정되며 메모리 캐시에 저장됩니다.

## 장치 모니터링 및 상태 보고서 {#device-monitoring-and-health-reports}

### 1. AEM Screens 플레이어에 빈 화면이 표시되는 경우 어떻게 해결할 수 있습니까? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

빈 화면 문제를 해결하려면 다음 가능성을 확인하십시오.

* AEM에서 오프라인 콘텐츠를 푸시할 수 없습니다.
* 채널에 콘텐츠가 없습니다.
* 현재 시간에 표시할 자산이 예약되어 있지 않습니다.

### 2. AEM Screens 플레이어를 등록할 수 없고 해당 상태가 실패로 표시된 경우 어떻게 해야 합니까? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Apache Sling 레퍼러 필터 [비어 있음 허용]을 활성화해야 합니다. 이는 AEM Screens 플레이어와 AEM Screens 서버 사이의 제어 프로토콜을 최적의 방식으로 운영하기 위해 필요합니다.

1. **Adobe Experience Manager 웹 콘솔 구성으로 이동**
1. allow.empty **옵션을** 선택합니다.
1. **저장**&#x200B;을 클릭합니다.

### 3. AEM Screens 플레이어를 등록하는 동안 장치에 오류가 표시되고 콘솔 로그에 ENAME_NOT_FOUND 오류가 표시되는 경우 문제를 해결하는 방법? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

플레이어에서 AEM Screens 서버 DNS를 찾을 수 없는 경우 이 문제가 발생할 수 있습니다. IP 주소를 사용하여 연결할 수 있습니다. 서버의 IP를 얻으려면 다음을 사용하십시오. *arp &lt;server_dns_name>*.

### 4. AMS는 모든 장치에서 Android Watchdog를 구현할 것을 권장합니까? Watchdova(Cordova) 플러그인이 APK의 일부로 포함되어 있습니까? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

순수 Android API를 사용하는 크로스 플랫폼 Android 감시기는 이미 apk의 일부입니다. 추가 소프트웨어는 필요하지 않지만 사용하는 장치에 따라 전체 전원 주기에 대한 시스템 권한을 얻기 위해 apk를 포기해야 할 수도 있습니다(Powermanager api). 제조업체 키를 사용하여 그만두지 않으면 애플리케이션을 종료하고 다시 시작하지만 전원 사이클은 종료되지 않습니다.

Android Player 구현 방법에 대한 자세한 내용은 [**Android Player 구현을 참조하십시오**](implementing-android-player.md).

### 5. Adobe/AMS가 각 장치를 모니터링하기 위해 추천하는 타사 원격 모니터링 및 경고 도구(소프트웨어)는 무엇입니까?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

모니터링 및 경고에서 원하는 내용에 따라, 새로운 기능 AEM Screens 알림 서비스는 장치가 잠시 동안 핑되지 않았으면 사용자에게 알립니다. 타사 도구는 운영 체제(OS), 기능 및 고객의 특정 요구 사항에 따라 다릅니다.

장치 활동을 모니터링할 수 있는 위치에 대한 자세한 내용은 [**AEM Screens 알림 서비스를 참조하십시오**](screens-notifications-service.md).

## AEM 스크린 플레이어 {#aem-screens-player}

### 1. Chrome 브라우저 플러그인으로 ChromeOS 플레이어를 설치하는 방법? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS 플레이어는 실제 크롬 플레이어 장치가 없어도 개발자 모드에서 Chrome Browser 플러그인으로 설치할 수 있습니다. 설치하려면 아래 단계를 수행하십시오.

1. 최신 Chrome Player를 다운로드하려면 [여기를](https://download.macromedia.com/screens/) 클릭하십시오.
1. 압축을 풀고 디스크에 저장합니다.
1. 크롬 브라우저를 열고 메뉴에서 **확장** 기능을 선택하거나 chrome://extensions으로 직접 ***이동합니다***.
1. 오른쪽 상단 모서리에서 **개발자 모드를** 전환합니다.
1. 왼쪽 위 **모서리에서 [압축을** 푼 파일 로드]를 클릭하고 압축을 푼 Chrome Player를 로드합니다.
1. 확장 프로그램 목록에 **있는 경우 AEM Screens Chrome Player** 플러그인을 확인하십시오.
1. 새 탭을 열고 왼쪽 상단 모서리에서 **앱** 아이콘을 클릭하거나 chrome://apps으로 직접 ***이동합니다***.
1. Chrome Player를 **시작하려면 AEM Screens** 플러그인을 클릭합니다. 기본적으로 플레이어가 전체 화면 모드로 실행됩니다. 전체 화면 모드를 **종료하려면 esc** 키를 누릅니다.

### 2. Screens 플레이어가 사용자 지정 오류 처리기로 게시 인스턴스를 통해 인증할 수 없는 경우 문제를 어떻게 해결합니까? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens 플레이어가 시작되면 플레이어에서 404 오류가 발생하는 경우 /content/screens/svc.ping ***.json***&#x200B;을 요청합니다. 플레이어는 게시 인스턴스에 대해 인증하도록 인증 요청을 시작합니다. 게시 인스턴스에 사용자 지정 오류 처리기가 있는 경우 /content/screens/svc.ping.json에서 익명 사용자의 404 상태 코드를 ***반환해야 합니다***.

### 3. Android Player에서 장치 화면을 설정하는 방법 {#how-to-set-the-device-screen-stay-on-in-an-android-player}

아래 단계에 따라 모든 Android 플레이어에서 깨어 있으십시오.

1. Android 플레이어 설정 —> **정보**
1. 빌드 번호를 7번 눌러 **설정에서 개발자 옵션** 활성화 ****
1. 개발자 **옵션으로 이동**
1. 깨어 **있도록 설정**

### 4. Windows 플레이어에 대한 창 모드를 활성화하는 방법?{#enable-player}

Windows 플레이어에는 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### 5. Screens 플레이어에서 로그인 요청을 지속적으로 전송하는 경우 어떻게 해결합니까?{#requests-login}

아래 절차에 따라 계속해서 요청을 보내는 AEM Screens 플레이어의 문제를 `/content/screens/svc.json` 해결하십시오. `/libs/granite/core/content/login.validate/j_security_check`

1. AEM Screens 플레이어가 시작되면 이 응답으로 플레이어가 404 상태 코드를 받게 되면 플레이어는 게시 인스턴스에 대해 인증 요청을 시작 `/content/screens/svc.json``/libs/granite/core/content/login.validate/j_security_check` 합니다. 게시 인스턴스에 사용자 지정 오류 처리기가 있는 경우 `/content/screens/svc.json` 또는 에서 익명 사용자의 404 상태 코드를 반환해야 합니다 `/content/screens/svc.ping.json`.

1. 디스패처 구성에서 섹션에서 이러한 요청을 허용하는지 `/filters` 확인합니다. 자세한 [내용은 스크린 필터](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 구성을 참조하십시오.

1. 디스패처 다시 작성 규칙이 스크린 경로를 다른 경로로 재작성하는지 확인합니다.

1. 작성자 `/etc/map` 또는 *게시* 인스턴스에 대한 규칙이 있는지 *확인하고 화면 경로가 다른 경로로* `sling:match` 내부적으로 리디렉션되었는지 확인합니다. /`system/console/jcrresolver` 의 정확한 url을 확인하면 *게시* 인스턴스가 이러한 url을 다른 경로로 재작성하고 있는지 확인할 수 있습니다.

1. 내부 다시 쓰기를 발생시키는 Apache Sling Resource Resolver Factory 구성이 있는지 확인하십시오.

## 일반 문제 해결 팁 {#general-troubleshooting-tips}

### 1. A/P 화면 오류를 방지하기 위해 Livefyre를 비활성화하는 방법? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

로그 오류를 방지하기 위해 Livefyre를 비활성화하려면:

1. ***Livefyre 번들 비활성화:***

   * 다음으로 이동 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * AEM Livefyre 번들 검색: `com.adobe.cq.social.cq-social-livefyre`
   * 중지 **를 클릭합니다**

1. ***Livefyre 폴러 비활성화:***

   * CRXDE Lite에서 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 새 속성 *활성화* 유형 *부울 추가*
   * 활성화된 **속성을** **false로 설정**

