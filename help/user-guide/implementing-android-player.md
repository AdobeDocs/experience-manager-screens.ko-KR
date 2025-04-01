---
title: Android 구현&트레이드; 플레이어
description: Android&trade; Watchdog, Android&trade; 플레이어의 충돌을 복구할 수 있는 솔루션 구현에 대해 알아봅니다.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 7410e2d8fd7fe1e8b795a35f3a76df4ea882117e
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 0%

---

# Android™ Player 구현 {#implementing-android-player}

>[!CAUTION]
>Android 기반 AEM Screens Player는 공식적으로 더 이상 사용되지 않습니다. 사용자는 AEM Screens에서 지원하는 다른 운영 체제로 마이그레이션하는 것이 좋습니다.

이 섹션에서는 Android™ 플레이어 구성에 대해 설명합니다. 구성 파일 및 사용 가능한 옵션에 대한 정보와 개발 및 테스트에 사용할 설정에 대한 권장 사항을 제공합니다.

또한 **Watchdog**&#x200B;은(는) 충돌에서 플레이어를 복구하는 솔루션입니다. 응용 프로그램은 Watchdog 서비스에 등록하고 주기적으로 Watchdog 서비스가 사용 중이라는 메시지를 전송해야 합니다. 워치독 서비스가 지정된 시간 내에 keep-alive 메시지를 수신하지 못한 경우 서비스는 디바이스를 재부팅하려고 시도합니다. 완전한 복구를 위해(충분한 권한이 있는 경우) 또는 애플리케이션을 다시 시작합니다.

## Android™ Player 설치 {#installing-android-player}

AEM Screens용 Android™ Player를 구현하려면 AEM Screens용 Android™ Player를 설치합니다.

