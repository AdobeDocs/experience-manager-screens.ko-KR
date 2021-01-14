---
title: 티젠 플레이어
description: 이 페이지에서는 Tizen Player의 설치 및 작업에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: c1ddb5f458831025bdcd1481bcdc198616f5bb47
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 1%

---


# Tizen 플레이어 구현 {#tizen-player}

## Tizen Player {#installing-tizen-player} 설치

AEM Screens용 Tizen Player를 구현하려면 아래 절차를 따르십시오.

1. [AEM Screens Player 다운로드](https://download.macromedia.com/screens/) 페이지로 이동하여 티젠 플레이어를 다운로드합니다.

1. 로컬 컴퓨터에서 Tizen 플레이어 *(.zip)* 파일을 설치합니다.

## 샘플 쿠키 문제로 사용자 에이전트 제외 {#exempting-user-agents}

>[!IMPORTANT]
>**이 섹션은 Adobe Experience Manager(AEM) 6.5.5에서 AEM 6.5.7**에 적용됩니다.
>AEM 6.5에서 AEM 6.7로 발행한 로그인 토큰에 사용된 *SameSite=None* 속성과 호환되지 않는 브라우저 엔진이 있습니다. 대부분의 경우 브라우저를 사용 가능한 최신 버전으로 업그레이드하여 문제를 해결할 수 있습니다. 스마트 디스플레이, 내장 검색 엔진이 있는 상단 상자 또는 기타 장치 등 일부 경우에는 업그레이드를 수행할 수 없습니다.

*SameSite=None*&#x200B;을 사용할 때 이러한 호환되지 않는 클라이언트를 제외하려면 아래 단계를 따르십시오.

1. Adobe Experience Manager(AEM) 서비스 팩 6.5.8으로 업그레이드하십시오.

   >[!NOTE]
   >AEM 6.5.8을 설치하는 경우 2단계와 3단계를 건너뛸 수 있습니다.

1. AEM에서 `/system/console/bundles`으로 이동하고 `install/update` 단추를 클릭합니다.

1. `crx-auth-token` jar 파일을 설치합니다. 이 jar는 인증과 관련되어 있으므로 이 jar를 설치한 후 AEM을 종료하고 다시 시작해야 할 수 있습니다.

1. AEM이 다시 시작되면 `/system/console/configMgr`으로 이동하여 **Adobe Granite Token 인증 핸들러**&#x200B;를 검색합니다. **SameSite** 값의 값을 **None**&#x200B;으로 설정합니다.

1. 샘플 속성&#x200B;*에서 제외되는 새 옵션*&#x200B;사용자 에이전트가 표시됩니다. *SameSite=None* 속성과 호환되지 않는 사용자 에이전트에 해당하는 regex로 이 값을 채웁니다.
   >[!NOTE]
   >[SameSite=None을 참조하십시오.자세한 내용은 호환되지 않는 클라이언트](https://www.chromium.org/updates/same-site/incompatible-clients)을(를) 참조하십시오. Tizen 플레이어의 경우 regex를 사용합니다.`(.*)Tizen(.*)`.

1. AEM 6.5.5 이상 인스턴스에 대해 Tizen 플레이어를 등록하면 정상적으로 컨텐츠를 등록하고 표시할 수 있습니다.


## 로컬 서버 설정 및 Zip 파일 압축 해제 {#setting-local-server}

아래 단계를 따르십시오.

1. 추출된 두 파일(예: `AEMScreensPlayer.wgt` 및 `sssp_config.xml`)을 로컬 Apache 웹 서버의 루트 디렉토리에 복사합니다.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`은 실제 Tizen 플레이어 응용 프로그램이며 `sssp_config.xml`에는 이 맵을 Tizen 장치에 설치할 수 있도록 돕는 이 맵에 대한 정보가 포함되어 있습니다.

1. 로컬 HTTP 서버의 IP 또는 URL(루트 폴더가 아닌 하위 폴더로 추출된 파일이 들어 있는 폴더의 경로) 가져오기

1. Tizen 플레이어는 로컬 서버에서 설치 프로그램을 다운로드합니다.

### Samsung 장치에 업데이트 구성 {#config-updates}

장치에서 AEM Screens 플레이어의 설치를 완료하려면 Samsung 장치의 아래 절차를 따르십시오.

1. Samsung 장치로 이동하여 켜십시오.

1. 장치의 리모콘에서 **MENU** 단추를 클릭하고 왼쪽 탐색 막대에서 **System**&#x200B;으로 아래로 스크롤합니다.

1. 아래로 스크롤하고 **을 통해 재생 옵션을 선택하고** URL 시작 관리자&#x200B;**옵션으로 변경합니다.**
   ![이미지](/help/user-guide/assets/tizen/rms-2.png)

1. URL 실행(Launcher)이 설정되면 리모컨에서 **Home** 단추를 누릅니다.

1. **URL 시작 설정**&#x200B;으로 이동하고 로컬 호스트 서버의 IP 주소를 입력하고 **완료**&#x200B;를 클릭합니다.
   >[!NOTE]
   >Tizen 플레이어는 http 서버에 연결할 수 있어야 합니다.

1. 이제 AEM Screens Player가 Samsung 장치에 자동으로 설치 및 실행되어야 합니다.

   >[!NOTE]
   >Tizen 장치와 `http` 서버 모두 서로 연결할 수 있어야 합니다. 즉, 서버에 Tizen 플레이어에 연결할 수 있어야 합니다.

## Tizen Player의 벌크 프로비저닝 {#bulk-provisioning-tizen-player}

>[!NOTE]
>많은 수의 장치에 대해 각 및 모든 장치의 관리자 UI에 AEM 서버 주소를 수동으로 입력하는 것은 번거로운 작업일 수 있습니다. 대규모 솔루션을 배포하고 관리하는 경우 Samsung Remote Management(RMS) 솔루션을 사용하는 것이 좋습니다. 자세한 내용은 [RMS(Samsung Remote Management Service)](#enroll-tizen-device-rm)에 Tizen 장치 등록을 참조하십시오.

실행 시 AEM 작성자 인스턴스를 가리키도록 애플리케이션을 일괄 프로비저닝하려면 아래 단계를 따르십시오.

1. [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)를 다운로드하여 설치합니다.
1. Tizen 스튜디오를 사용하여 `wgt` 파일을 엽니다.
1. `firmware-platform.js` 파일을 열고 `DEFAULT_PREFERENCES` 검색을 수행하고 서버 URL을 AEM 작성자 URL로 변경하고 저장합니다.
1. 새 `wgt` 파일을 만듭니다.

   >[!NOTE]
   >서명 인증서를 만들거나 설정해야 할 수 있습니다.

1. 이 새 `wgt` 파일 RMS를 배포하고, 플레이어가 실행되면 자동으로 서버를 가리키므로 모든 장치에 대해 수동으로 입력할 필요가 없습니다.

### RMS(Samsung Remote Management Service) {#enroll-tizen-device-rms}에 Tizen 장치 등록

RMS(Samsung Remote Management Service)에 Tizen 장치를 등록하고 URL Launcher를 원격으로 구성하려면 아래 절차를 따르십시오.

>[!NOTE]
>네트워크 설정과 모니터를 확인합니다.

1. **메뉴** -> **네트워크** -> **서버 네트워크 설정**&#x200B;으로 이동하고 **Enter**&#x200B;를 누릅니다.

   >[!NOTE]
   >화면이 URL 실행 프로그램을 통해 재생되도록 설정되어 있는지 확인합니다.
   >![이미지](/help/user-guide/assets/tizen/rms-2.png)

1. 서버 주소로 이동하여 MagicInfo URL 액세스 권한을 입력하고 **Done**&#x200B;을 누릅니다.

1. 필요한 경우 TLS를 설정합니다. 포트로 이동하여 서버에서 포트 번호를 선택하고 **저장**&#x200B;을 클릭합니다.

1. **장치** 탭으로 이동하여 방금 구성한 장치를 확인합니다. 장치가 발견되면 확인란을 클릭하고 **승인**&#x200B;을 선택합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-3.png)

1. 필요한 정보를 입력하고 장치 그룹을 선택합니다. 승인 프로세스를 완료하려면 **확인**&#x200B;을 클릭하십시오.

   >![이미지](/help/user-guide/assets/tizen/rms-7.png)

1. 장치가 승인되면 장치 목록에 표시됩니다. 아래 그림과 같이 장치 상자에 있는 *정보* 단추(**i**)를 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-6.png)

1. 장치 정보 대화 상자가 표시됩니다. **장치 정보** 탭을 선택하고 **편집**&#x200B;을 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-5.png)

1. 장치 옵션을 편집하고 **설정** 탭을 선택합니다. **URL Launcher** 섹션으로 이동하여 아래 그림과 같이 wgt를 호스팅하는 URL 및 `SSSP config file` 애플리케이션을 설치합니다.`SSSP`

   ![이미지](/help/user-guide/assets/tizen/rms-9.png)

1. 변경 내용이 표시 화면에 표시하려면 **저장**&#x200B;을 클릭합니다.




