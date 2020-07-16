---
title: Android Player 구현
seo-title: Android Player 구현
description: 이 페이지에서 충돌 시 플레이어를 복구할 수 있는 솔루션인 Android Watchdog 구현에 대해 알아보십시오.
seo-description: 이 페이지에서 충돌 시 플레이어를 복구할 수 있는 솔루션인 Android Watchdog 구현에 대해 알아보십시오.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: db3429d93833ec22ba60732c45da274830692b39
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---


# Android Player 구현 {#implementing-android-player}

이 섹션에서는 Android 플레이어 구성에 대해 설명합니다. 개발 및 테스트에 사용할 설정에 대한 구성 파일 및 사용 가능한 옵션 및 권장 사항을 제공합니다.

또한 **Watchdog** 는 충돌 시 플레이어를 복구할 수 있는 솔루션입니다. 애플리케이션을 감사자 서비스에 등록한 다음 주기적으로 살아 있는 서비스에 메시지를 보내야 합니다. 감시 서비스가 지정된 시간 내에 활성 상태 유지 메시지를 받지 못하는 경우, 서비스는 정리 복구를 위해 장치를 다시 부팅하거나(충분한 권한이 있는 경우) 응용 프로그램을 다시 시작합니다.

## Android Player 설치 {#installing-android-player}

AEM Screens용 Android 플레이어를 구현하려면 AEM Screens용 Android 플레이어를 설치하십시오.

AEM [**6.5 플레이어 다운로드&#x200B;**](https://download.macromedia.com/screens/)페이지를 참조하십시오.

### 애드혹 메서드 {#ad-hoc-method}

애드혹 방법을 사용하면 최신 Android 플레이어(*.exe*)를 설치할 수 있습니다. AEM [**6.5 Player 다운로드&#x200B;**](https://download.macromedia.com/screens/)페이지를 참조하십시오.

애플리케이션을 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 작업 메뉴에서 **구성으로** 이동하고 연결할 AEM 인스턴스의 위치(주소)를 입력하고 **저장을 클릭합니다**.

1. 왼쪽 작업 메뉴에서 **장치** **** 등록링크로 이동하여 장치 등록 프로세스의 상태를 확인합니다.

>[!NOTE]
>
>상태 **가** **REGISTERED**&#x200B;인 **** 경우장치 ID필드가 채워지는 것을 확인할 수 있습니다.
>
>상태 **가** **등록되지인**&#x200B;경우 **토큰을** 사용하여 장치를 등록할수 있습니다.

## Android Watchdog 구현 {#implementing-android-watchdog}

Android 아키텍처로 인해 장치를 재부팅하려면 응용 프로그램에 시스템 권한이 있어야 합니다. 이렇게 하려면 제조업체의 서명 키를 사용하여 apk에 서명해야 합니다. 그렇지 않으면 감시 기관에서 플레이어 애플리케이션을 다시 시작하고 장치를 다시 부팅하지 않습니다.

### 제조업체 키를 사용한 Android 앱의 서명 {#signage-of-android-apks-using-manufacturer-keys}

PowerManager 또는 *HDMICcontrolServices와 같은* Android의 권한 있는 API **&#x200B;중 일부를 액세스하려면 제조업체 키를 사용하여 android api에 서명해야 합니다.

>[!CAUTION]
>
>전제 조건:
>
>다음 단계를 수행하기 전에 Android SDK가 설치되어 있어야 합니다.

제조업체 키를 사용하여 android apk에 서명하려면 아래 절차를 따르십시오.

1. Google Play 또는 [AEM Screens 플레이어 다운로드 페이지에서 페이지](https://download.macromedia.com/screens/) 다운로드
1. 제조업체에서 플랫폼 키를 *받아 pk8* 및 *pem* 파일 가져오기

1. 찾기 ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;를 사용하여 android sdk에서 apksigner 도구를 찾습니다.
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. android sdk에서 zip 정렬 도구의 경로 찾기
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensored.apk
1. 장치에 ***adb 설치를 사용하여 aemscreensalested.apk*** 설치

## Android Watchdog 구현 {#android-watchdog-implementation}

크로스 Android 감시 서비스는 AlarmManager를 사용하여 cordova 플러그인으로 *구현됩니다*.

다음 다이어그램은 감시 서비스 구현을 보여줍니다.

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 초기화** cordova 플러그인을 초기화할 때 시스템 권한이 있는지, 따라서 재부팅 권한이 있는지 확인하기 위해 권한이 확인됩니다. 이 두 기준이 충족되면 재부팅 대기 중인 의향이 생성되고, 그렇지 않으면 애플리케이션을 다시 시작할 보류 중인 의도(실행 활동에 따라)가 생성됩니다.

**2. 살아 있는 타이머** 유지 타이머는 15초마다 이벤트를 트리거하는 데 사용됩니다. 이 경우, 기존의 보류 중인 의도를 취소하고(앱을 다시 부팅하거나 다시 시작하려면) 향후 60초 동안 동일한 보류 중인 의도를 새로 등록해야 합니다(기본적으로 재부팅 지연).

>[!NOTE]
>
>Android에서 *AlarmManager* 는 앱이 충돌하고 API 19(Kitkat)에서 해당 알람 배달이 부정확하더라도 실행할 수 있는 *보류* 중인 인스턴스를 등록하는 데 사용됩니다. 타이머의 간격과 AlarmManager의 *pendingIntent의* 경고 사이에 약간의 간격을 *유지하십시오* .

**3. 응용 프로그램 충돌** 충돌이 발생하는 경우, AlarmManager에 등록된 재부팅 대기 중 의사표시는 더 이상 재설정되지 않으므로 cordova 플러그인의 초기화 시 사용 가능한 권한에 따라 앱의 다시 부팅 또는 다시 시작을 실행합니다.
