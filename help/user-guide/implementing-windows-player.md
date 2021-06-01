---
title: Windows 10 Player 구현
seo-title: Windows 10 Player 구현
description: AEM Screens Windows 10 Player 구성에 대한 자세한 내용은 이 페이지를 참조하십시오.
seo-description: AEM Screens Windows 10 Player 구성에 대한 자세한 내용은 이 페이지를 참조하십시오.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Screens 관리, Windows Player
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 1%

---


# Windows 10 Player 구현 {#implementing-windows-player}

이 섹션에서는 AEM Screens Windows 10 Player 구성에 대해 설명합니다. 구성 파일 및 사용 가능한 옵션에 대한 정보와 개발 및 테스트에 사용할 설정에 대한 권장 사항을 제공합니다.

## Windows Player {#installing-windows-player} 설치

AEM Screens용 Windows Player를 구현하려면 AEM Screens용 Windows Player를 설치하십시오.

[**AEM 6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

>[!NOTE]
>Windows Player에 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### AEM Screens 6.5.5 서비스 팩의 환경 설정 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Windows Player용 환경을 설정해야 합니다.

**Lax**&#x200B;에서 로그인 토큰 쿠키에 대한 **SameSite 속성을** Adobe Experience Manager 웹 콘솔에서 **없음**으로 설정합니다
모든 AEM 작성자 및 게시 인스턴스의 구성**.**

아래 단계를 따르십시오.

1. **Adobe Experience Manager 웹 콘솔로 이동합니다.
`http://localhost:4502/system/console/configMgr`를 사용하는 구성**.

1. *Granite 토큰 인증 핸들러 Adobe*&#x200B;를 검색합니다.

1. **Lax**&#x200B;에서 로그인 토큰 쿠키&#x200B;**에 대한** SameSite 속성을 **없음**으로 설정합니다.
   ![이미지](/help/user-guide/assets/granite-updates.png)

1. **저장**&#x200B;을 클릭합니다.

### Ad-Hoc 메서드 {#ad-hoc-method}

Ad-Hoc 메서드를 사용하면 최신 Windows Player(*.exe*)를 설치할 수 있습니다. [**AEM 6.5 Player 다운로드**](https://download.macromedia.com/screens/) 페이지를 방문하십시오.

애플리케이션을 다운로드한 후에는 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리에서 을(를) 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 작업 메뉴에서 **구성**&#x200B;으로 이동하고 연결할 AEM 인스턴스의 위치(주소)를 입력하고 **저장**&#x200B;을 클릭합니다.
1. 왼쪽 작업 메뉴에서 **Device** **등록** 링크로 이동하여 장치 등록 프로세스의 상태를 확인합니다.

>[!NOTE]
>
>**State**&#x200B;가 **REGISTERED**&#x200B;이면 **장치 id** 필드가 채워지는 것을 볼 수 있습니다.
>
>**State**&#x200B;가 **UNREGISTER**&#x200B;인 경우 **토큰**&#x200B;을 사용하여 장치를 등록할 수 있습니다.

## Windows Installer {#changing-default-options}에서 기본 옵션 변경

Windows Installer의 기본 옵션을 변경하는 방법과 사용 가능한 사용자 지정 목록을 변경하려면 이 섹션을 따르십시오.

## CLI(PowerShell)를 사용한 설치 {#install-powershell}

1. Screens 플레이어용 사용자 지정 위치 **전용**을(를) 만듭니다. 예:
   `C:\Users\User\screens-player`)
1.  설치
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 열기
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**예**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Windows Player {#bulk-registration} 벌크 등록

Windows 플레이어를 구현하는 경우 모든 단일 플레이어를 수동으로 구성할 필요가 없습니다. 대신, 구성 JSON 파일이 테스트되고 배포가 준비되면 업데이트할 수 있습니다.

구성에서는 모든 플레이어가 구성 파일에 제공된 동일한 서버를 ping하는지 확인합니다. 각 플레이어를 수동으로 등록해야 합니다.

아래 절차에 따라 Windows 10 Player를 구성하십시오.

1. Windows Player를 설치합니다.
1. ***%appdata%\com.adobe.aem.screens.player\config.json***&#x200B;에서 구성 파일을 찾습니다.
1. 아래 정보를 사용하여 구성 JSON을 업데이트한 다음, 플레이어가 상주하는 모든 시스템에 동일한 폴더를 복사합니다.

### 정책 속성 {#policy-attributes}

다음 표에는 참조에 대한 정책 JSON 예제 정책이 있는 정책 속성이 요약되어 있습니다.

| **정책 이름** | **목적** |
|---|---|
| 서버 | AEM(Adobe Experience Manager) 서버의 URL입니다. |
| 해상도 | 장치의 해상도. |
| rebootSchedule | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 사이트에서 장치를 구성하려면 관리자 UI를 활성화합니다. 완전히 구성 및 프로덕션에서 false로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 완전히 구성 및 프로덕션에서 를 설정한 후에는 을 false 로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시하도록 활성화합니다. 문제 해결을 활성화하고 완전히 구성하고 프로덕션에서 비활성화합니다. |

#### 정책 JSON 파일 {#example-policy-json-file} 예

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

## 키오스크 모드 {#enabling-kiosk-mode} 활성화

Windows 플레이어를 배포할 때는 다른 응용 프로그램이나 작업 표시줄이 Windows 바탕 화면에 나타나지 않도록 키오스크 모드를 활성화해야 합니다.

>[!CAUTION]
>
>Adobe은 Windows용 키오스크를 사용하도록 장치 관리 솔루션을 권장합니다. 키오스크 모드를 활성화할 장치 관리 솔루션이 없는 경우 아래 절차를 따르십시오. 이 방법에서는 Windows 10 Enterprise 및 Edu에서 사용할 수 있는 셸 런처 기능을 사용합니다. Microsoft에서 권장하는 비UWP 앱의 다른 수단도 키오스크를 사용하도록 설정할 수 있습니다. 특히 Windows의 다른 버전에서 사용할 수도 있습니다.

아래 절차에 따라 키오스크 모드를 활성화합니다.

>[!NOTE]
>
>아래 단계를 따르기 전에 Windows 10 Enterprise 또는 Education을 사용하는지 확인하십시오.

1. 셸 실행 프로그램을 활성화합니다.

   자세한 내용은 Microsoft Windows의 **[셸 시작 관리자](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 페이지에서 ***셸 시작 관리자 구성*** 섹션을 참조하십시오.

1. 키오스크에 사용할 관리자가 아닌 사용자(아직 없는 경우)를 만듭니다. 로컬 또는 도메인 사용자일 수 있습니다.
1. [AEM Screens Player 다운로드](https://download.macromedia.com/screens/) 페이지에서 해당 키오스크 사용자의 Windows 플레이어를 설치합니다.
1. 자세한 내용은 [셸 런처를 사용하여 Windows 10 키오스크](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher)를 만들어 PowerShell 스크립트를 수정하십시오.

   PowerShell 스크립트를 수정하여 사용자가 만든 사용자 이름으로 대체합니다. 응용 프로그램 실행 파일의 경로가 올바른지 확인합니다. 사용자 정의 셸을 키오스크 사용자의 windows 플레이어 응용 프로그램으로 설정하고 기본값을 다른 사용자의 explorer.exe로 설정합니다.

1. PowerShell 스크립트를 관리자로 실행합니다.
1. 키오스크 사용자 및 플레이어 응용 프로그램이 바로 시작될 때 재부팅하고 로그인합니다.

### 문제 해결 {#troubleshooting}

키오스크 사용자로 로그인할 때 검정색 화면이 나타나면 windows 플레이어 실행 파일의 경로를 잘못 지정했을 수 있습니다. 관리자로 다시 로그인하고 스크립트를 확인하고 다시 실행합니다.

Windows 플레이어의 기본 설치 경로는 다음과 같습니다.

***C:\Users\&amp;lt;사용자>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

링크의 샘플 스크립트는 사용자 지정 셸을 활성화하고 비활성화합니다. 따라서 스크립트를 두 개로 분할하고 아래의 적용 가능한 행을 활성화/비활성화해야 할 수 있습니다.

>[!NOTE]
>
>일부 Windows 환경에서 PowerShell 스크립트는 정책(특히 서명되지 않은 스크립트)에 의해 제한될 수 있습니다. 스크립트를 실행하려면 일시적으로 이 제한을 비활성화하고 다시 활성화해야 할 수 있습니다. PowerShell 창을 열고 다음 명령을 사용합니다.
>
>*제한 없는 설정 실행 정책*  - 제한 사항을 일시적으로 제거합니다.
>
>*set-executionpolicy restricted*  - 스크립트를 실행한 후 제한을 다시 사용하도록 설정

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

