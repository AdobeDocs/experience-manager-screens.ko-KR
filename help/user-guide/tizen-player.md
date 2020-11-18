---
title: 티젠 플레이어
description: 이 페이지에서는 Tizen Player의 설치 및 작업에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Tizen Player 구현 {#tizen-player}

## Tizen Player 설치 {#installing-tizen-player}

아래 절차에 따라 AEM Screens용 Tizen Player를 구현하십시오.

1. [**AEM 6.5 플레이어 다운로드**](https://download.macromedia.com/screens/) 페이지로 이동하여 티젠 플레이어를 다운로드합니다.

1. 로컬 컴퓨터에서 Tizen 플레이어(.zip) 파일을 설치합니다.

## 로컬 서버 설정 및 Zip 파일 추출 {#setting-local-server}

아래 절차에 따라 로컬 서버를 설정하고 압축을 푼 파일을 복사합니다.

1. 로컬 컴퓨터의 IP 주소를 가져옵니다.
   >[!NOTE]
   >공식 설명서를 검토하여 플랫폼에서 로컬 서버를 활성화하는 방법에 대해 알아보십시오.

1. 터미널에서 압축을 푼 설치 프로그램 폴더의 동일한 디렉토리로 이동하여 localhost가 작동하는지 확인합니다.

1. Tizen 플레이어는 로컬 서버에서 설치 프로그램을 다운로드합니다.

1. 추출된 두 파일(예: `AEMScreensPlayer.wgt` 및 `sssp_config.xml` )을 로컬 서버의 루트 디렉토리로 복사합니다.

### 삼성 장치에 업데이트 구성 {#config-updates}

Samsung 장치의 아래 단계에 따라 장치에서 AEM Screens 플레이어 설치를 완료합니다.

1. 삼성 장치로 이동합니다.

1. 장치의 **원격** 을 사용하여 [홈] 단추를 클릭하고 [ **URL 실행 설정]을 선택합니다**.

1. localhost 서버의 IP 주소를 입력합니다.

1. 개발자 **모드** 에서 **원격**&#x200B;을 선택합니다.

1. 장치의 원격 **에서 [홈** ] 단추를 클릭하고 [ **URL 시작 관리자]를 선택합니다**.

1. 이제 AEM Screens 플레이어는 Samsung 장치에 자동으로 설치하고 실행해야 합니다.



