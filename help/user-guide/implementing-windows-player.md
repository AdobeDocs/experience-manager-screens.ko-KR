---
title: Windows 10 Player 구현
description: AEM Screens Windows 10 플레이어 구성에 대해 알아봅니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 1%

---

# Windows 10 Player 구현 {#implementing-windows-player}

이 섹션에서는 AEM Screens Windows 10 Player 구성에 대해 설명합니다. 구성 파일 및 사용 가능한 옵션에 대한 정보와 개발 및 테스트에 사용할 설정에 대한 권장 사항을 제공합니다.

## Windows Player 설치 {#installing-windows-player}

AEM Screens용 Windows Player를 구현하려면 AEM Screens용 Windows Player를 설치하십시오.

다음 방문: [**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지를 가리키도록 업데이트하는 중입니다.

>[!NOTE]
>Windows 플레이어에는 창 모드가 없습니다. 항상 전체 화면 모드입니다.

### AEM Screens 6.5.5 서비스 팩용 환경 설정 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 서비스 팩을 사용하는 경우 Windows 플레이어용 환경을 설정합니다.

설정 **로그인 토큰 쿠키에 대한 SameSite 속성** 출처: **Lax** 끝 **없음** 출처: **Adobe Experience Manager 웹 콘솔 구성** 모든 AEM 작성자 및 게시 인스턴스.

아래 단계를 따르십시오.

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** 사용 `http://localhost:4502/system/console/configMgr`.

1. 검색 대상 *Adobe Granite 토큰 인증 핸들러*.

1. 설정 **로그인 토큰 쿠키에 대한 SameSite 속성** 출처: **Lax** 끝 **없음**.
   ![이미지](/help/user-guide/assets/granite-updates.png)

1. **저장**&#x200B;을 선택합니다.

### 임시 메서드 {#ad-hoc-method}

Ad-Hoc 메서드를 사용하면 최신 Windows Player(*.exe*). 방문 [**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지를 가리키도록 업데이트하는 중입니다.

응용 프로그램을 다운로드한 후 플레이어의 단계에 따라 임시 설치를 완료합니다.

1. 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
1. 다음으로 이동 **구성** 왼쪽 작업 메뉴에서 연결하려는 AEM 인스턴스의 위치(주소)를 입력하고 를 선택합니다 **저장**.
1. 다음 위치로 이동 **장치** **등록** 디바이스 등록 프로세스의 상태를 확인할 수 있도록 왼쪽 작업 메뉴에서 링크를 클릭합니다.

>[!NOTE]
>
>다음과 같은 경우 **시/도** 은(는) **등록됨**&#x200B;를 확인합니다. **장치 ID** 필드가 채워집니다.
>
>다음과 같은 경우 **시/도** 은(는) **등록되지 않음**, 다음을 사용할 수 있습니다. **토큰** 장치를 등록합니다.

## Windows Player 이름 지정 {#name-windows}

사용자에게 친숙한 장치 이름을 Windows 플레이어에 할당하여 지정된 장치 이름을 AEM(Adobe Experience Manager)로 보낼 수 있습니다. 이 기능을 사용하면 Windows 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 컨텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록하기 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 더 이상 플레이어 이름을 변경할 수 없습니다.

Windows 플레이어에서 이름을 구성하려면 아래 단계를 따르십시오.

1. 선택 **시작** > **실행**.
1. 입력 `system.cpl`.
1. 컴퓨터 이름 탭을 사용하여 컴퓨터의 호스트 이름을 설정합니다.

## Windows Installer에서 기본 옵션 변경 {#changing-default-options}

Windows Installer의 기본 옵션 및 사용 가능한 사용자 지정 목록을 변경하는 방법을 배울 수 있도록 이 섹션을 따르십시오.

## CLI를 사용한 설치(PowerShell) {#install-powershell}

1. 사용자 지정 위치 만들기 **전용** Screens 플레이어의 경우 예:
   `C:\Users\User\screens-player`)
1. 설치
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 열기
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**예**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Windows Player 일괄 등록 {#bulk-registration}

Windows 플레이어를 구현할 때 모든 플레이어를 수동으로 구성할 필요는 없습니다. 대신 구성 JSON 파일을 테스트하고 배포할 준비가 되면 업데이트할 수 있습니다.

구성을 통해 모든 플레이어가 구성 파일에 제공된 동일한 서버를 ping하도록 합니다. 각 플레이어를 수동으로 등록합니다.

아래 단계에 따라 Windows 10 Player를 구성하십시오.

1. Windows Player를 설치합니다.
1. 아래에서 구성 파일 찾기 ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. 아래 정보를 사용하여 구성 JSON을 업데이트한 다음 동일한 폴더를 플레이어가 있는 모든 시스템에 복사합니다.

### 정책 속성 {#policy-attributes}

다음 표에는 정책 속성이 참조용으로 JSON 예와 함께 요약되어 있습니다.


| **정책 이름** | **목적** |
|---|---|
| 서버 | Adobe Experience Manager(AEM) 서버의 URL입니다. |
| registrationKey | 미리 공유한 키를 사용하여 장치를 대량으로 등록하는 데 사용됩니다. |
| 해상도 | 장치의 해상도입니다. |
| rebootScheduling | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 관리자 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 작업 진행 상황을 표시할 수 있도록 활성화합니다. 문제 해결을 위해 활성화하고, 완전히 구성되어 프로덕션에 있는 경우 비활성화합니다. |
| cloudMode | Windows 플레이어를 Screens에 as a Cloud Service으로 연결하려면 true로 설정합니다. AMS 또는 온프레미스 AEM에 연결하려면 false로 설정합니다. |
| cloudToken | Screens에 대해 as a Cloud Service으로 등록할 등록 토큰입니다. |

#### 예제 정책 JSON 파일 {#example-policy-json-file}

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

Windows 플레이어를 배포하는 경우 다른 응용 프로그램이나 작업 표시줄이 Windows 바탕 화면에 나타나지 않도록 키오스크 모드를 활성화해야 합니다.

>[!CAUTION]
>
>Adobe은 Windows용 키오스크를 활성화하는 장치 관리 솔루션을 권장합니다. 키오스크 모드를 활성화하는 장치 관리 솔루션이 없는 경우 아래 단계를 따르십시오. 이 메서드는 Windows 10 enterprise 및 Edu에서 사용할 수 있는 셸 시작 관리자 기능을 사용합니다. 특히 다른 Windows 버전에서 키오스크를 활성화하기 위해 UWP가 아닌 앱에 대해 Microsoft이 권장하는 다른 수단도 적용할 수 있습니다.

키오스크 모드를 활성화하려면 아래 단계를 따르십시오.

>[!NOTE]
>
>아래 단계를 수행하기 전에 Windows 10 Enterprise 또는 Education을 사용하는지 확인하십시오.

1. 셸 런처를 사용하도록 설정합니다.

   다음을 참조하십시오 ***셸 런처 구성*** 위치: **[쉘 런처](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/customize/shell-launcher)** page by Microsoft® Windows에서 추가 정보를 지원합니다.

1. 키오스크에 사용할 비관리 사용자(아직 없는 경우)를 만듭니다. 로컬 또는 도메인 사용자일 수 있습니다.
1. 에서 해당 Kiosk 사용자의 Windows 플레이어를 설치합니다. [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/) 페이지를 가리키도록 업데이트하는 중입니다.
1. 다음을 참조하십시오 [셸 런처를 사용하여 Windows 10 키오스크 만들기](https://learn.microsoft.com/en-us/windows/configuration/assigned-access/shell-launcher/?tabs=intune) PowerShell 스크립트를 수정하려면 여기를 클릭하십시오.

   사용자 이름을 만든 사용자 이름으로 바꿀 수 있도록 PowerShell 스크립트를 수정합니다. 애플리케이션 실행 파일에 대한 경로가 올바른지 확인합니다. 이렇게 하면 사용자 지정 셸이 키오스크 사용자의 Windows 플레이어 응용 프로그램으로 설정되고 다른 사용자의 경우 기본값이 explorer.exe로 설정됩니다.

1. 관리자로 PowerShell 스크립트를 실행합니다.
1. 키오스크 사용자 및 플레이어 애플리케이션이 바로 시작될 때 재부팅하고 로그인합니다.

### 문제 해결 {#troubleshooting}

키오스크 사용자로 로그인한 후 검정색 화면이 나타나면 Windows 플레이어 실행 파일의 경로를 잘못 지정했을 수 있습니다. 관리자로 다시 로그인하고 스크립트를 확인하고 다시 실행합니다.

Windows 플레이어의 기본 설치 경로는 다음과 같습니다.

***C:\Users\&lt;your user=&quot;&quot;>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

링크의 샘플 스크립트는 사용자 지정 셸을 활성화하거나 비활성화합니다. 따라서 스크립트를 두 개로 분할하고 아래의 적용 가능한 행을 활성화/비활성화하십시오.

>[!NOTE]
>
>일부 Windows 환경에서는 PowerShell 스크립트가 정책에 의해 제한될 수 있습니다(특히 서명되지 않은 스크립트). 스크립트를 실행하려면 이 제한을 일시적으로 비활성화했다가 다시 활성화하여 스크립트를 실행합니다. PowerShell 창을 열고 다음 명령을 사용합니다.
>
>*`set-executionpolicy unrestricted`* - 일시적으로 제한을 제거합니다.
>
>*`set-executionpolicy restricted`* - 스크립트를 실행한 후 제한을 다시 활성화합니다.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Screens 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대한 자세한 내용은 여기를 참조하십시오. [화면 원격 제어](implementing-remote-control.md)