[**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

### AEM Screens 6.5.5 서비스 팩용 환경 설정 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Android™ 플레이어에 대한 환경을 설정합니다.

모든 AEM 작성자 및 게시 인스턴스에서 로그인 토큰 쿠키에 대한 **SameSite 특성**&#x200B;을(를) **Lax**&#x200B;에서 **없음**(으)로 **Adobe Experience Manager 웹 콘솔 구성**&#x200B;에서 설정합니다.

아래 단계를 따르십시오.

1. `http://localhost:4502/system/console/configMgr`을(를) 사용하여 **Adobe Experience Manager 웹 콘솔 구성**(으)로 이동합니다.

1. *Adobe Granite 토큰 인증 처리기*&#x200B;를 검색합니다.

1. 로그인 토큰 쿠키에 대한 **SameSite 특성**&#x200B;을(를) **Lax**&#x200B;에서 **없음**(으)로 설정합니다.
   ![이미지](/help/user-guide/assets/granite-updates.png)

1. **저장**&#x200B;을 클릭합니다.


### 임시 메서드 {#ad-hoc-method}

Ad-Hoc 메서드를 사용하면 최신 Android™ 플레이어(*.exe*)를 설치할 수 있습니다. [**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

응용 프로그램을 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 작업 메뉴에서 **구성**(으)로 이동하고 연결할 AEM 인스턴스의 위치(주소)를 입력한 다음 **저장**&#x200B;을 클릭합니다.

1. 장치 등록 프로세스 상태를 확인할 수 있도록 왼쪽 작업 메뉴에서 **장치** **등록** 링크로 이동합니다.

>[!NOTE]
>
>**State**&#x200B;이(가) **REGISTERED**&#x200B;인 경우 **Device ID** 필드가 채워져 있는 것을 볼 수 있습니다.
>
>**상태**&#x200B;가 **등록 취소됨**&#x200B;인 경우 **토큰**&#x200B;을(를) 사용하여 장치를 등록할 수 있습니다.

## Android™ Watchdog 구현 {#implementing-android-watchdog}

Android™ 아키텍처로 인해 디바이스를 재부팅하려면 애플리케이션에 시스템 권한이 있어야 합니다. 제조업체의 서명 키를 사용하여 APK에 서명합니다. 그렇지 않으면 워치독이 플레이어 애플리케이션을 다시 시작하고 디바이스를 재부팅하지 않을 수 있습니다.

### 제조업체 키를 사용하는 Android™ `apks`의 서명 {#signage-of-android-apks-using-manufacturer-keys}

*PowerManager* 또는 *HDMIControlServices*&#x200B;과(와) 같은 Android™의 권한이 있는 일부 API에 액세스하려면 제조업체의 키를 사용하여 Android™ `apk`에 서명하십시오.

>[!CAUTION]
>
>전제 조건:
>
>다음 단계를 수행하기 전에 Android™ SDK이 설치되어 있어야 합니다.

제조업체의 키를 사용하여 Android™ APK에 서명하려면 아래 단계를 따르십시오.

1. Google Play 또는 [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/) 페이지에서 APK를 다운로드합니다
1. *pk8* 및 *pem* 파일을 가져올 수 있도록 제조업체의 플랫폼 키를 가져옵니다.

1. `~/Library/Android/sdk/build-tools -name "apksigner"` 찾기를 사용하여 Android™ SDK에서 `apksigner` 도구를 찾습니다.
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Android™ SDK에서 zip 정렬 도구의 경로를 찾습니다
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. 장치에 adb 설치를 사용하여 ***aemscreensaligned.apk*** 설치

## Android™ Watchdog 서비스 이해 {#android-watchdog-services}

크로스 Android™ 감시 서비스는 *AlarmManager*&#x200B;을(를) 사용하여 Cordova 플러그인으로 구현됩니다.

다음 다이어그램은 Watchdog 서비스의 구현을 보여 줍니다.

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialization** - Cordova 플러그인을 초기화할 때 시스템 권한이 있는지 그리고 재부팅 권한이 있는지 확인하기 위해 사용 권한이 확인됩니다. 이 두 가지 기준을 충족하면 재부팅 보류 의도가 만들어지고, 그렇지 않으면 응용 프로그램을 다시 시작하려는 보류 의도(실행 활동에 따라)가 만들어집니다.

**2. Keep Alive 타이머** - Keep Alive 타이머는 15초마다 이벤트를 트리거하는 데 사용됩니다. 이 경우 기존의 보류 중인 의도(앱을 다시 부팅하거나 다시 시작하려는 의도)를 취소하고 향후 동일한 60초 동안 새로운 보류 중인 의도를 등록합니다(기본적으로 재부팅 연기).

>[!NOTE]
>
>Android™에서는 *AlarmManager*&#x200B;이(가) 앱이 충돌하고 API 19(Kitkat)에서 알람 전달이 정확하지 않아도 실행할 수 있는 *pendingIntts*&#x200B;을(를) 등록하는 데 사용됩니다. 타이머 간격과 *AlarmManager* *pendingIntent&#39;s* 알람 사이에 간격을 유지하십시오.

**3. 응용 프로그램 충돌** - 충돌이 있는 경우 AlarmManager에 등록된 PendingIntent for Reboot가 더 이상 재설정되지 않습니다. 따라서 Cordova 플러그인의 초기화 시 사용 가능한 권한에 따라 앱의 재부팅 또는 재시작을 실행합니다.

## Android™ Player 벌크 프로비저닝 {#bulk-provision-android-player}

Android™ 플레이어를 일괄적으로 롤아웃할 때 관리 UI에 수동으로 입력하지 않고 AEM 인스턴스를 가리키도록 플레이어를 프로비저닝하고 다른 속성을 구성해야 합니다.

>[!NOTE]
>이 기능은 Android™ player 42.0.372에서 사용할 수 있습니다.

Android™ 플레이어에서 대량 프로비저닝을 허용하려면 아래 단계를 따르십시오.

1. 이름이 `player-config.default.json`인 구성 JSON 파일을 만듭니다.
[JSON 정책 예](#example-json)와 다양한 [정책 특성](#policy-attributes)의 사용을 설명하는 표를 참조하십시오.

1. MDM, ADB 또는 Android™ Studio 파일 탐색기를 사용하여 이 정책 JSON 파일을 Android™ 장치의 *sdcard* 폴더에 놓습니다.

1. 파일이 배포되면 MDM을 사용하여 플레이어 응용 프로그램을 설치합니다.

1. 플레이어 애플리케이션이 실행되면 이 구성 파일을 읽고 해당 구성 파일이 등록된 다음 제어되는 해당 AEM 서버를 가리킵니다.

   >[!NOTE]
   >이 파일은 응용 프로그램을 처음 시작할 때 *읽기 전용*&#x200B;이므로 후속 구성에 사용할 수 없습니다. 구성 파일을 삭제하기 전에 플레이어를 시작한 경우 응용 프로그램을 제거하고 장치에 다시 설치하십시오.

### 정책 속성 {#policy-attributes}

다음 표에는 정책 속성이 참조용으로 JSON 예와 함께 요약되어 있습니다.

| **정책 이름** | **용도** |
|---|---|
| *server* | Adobe Experience Manager 서버의 URL입니다. |
| *해상도* | 장치의 해상도입니다. |
| *rebootSchedule* | 재부팅 일정은 모든 플랫폼에 적용됩니다. |
| *enableAdminUI* | 관리자 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되어 프로덕션에 있는 경우 *false*(으)로 설정하십시오. |
| *enableOSD* | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 프로덕션에 완전히 구성된 후 *false*(으)로 설정하는 것이 좋습니다. |
| *enableActivityUI* | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시하려면 활성화합니다. 문제 해결을 위해 활성화하고, 완전히 구성되어 프로덕션에 있는 경우 비활성화합니다. |
| *enableNativeVideo* | 비디오 재생에 기본 하드웨어 가속을 사용하려면 활성화합니다(Android™ 전용). |

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
>모든 Android™ 장치에는 실제 `*sdcard*`이(가) 삽입되었는지 여부에 관계없이 `*sdcard*` 폴더가 있습니다. 이 파일은 배포 시 다운로드 폴더와 동일한 수준에 있습니다. Samsung Knox와 같은 일부 MDM에서는 이 *sdcard* 폴더 위치를 *내부 저장소*(으)로 볼 수 있습니다.

## Enterprise Mobility Management를 사용한 Android™ Player 벌크 프로비저닝 {#bulk-provisioning}

Android™ 플레이어를 일괄적으로 배포할 때 모든 플레이어를 AEM에 수동으로 등록하는 것은 번거로워집니다. [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron 또는 Samsung Knox와 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 배포를 원격으로 프로비저닝하고 관리할 수 있습니다. AEM Screens Android™ player는 원격 프로비저닝이 가능하도록 업계 표준 EMM AppConfig를 지원합니다.

## Android™ 플레이어 이름 지정 {#name-android}

사용자에게 친근한 장치 이름을 Android™ 플레이어에 할당하여 할당된 장치 이름을 AEM(Adobe Experience Manager)로 보낼 수 있습니다. 이 기능을 사용하면 Android™ 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 컨텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록하기 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 더 이상 플레이어 이름을 변경할 수 없습니다.

Android™ 플레이어에서 이름을 구성하려면 아래 단계를 따르십시오.

1. **설정** > **장치 정보**(으)로 이동
1. 장치 이름을 편집하고 설정하여 Android™ 플레이어 이름을 지정합니다.

### Enterprise Mobility Management를 사용하여 Android™ Player 벌크 프로비저닝 구현 {#implementation}

Android™ Player에서 일괄 프로비저닝을 허용하려면 아래 단계를 따르십시오.

1. Android™ 장치가 Google Play 서비스를 지원하는지 확인합니다.
1. AppConfig를 지원하는 자주 사용하는 EMM 솔루션으로 Android™ 플레이어 장치를 등록합니다.
1. EMM 콘솔에 로그인하고 Google Play에서 AEM Screens 플레이어 애플리케이션을 가져옵니다.
1. 관리되는 구성 또는 관련 옵션을 클릭합니다.
1. 이제 서버 및 대량 등록 코드와 같이 구성할 수 있는 플레이어 옵션 목록이 표시됩니다.
1. 이러한 매개 변수를 구성하고, 저장하고, 장치에 정책을 배포합니다.

   >[!NOTE]
   >장치는 구성과 함께 애플리케이션을 수신해야 합니다. 선택한 구성이 있는 올바른 AEM 서버를 가리켜야 합니다. 벌크 등록 코드를 구성하도록 선택하고 AEM에 구성된 것과 동일하게 유지한 경우 플레이어가 자동으로 등록할 수 있어야 합니다. 기본 디스플레이를 구성한 경우 일부 기본 콘텐츠를 다운로드하여 표시할 수도 있습니다(나중에 필요에 따라 변경할 수 있음).

또한 AppConfig 지원에 대해 EMM 공급업체에 확인해야 합니다. [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 및 [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)과 같이 가장 인기 있는 항목은 이 업계 표준을 지원합니다.

### Screens 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대해 자세히 알아보세요. [Screens 원격 제어](implementing-remote-control.md)
