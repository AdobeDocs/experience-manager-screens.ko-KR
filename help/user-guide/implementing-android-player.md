---
title: Android Player 구현
seo-title: Implementation of Android Player
description: 충돌에서 플레이어를 복구하는 솔루션인 Android Watchdog를 구현하려면 이 페이지를 따르십시오.
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Android Player 구현 {#implementing-android-player}

이 섹션에서는 Android 플레이어 구성에 대해 설명합니다. 구성 파일 및 사용 가능한 옵션에 대한 정보와 개발 및 테스트에 사용할 설정에 대한 권장 사항을 제공합니다.

또한, **감시장치** 은(는) 충돌 시 플레이어를 복구하는 솔루션입니다. 애플리케이션은 자신을 감시 서비스에 등록한 다음, 주기적으로 해당 서비스가 살아 있는 서비스에 메시지를 보내야 합니다. 감시장치 서비스가 지정된 시간 내에 Keep-Alive 메시지를 수신하지 못하는 경우, 서비스는 정리 복구를 위해 디바이스를 재부팅하거나(충분한 권한이 있는 경우) 응용 프로그램을 다시 시작하려고 시도합니다.

## Android Player 설치 {#installing-android-player}

AEM Screens용 Android Player를 구현하려면 AEM Screens용 Android Player를 설치하십시오.

다음 방문 [**AEM 6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지.

### AEM Screens 6.5.5 서비스 팩용 환경 설정 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Android 플레이어에 대한 환경을 설정해야 합니다.

설정 **로그인 토큰 쿠키에 대한 SameSite 속성** 변환 전: **Lax** to **없음** 변환 전: **Adobe Experience Manager 웹 콘솔 구성** 모든 AEM 작성자 및 게시 인스턴스에서 볼 수 있습니다.

아래 단계를 따르십시오.

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** 사용 `http://localhost:4502/system/console/configMgr`.

1. 검색 대상 *Adobe Granite 토큰 인증 핸들러*.

1. 설정 **로그인 토큰 쿠키에 대한 SameSite 속성** 변환 전: **Lax** to **없음**.
   ![이미지](/help/user-guide/assets/granite-updates.png)

1. **저장**&#x200B;을 클릭합니다.


### Ad-Hoc 메서드 {#ad-hoc-method}

Ad-Hoc 메서드를 사용하면 최신 Android Player(*.exe*). 방문 [**AEM 6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지.

애플리케이션을 다운로드한 후에는 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리에서 을(를) 길게 눌러 관리 패널을 엽니다.
1. 다음으로 이동 **구성** 왼쪽 작업 메뉴에서 연결할 AEM 인스턴스의 위치(주소)를 입력하고 를 클릭합니다 **저장**.

1. 로 이동합니다 **장치** **등록** 왼쪽 작업 메뉴에서 링크를 클릭하여 장치 등록 프로세스의 상태를 확인합니다.

>[!NOTE]
>
>만약 **주/도** is **등록**&#x200B;를 클릭하면 **장치 ID** 필드가 채워집니다.
>
>만약 **주/도** is **등록되지 않음**&#x200B;를 사용하여 다음을 수행할 수 있습니다. **토큰** 를 클릭하여 장치를 등록합니다.

## Android Watchdog 구현 {#implementing-android-watchdog}

Android의 아키텍처로 인해 장치를 재부팅하려면 애플리케이션에 시스템 권한이 있어야 합니다. 이렇게 하려면 제조업체의 서명 키를 사용하여 apk에 서명해야 합니다. 그렇지 않으면 감시가 플레이어 애플리케이션을 다시 시작하고 장치를 재부팅하지 않습니다.

### 제조업체 키를 사용한 Android 앱의 서명 {#signage-of-android-apks-using-manufacturer-keys}

Android의 권한 있는 API 일부(예: *PowerManager* 또는 *HDMIControlServices*, 제조업체의 키를 사용하여 android api에 서명해야 합니다.

>[!CAUTION]
>
>전제 조건:
>
>다음 단계를 수행하려면 먼저 Android SDK가 설치되어 있어야 합니다.

아래 절차에 따라 제조업체의 키를 사용하여 Android 앱에 서명하십시오.

1. Google Play 또는 [AEM Screens Player 다운로드](https://download.macromedia.com/screens/) 페이지
1. 제조업체에서 플랫폼 키를 가져와 *pk8* 그리고 *pem* 파일

1. find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;를 사용하여 android sdk에서 apksigner 도구를 찾습니다.
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. android sdk에서 zip 정렬 도구의 경로를 찾습니다
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalshed.apk
1. 설치 ***aemscreensalested.apk*** 장치에 adb 설치 사용

## Android Watchdog Services 이해 {#android-watchdog-services}

Android 간 감시 서비스는 를 사용하여 cordova 플러그인으로 구현됩니다 *AlarmManager*.

다음 다이어그램은 감시 서비스 구현입니다.

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 초기화** Cordova 플러그인의 초기화 시 시스템 권한이 있는지 확인하여 Reboot 권한이 있는지 확인합니다. 이 두 기준이 충족되면 재부팅에 대한 보류 중인 의도가 만들어지고, 그렇지 않으면 애플리케이션을 다시 시작하려는 보류 중인 의도(Launch 활동에 따라)가 생성됩니다.

**2. 타이머 유지** 생존 유지 타이머는 15초마다 이벤트를 트리거하는 데 사용됩니다. 이 경우 기존의 보류 중인 의도를 취소하고(앱을 다시 부팅하거나 다시 시작하기) 향후 60초 동안 새 보류 중인 의도를 등록해야 합니다(즉 다시 부팅을 연기함).

>[!NOTE]
>
>Android에서 *AlarmManager* 는 를 등록하는 데 사용됩니다. *pendingIntents* 앱이 충돌하고 API 19(Kitkat)에서 해당 경고 배달이 정확하지 않은 경우에도 실행할 수 있습니다. 타이머의 간격과 간격 사이의 간격을 유지합니다. *AlarmManager의* *pendingIntent의* 경보

**3. 애플리케이션 충돌** 충돌이 발생한 경우 AlarmManager와 함께 등록된 보류 중인 재부팅용 Intent가 더 이상 재설정되지 않으므로 Cordova 플러그인의 초기화 시 사용 가능한 권한에 따라 앱의 다시 부팅 또는 다시 시작을 실행합니다.

## Android Player 벌크 프로비저닝 {#bulk-provision-android-player}

Android 플레이어를 일괄적으로 롤아웃할 때, Admin UI에서 수동으로 입력하지 않고 AEM 인스턴스를 가리키도록 플레이어를 프로비저닝하고 다른 속성을 구성해야 합니다.

>[!NOTE]
>이 기능은 Android 플레이어 42.0.372에서 사용할 수 있습니다.

Android 플레이어에서 벌크 프로비저닝을 허용하려면 아래 단계를 따르십시오.

1. 이름이 인 구성 JSON 파일 만들기 `player-config.default.json`.
다음을 참조하십시오 [JSON 정책 예](#example-json) 또한, [정책 속성](#policy-attributes).

1. MDM 또는 ADB 또는 Android Studio 파일 탐색기를 사용하여 이 정책 JSON 파일을 *sdcard* Android 장치의 폴더.

1. 파일이 배포되면 MDM을 사용하여 플레이어 응용 프로그램을 설치합니다.

1. 플레이어 애플리케이션이 실행되면 이 구성 파일을 읽고 등록하여 제어할 수 있는 해당 AEM 서버를 가리킵니다.

   >[!NOTE]
   >이 파일은 *읽기 전용* 애플리케이션이 처음 실행되면 후속 구성에 사용할 수 없습니다. 구성 파일이 삭제되기 전에 플레이어가 시작된 경우 해당 애플리케이션을 제거하고 장치에 다시 설치하면 됩니다.

### 정책 속성 {#policy-attributes}

다음 표에는 참조에 대한 정책 JSON 예제 정책이 있는 정책 속성이 요약되어 있습니다.

| **정책 이름** | **목적** |
|---|---|
| *서버* | Adobe Experience Manager 서버의 URL입니다. |
| *해상도* | 장치의 해상도. |
| *rebootSchedule* | 재부팅할 일정은 모든 플랫폼에 적용됩니다. |
| *enableAdminUI* | 사이트에서 장치를 구성하려면 관리자 UI를 활성화합니다. 을 로 설정합니다. *false* 완전히 구성 및 프로덕션에 포함될 수 있습니다. |
| *enableOSD* | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 을(를) (으)로 설정하는 것이 좋습니다. *false* 완전히 구성 및 프로덕션에 포함될 수 있습니다. |
| *enableActivityUI* | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시하도록 활성화합니다. 문제 해결을 활성화하고 완전히 구성하고 프로덕션에서 비활성화합니다. |
| *enableNativeVideo* | 비디오 재생에 기본 하드웨어 가속을 사용할 수 있도록 합니다(Android만 해당). |

### JSON 정책 예 {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>모든 Android 장치에는 *sdcard* 실제 폴더 *sdcard* 삽입되었거나 삽입되지 않았습니다. 배포될 때 이 파일은 다운로드 폴더와 동일한 수준에 있게 됩니다. Samsung Knox와 같은 일부 MDM들은 이것을 언급할 수도 있습니다 *sdcard* 폴더 위치 *내부 스토리지*.

## Enterprise Mobility Management를 사용하여 Android Player의 벌크 프로비저닝 {#bulk-provisioning}

Android 플레이어를 일괄적으로 배포할 때 모든 단일 플레이어를 AEM에 수동으로 등록하는 것은 번거롭습니다. VMWare Airwatch, MobileIron 또는 Samsung Knox와 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 원격으로 배포를 프로비저닝하고 관리하는 것이 좋습니다. AEM Screens Android 플레이어는 원격 프로비저닝을 허용하도록 업계 표준 EMM AppConfig 를 지원합니다.

## Android 플레이어 이름 지정 {#name-android}

Android 플레이어에 사용자에게 친숙한 장치 이름을 할당하여 할당된 장치 이름을 Adobe Experience Manager(AEM)에 전송할 수 있습니다. 이 기능을 사용하면 Android 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 컨텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 플레이어 이름을 더 이상 변경할 수 없습니다.

아래 절차에 따라 Android 플레이어에서 이름을 구성하십시오.

1. 다음으로 이동 **설정** —> **장치 정보**
1. 장치 이름을 편집하고 설정하여 Android 플레이어의 이름을 지정합니다

### Enterprise Mobility Management를 사용하여 Android Player의 벌크 프로비저닝 구현 {#implementation}

Android Player에서 벌크 프로비저닝을 허용하려면 아래 단계를 따르십시오.

1. Android 장치가 Google Play 서비스를 지원하는지 확인합니다.
1. AppConfig를 지원하는 자주 사용하는 EMM 솔루션으로 Android 플레이어 장치를 등록합니다.
1. EMM 콘솔에 로그인하고 Google Play에서 AEM Screens Player 애플리케이션을 가져옵니다.
1. 관리 구성 또는 관련 옵션을 선택합니다.
1. 이제 서버 및 벌크 등록 코드와 같이 구성할 수 있는 플레이어 옵션 목록이 표시됩니다.
1. 이러한 매개 변수를 구성하고 정책을 저장하고 장치에 배포합니다.

   >[!NOTE]
   >장치는 구성과 함께 응용 프로그램을 수신하고 선택한 구성으로 올바른 AEM 서버를 가리켜야 합니다. 벌크 등록 코드를 구성하고 AEM에 구성된 것과 동일하게 유지하는 경우 플레이어가 자동으로 등록할 수 있어야 합니다. 기본 디스플레이를 구성한 경우 기본 콘텐츠를 다운로드하고 표시할 수도 있습니다(나중에 필요에 따라 변경할 수 있음).

또한 AppConfig 지원에 대해 EMM 공급업체에 문의해야 합니다. 가장 인기 있는 것은 다음과 같습니다. [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [모바일 아이언](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 및 [삼성 녹스](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 이 업계 표준을 지원하는 제품도 있습니다.

### 화면 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대한 자세한 내용은 다음을 참조하십시오. [화면 원격 제어](implementing-remote-control.md)
