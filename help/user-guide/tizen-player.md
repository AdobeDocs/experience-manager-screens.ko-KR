---
title: 티젠 플레이어
description: 이 페이지에서는 Tizen Player의 설치 및 작업에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Tizen Player 구현 {#tizen-player}

## Tizen Player 설치 {#installing-tizen-player}

아래 절차에 따라 AEM Screens용 Tizen Player를 구현하십시오.

1. [**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지로 이동하여 티젠 플레이어를 다운로드합니다.

1. 로컬 컴퓨터에서 Tizen 플레이어(.zip) 파일을 설치합니다.

1. 로컬 컴퓨터의 IP 주소를 가져옵니다.

   >[!NOTE]
   >**Mac** 및 **Windows** 의 경우 `ifconfig` 터미널에서 명령을 입력합니다.

1. 터미널에서 압축을 푼 설치 프로그램 폴더의 동일한 디렉토리로 이동하여 localhost가 작동하는지 확인합니다.

   >[!NOTE]
   >**Mac**&#x200B;의 경우 `http://localhost` 서버를 실행하고 있는지 `http` 확인하고 입력합니다.

1. Tizen 플레이어는 로컬 서버에서 설치 프로그램을 다운로드합니다.

1. 추출된 두 파일 `AEMScreensPlayer.wgt` 을 복사하여 다음 `sssp_config.xml` 에 붙여넣습니다 `/Library/WebServer/Documents`.

### SamSame 장치의 구성 업데이트 {#config-updates}

Samsung 장치의 아래 단계에 따라 장치에서 AEM Screens 플레이어 설치를 완료합니다.

1. Samsung Remote에서 **Home** 버튼을 클릭합니다.
1. 설정 **에서** URL 론쳐를 **선택합니다**.
1. 개발자 **모드에서** [원격]을 선택합니다.
1. 웹 앱을 설치하고 컴퓨터의 IP 주소를 입력합니다.
AEM Screens 플레이어는 삼성 장치에 자동으로 설치해야 합니다.


