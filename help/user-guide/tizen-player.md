---
title: 티젠 플레이어
description: 이 페이지에서는 Tizen Player의 설치 및 작업에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: c1e7187ad3841cde08377d6daf700885d17706ba
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---


# Tizen 플레이어 구현 {#tizen-player}

## Tizen Player {#installing-tizen-player} 설치

AEM Screens용 Tizen Player를 구현하려면 아래 절차를 따르십시오.

1. [AEM 6.5 Player 다운로드](https://download.macromedia.com/screens/) 페이지로 이동하여 티젠 플레이어를 다운로드합니다.

1. 로컬 컴퓨터에서 Tizen 플레이어 *(.zip)* 파일을 설치합니다.

## 로컬 서버 설정 및 Zip 파일 압축 해제 {#setting-local-server}

아래 절차에 따라 로컬 서버를 설정하고 추출된 파일을 복사합니다.

1. 로컬 컴퓨터의 IP 주소를 가져옵니다.
   >[!NOTE]
   >공식 설명서를 검토하여 플랫폼에서 로컬 서버를 활성화하는 방법에 대해 알아보십시오.

1. Terminal에서 압축을 푼 설치 프로그램 폴더의 동일한 디렉토리로 이동하여 localhost가 작동하는지 확인합니다.

1. Tizen 플레이어는 로컬 서버에서 설치 프로그램을 다운로드합니다.

1. 추출된 두 파일(예: `AEMScreensPlayer.wgt` 및 `sssp_config.xml`)을 로컬 Apache 웹 서버의 루트 디렉토리에 복사합니다.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`은 실제 Tizen 플레이어 응용 프로그램이며 `sssp_config.xml`에는 이 맵을 Tizen 장치에 설치할 수 있도록 돕는 이 맵에 대한 정보가 포함되어 있습니다.

### Samsung 장치에 업데이트 구성 {#config-updates}

장치에서 AEM Screens 플레이어의 설치를 완료하려면 Samsung 장치의 아래 절차를 따르십시오.

1. Samsung 장치로 이동하여 켜십시오.

1. 장치의 리모콘에서 **MENU** 단추를 클릭하고 왼쪽 탐색 막대에서 **System**&#x200B;으로 아래로 스크롤합니다.

1. 아래로 스크롤하고 **URL 실행 프로그램** 옵션을 선택합니다.
   ![이미지](/help/user-guide/assets/tizen/url-launcher.png)

1. 리모콘에서 **홈** 단추를 누릅니다.

1. localhost 서버의 IP 주소를 입력합니다.

1. **개발자 모드**&#x200B;에서 **원격**&#x200B;을 선택합니다.

1. 장치의 원격 장치에서 **홈** 단추를 클릭하고 **URL 시작 관리자**&#x200B;를 선택합니다.

1. 이제 AEM Screens Player가 Samsung 장치에 자동으로 설치 및 실행되어야 합니다.

## Tizen Player의 벌크 프로비저닝 {#bulk-provisioning-tizen-player}

>[!NOTE]
>많은 수의 장치에 대해 각 및 모든 장치의 관리자 UI에 AEM 서버 주소를 수동으로 입력하는 것은 번거로운 작업일 수 있습니다. 솔루션 배포 및 관리에 RMS(Samsung Remote Management) 솔루션을 사용하는 것이 좋습니다. 자세한 내용은 [RMS(Samsung Remote Management Service)](#enroll-tizen-device-rm)에 Tizen 장치 등록을 참조하십시오.

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

1. [서버 주소]로 이동하여 MagicInfo URL 액세스를 입력하고 [완료]를 누릅니다.

1. 대/소문자별로 TLS를 사용하거나 사용하지 않도록 설정
   1. 포트로 이동하여 서버에서 포트 번호를 선택합니다.
   1. 옵션이 준비되면 저장을 누릅니다.

1. MIS에 로그인한 후 장치 탭으로 이동
   1. IP 주소 및/또는 Mac 주소를 보고 방금 구성한 장치를 찾습니다.
   1. 장치가 발견되면 확인란을 클릭하고 승인을 선택합니다.

1. [승인됨] 단추를 클릭하면 다음 팝업이 나타납니다
   1. 필요한 정보 채우기
   1. 장치 그룹 선택
   1. 확인 단추를 클릭하여 승인 프로세스를 완료합니다.

1. 장치가 승인되면 장치 목록에 다음과 같이 나타납니다.
   1. 장치 상자 &quot;i&quot;에 있는 정보 단추를 클릭합니다.

1. [장치 정보] 팝업이 다음과 같이 나타나고 [편집] 단추를 클릭합니다.

1. 장치 옵션을 편집하고 **설정** 탭을 선택합니다.

1. **URL Launcher** 섹션으로 이동하여 아래 그림과 같이 wgt를 호스팅하는 URL 및 `SSSP config file` 애플리케이션을 설치합니다.`SSSP`

   ![이미지](/help/user-guide/assets/tizen/rms-9.png)

1. 표시 화면에서 변경 사항을 적용하려면 **저장**&#x200B;을 클릭합니다.




