---
title: Windows 10 Player 구현
seo-title: Windows 10 Player 구현
description: AEM Screens Windows 10 플레이어 구성에 대해 알려면 이 페이지를 따르십시오.
seo-description: AEM Screens Windows 10 플레이어 구성에 대해 알려면 이 페이지를 따르십시오.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: 2ab8496cebb81864a8354ad5dcb8d72bc1e44c13
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---


# Windows 10 Player 구현 {#implementing-windows-player}

이 섹션에서는 AEM Screens Windows 10 플레이어 구성에 대해 설명합니다. 개발 및 테스트에 사용할 설정에 대한 구성 파일 및 사용 가능한 옵션 및 권장 사항을 제공합니다.

## Windows Player 설치 {#installing-windows-player}

AEM Screens용 Windows Player를 구현하려면 AEM Screens용 Windows Player를 설치하십시오.

AEM [**6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지를 참조하십시오.

>[!NOTE]
>Windows 플레이어에는 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### AEM Screens 6.5.5 서비스 팩 환경 설정 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Windows 플레이어에 대한 환경을 설정해야 합니다.

로그인 **토큰 쿠키에** 대한 **SameSite 속성을 Lax에서** None으로 **설정하** 는 **Facebook 웹 콘솔Configuration모든 AEM 작성자 및 게시 인스턴스의 SameSite 속성을 None으로** 설정합니다.

아래 단계를 따르십시오.

1. 를 사용하여 **Adobe Experience Manager 웹 콘솔** 구성으로 이동합니다 `http://localhost:4502/system/console/configMgr`.

1. [MOCK] Search for *Adobe Granite Token Authentication Handler*.

1. 로그인 **토큰 쿠키의 SameSite 속성을 Lax에서** **None** 으로 ****설정합니다.
   ![이미지](/help/user-guide/assets/granite-updates.png)

1. **저장**&#x200B;을 클릭합니다.

### 애드혹 메서드 {#ad-hoc-method}

애드혹 방법을 사용하면 최신 Windows Player(*.exe*)를 설치할 수 있습니다. AEM [**6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지를 참조하십시오.

애플리케이션을 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 작업 **메뉴에서** 구성으로 이동하고 연결할 AEM 인스턴스의 위치(주소)를 입력하고 **저장을 클릭합니다**.
1. 왼쪽 작업 메뉴에서 **장치** **** 등록링크로 이동하여 장치 등록 프로세스의 상태를 확인합니다.

>[!NOTE]
>
>상태 **가** **REGISTERED**&#x200B;인 **** 경우장치 ID필드가 채워지는 것을 확인할 수 있습니다.
>
>상태 **가** **등록되지인**&#x200B;경우 **토큰을** 사용하여 장치를 등록할수 있습니다.

### 벌크 서버 구성:하나의 구성으로 여러 Windows 10 플레이어 등록 {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Windows 플레이어를 설치한 후에는 하나의 구성으로 여러 플레이어를 등록할 수 있습니다.

>[!NOTE]
>
>**Windows Player 벌크 등록**
>
>Windows 플레이어를 구현할 때는 모든 단일 플레이어를 수동으로 구성할 필요가 없습니다. 대신 구성 JSON 파일을 테스트하여 배포할 준비가 된 후에 업데이트할 수 있습니다.
>
>이 구성을 통해 구성 파일에 제공된 동일한 서버에 대한 모든 플레이어가 ping되도록 할 수 있습니다. 여전히 각 플레이어를 수동으로 등록해야 합니다.

아래 절차에 따라 Windows 10 Player를 구성합니다.

1. Windows Player를 설치합니다.
1. %appdata%\com.adobe.aem.screens.player\config.json ***에서 구성 파일을 찾습니다***.
1. 아래 정보를 사용하여 구성 JSON을 업데이트한 다음 플레이어가 있는 모든 시스템에 동일한 폴더를 복사합니다.

### 정책 속성 {#policy-attributes}

다음 표는 참조용 JSON 정책 예제 정책과 함께 정책 속성을 요약합니다.

| **정책 이름** | **목적** |
|---|---|
| 서버 | Adobe Experience Manager(AEM) 서버에 대한 URL. |
| 해상도 | 장치의 해상도입니다. |
| rebootSchedule | 플레이어를 재부팅하는 일정 |
| enableAdminUI | 관리 UI를 활성화하여 사이트에서 장치를 구성합니다. 구성 및 제작 시 false로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 설정이 완전히 구성되고 프로덕션에서 false로 설정되도록 고려하십시오. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있습니다. 문제 해결을 활성화하거나 구성 및 제작 시 비활성화할 수 있습니다. |

#### 정책 JSON 파일 예 {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## 키오스크 모드 활성화 {#enabling-kiosk-mode}

Windows 플레이어를 배포하는 경우 키오스크 모드를 활성화하여 다른 응용 프로그램이나 작업 표시줄이 Windows 데스크탑에 표시되지 않도록 해야 합니다.

>[!CAUTION]
>
>Adobe은 Windows용 키오스크를 사용하도록 장치 관리 솔루션을 권장합니다. 키오스크 모드를 활성화할 장치 관리 솔루션이 없는 경우 아래 절차를 따르십시오. 이 메서드는 Windows 10 enterprise 및 Edu에서 사용할 수 있는 셸 실행 기능을 사용합니다. UWP 이외의 앱에 대해 Microsoft에서 권장하는 모든 수단을 특별히 Windows의 다른 버전에서 키오스크을 사용하도록 설정할 수도 있습니다.

아래 절차에 따라 키오스크 모드를 활성화합니다.

>[!NOTE]
>
>아래 단계를 수행하기 전에 Windows 10 Enterprise 또는 Education을 사용해야 합니다.

1. 셸 실행 기능을 활성화합니다.

   자세한 내용은 ***Microsoft Windows 지원*** 의 **[셸 실행](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 페이지구성 섹션을 참조하십시오.

1. 키오스크에 사용할 관리자가 아닌 사용자(아직 없는 경우)를 만듭니다. 로컬 또는 도메인 사용자일 수 있습니다.
1. AEM Screens 플레이어 다운로드 페이지에서 해당 키오스크 사용자의 windows 플레이어를 [설치합니다](https://download.macromedia.com/screens/) .
1. 자세한 내용은 [Shell 스크립트를 수정하려면 셸 실행](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 프로그램을 사용하여 Windows 10 키오스크 생성을 참조하십시오.

   PowerShell 스크립트를 수정하여 사용자 이름을 만든 사용자 이름으로 바꿉니다. 응용 프로그램 실행 파일의 경로가 올바른지 확인합니다. 이렇게 하면 사용자 정의 셸이 키오스크 사용자의 windows 플레이어 응용 프로그램으로 설정되고 다른 사용자의 경우 기본값을 explorer.exe로 설정합니다.

1. PowerShell 스크립트를 관리자로 실행합니다.
1. 키오스크 사용자와 플레이어 응용 프로그램이 바로 시작할 때 재부팅하여 로그인합니다.

### 문제 해결 {#troubleshooting}

키오스크 사용자로 로그인할 때 검은 화면이 표시되는 경우 windows 플레이어 실행 파일의 경로를 잘못 지정했을 수 있습니다. 관리자로 다시 로그인하고 스크립트를 확인하고 다시 실행합니다.

Windows 플레이어의 기본 설치 경로는 다음과 같습니다.

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screenscreens-player-electronic\AEM Screens Player.exe***

링크의 샘플 스크립트는 사용자 지정 셸을 활성화하고 비활성화합니다. 따라서 스크립트를 두 개로 분할하고 아래 해당 줄을 활성화/비활성화해야 할 수 있습니다.

>[!NOTE]
>
>일부 창 환경에서는 정책(특히 서명되지 않은 스크립트)으로 PowerShell 스크립트가 제한될 수 있습니다. 스크립트를 실행하려면 스크립트를 일시적으로 비활성화하고 다시 활성화해야 할 수 있습니다. PowerShell 창을 열고 다음 명령을 사용합니다.
>
>*set-execution policy unrestricted* - 임시로 제한 사항 제거
>
>*set-executional policy restricted* - 스크립트 실행 후 제한을 다시 사용하도록 설정

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

