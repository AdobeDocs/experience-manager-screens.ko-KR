---
title: 타이젠 플레이어
description: 이 페이지에서는 타이젠 플레이어의 설치 및 작업에 대해 설명합니다.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 1%

---

# 타이젠 플레이어 구현 {#tizen-player}

## 타이젠 플레이어 설치 {#installing-tizen-player}

AEM Screens용 Tizen Player를 구현하려면 아래 절차를 따르십시오.

1. 로 이동합니다 [AEM Screens Player 다운로드](https://download.macromedia.com/screens/) 페이지를 클릭하여 Tizen Player를 다운로드합니다.

1. 타이젠 플레이어 설치 *(.zip)* 로컬 컴퓨터의 파일

## http 서버 설정 {#setting-local-server}

>[!NOTE]
> zip 파일을 추출하고 를 통해 타이젠 플레이어를 사용할 수 있도록 합니다. `http server`. (다음 `http server` 는 로컬 또는 Apache 서버가 아니어야 합니다.

아래 단계를 따르십시오.

1. 추출된 두 파일(예: `AEMScreensPlayer.wgt` 및 `sssp_config.xml` 를 로컬 Apache 웹 서버의 루트 디렉토리에 추가합니다.

   >[!NOTE]
   >다음 `AEMScreensPlayer.wgt`은 실제 타이젠 플레이어 응용 프로그램이며 `sssp_config.xml` 타이젠 장치에 설치하는 데 도움이 되는 이 맵에 대한 정보를 포함합니다.

1. 로컬 HTTP 서버의 IP 또는 URL(및 루트 폴더가 아닌 하위 폴더로 추출된 경우 2단계에서 추출된 파일이 포함된 폴더의 경로)을 가져옵니다.

1. 타이젠 플레이어는 로컬 서버에서 설치 프로그램을 다운로드합니다.

### 이름 지정 타이젠 플레이어 {#name-tizen}

Tizen 플레이어에 사용자에게 친숙한 장치 이름을 할당하여 할당된 장치 이름을 Adobe Experience Manager(AEM)에 전송할 수 있습니다. 이 기능을 사용하면 타이젠 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 컨텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 플레이어 이름을 더 이상 변경할 수 없습니다.

타이젠 플레이어에서 이름을 구성하려면 아래 단계를 따르십시오.

1. 리모컨의 메뉴 단추를 클릭합니다.
1. 다음으로 이동 **네트워크** —> **장치 이름** 플레이어에 이름을 할당하려면

### 삼성 장치에 대한 업데이트 구성 {#config-updates}

Samsung 장치에서 아래 절차에 따라 장치에서 AEM Screens 플레이어 설치를 완료합니다.

1. 삼성 장치로 이동하여 켜십시오.

1. 을(를) 클릭합니다. **메뉴** 장치의 리모컨에서 아래로 스크롤하여 **시스템** 왼쪽 탐색 막대에서 을 클릭합니다.

1. 아래로 스크롤하여 **를 통해 재생** 옵션을 선택하고 변경합니다. **URL 시작 관리자** 선택 사항입니다.
   ![이미지](/help/user-guide/assets/tizen/rms-2.png)

1. URL 실행 프로그램이 설정되면 **홈** 리모컨에서 단추를 클릭합니다.

1. 로 이동합니다 **URL 실행 관리자 설정** 로컬 호스트 서버의 IP 주소를 입력하고 **완료**.
   >[!NOTE]
   >타이젠 플레이어는 http 서버에 연결할 수 있어야 합니다.

1. 이제 AEM Screens 플레이어가 Samsung 장치에 자동으로 설치 및 실행되어야 합니다.

   >[!NOTE]
   >타이젠 장치와 `http` 서버는 서로 연결할 수 있어야 합니다. 즉, 서버에 연결할 수 있어야 합니다.


## SameSite 쿠키 문제로 사용자 에이전트 제외 {#exempting-user-agents}

>[!IMPORTANT]
>**이 섹션은 Adobe Experience Manager(AEM) 6.5.5에서 AEM 6.5.7에 적용됩니다**
>일부 브라우저 엔진이 와 호환되지 않습니다 *SameSite=None* 속성은 AEM 6.5에서 AEM 6.7로 발행한 로그인 토큰에 사용됩니다. 일반적으로 브라우저를 사용 가능한 최신 버전으로 업그레이드하여 문제를 해결할 수 있습니다. 스마트 디스플레이, 상위 박스 또는 검색 엔진이 내장된 다른 장치 설정 등과 같이 일부 경우에는 업그레이드할 수 없습니다.

사용할 때 호환되지 않는 클라이언트를 제외하려면 아래 절차를 따르십시오 *SameSite=None*:

1. Adobe Experience Manager(AEM) 서비스 팩 6.5.7로 업그레이드하십시오.

1. AEM이 다시 시작된 후으로 이동 `/system/console/configMgr` 및 검색 **Adobe Granite 토큰 인증 핸들러**. 에 대한 값을 설정합니다. **SameSite** 값 **없음**.

1. 새 옵션이 표시됩니다 *samesite 속성에서 제외되는 사용자 에이전트*. 와 호환되지 않는 사용자 에이전트에 해당하는 regex로 이 필드를 채웁니다 *SameSite=None* 속성을 사용합니다.
   >[!NOTE]
   >자세한 내용은 [SameSite=None: 호환되지 않는 알려진 클라이언트](https://www.chromium.org/updates/same-site/incompatible-clients) 자세한 내용 타이젠 플레이어의 경우 regex를 사용합니다. `(.*)Tizen(.*)`.

1. AEM 6.5.5 이상 인스턴스에 Tizen 플레이어를 등록하면 컨텐츠를 정상적으로 등록하고 표시됩니다.

## 타이젠 플레이어 원격 프로비저닝 {#remote-provisioning}

Tizen Player를 원격으로 프로비저닝하면 많은 노력 없이 수백, 수천 개의 삼성 타이젠 디스플레이를 배포할 수 있습니다. 서버 URL 및 벌크 등록 코드 또는 기타 매개 변수로 각 플레이어를 구성하거나, Screens에서 as a Cloud Service으로 클라우드 모드 및 클라우드 토큰을 구성하는 번거로운 수동 작업이 발생하지 않습니다.

이 기능을 사용하면 필요한 경우 타이젠 플레이어를 원격으로 구성하고 해당 구성을 중앙에서 업데이트할 수 있습니다. 필요한 것은 `HTTP` 타이젠 응용 프로그램을 호스팅하는 데 사용되는 서버 `(wgt and xml file)` 텍스트 편집기를 사용하여 `config.json` 를 사용하십시오.

타이젠 장치에서 URL 시작 관리자 주소(홈 단추 —> URL 시작 관리자 설정)를 구성했는지 확인합니다.
설정 `HTTP` 타이젠 응용 프로그램을 호스팅하는 서버에서 파일을 배치합니다. `config.json` 와 동일한 위치에 `wgt` 파일. 파일 이름은 다음과 같아야 합니다. `config.json`.
타이젠 플레이어는 설치 및 실행 시(그리고 재부팅할 때마다)에서 설정을 확인하고 적용합니다. `config.json` 파일.

### JSON 정책 예 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 정책 속성 및 목적 {#policy-attributes}

다음 표에는 해당 기능이 있는 정책이 요약되어 있습니다.

>[!NOTE]
>정책 구성은 엄격히 적용되며, 플레이어의 관리 UI에서 수동으로 재정의되지 않습니다. 특정 정책에 대해 수동 플레이어 구성을 허용하려면 정책 구성에 정책을 지정하지 마십시오. 예를 들어, 재부팅을 위한 수동 구성을 허용하려면 키를 지정하지 마십시오 `rebootSchedule` ( 정책 구성)를 참조하십시오. 정책 구성은 플레이어가 다시 로드될 때마다 읽습니다.

| **정책 이름** | **목적** |
|---|---|
| 서버 | AEM(Adobe Experience Manager) 서버의 URL입니다. |
| registrationKey | 사전 공유 키를 사용하여 장치의 벌크 등록에 사용됩니다. |
| 해상도 | 장치의 해상도. |
| rebootSchedule | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 사이트에서 장치를 구성하려면 관리자 UI를 활성화합니다. 완전히 구성 및 프로덕션에서 false로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 구성이 완전히 완료되고 프로덕션에서 false로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시하도록 활성화합니다. 문제 해결을 활성화하고 완전히 구성하고 프로덕션에서 비활성화합니다. |
| cloudMode | 타이젠 플레이어에서 Screens에 as a Cloud Service으로 연결하려면 true로 설정합니다. AMS 또는 On-Prem AEM에 연결하려면 false로 설정하십시오. |
| cloudToken | Screens에 등록할 등록 토큰 as a Cloud Service. |


## RMS(Samsung Remote Management Service)에 타이젠 장치 등록 {#enroll-tizen-device-rms}

RMS(Samsung Remote Management Service)에 타이젠 장치를 등록하고 URL 런처를 원격으로 구성하려면 아래 단계를 따르십시오.

>[!NOTE]
>네트워크 설정과 모니터를 확인합니다.

1. 다음으로 이동 **메뉴** -> **네트워크** -> **서버 네트워크 설정** 누르기 **Enter 키**.

1. 서버 주소로 이동하여 MagicInfo URL 액세스를 입력하고 키를 누릅니다 **완료**.

1. 필요한 경우 TLS를 설정합니다. 포트로 이동하여 서버에서 포트 번호를 선택하고 을(를) 클릭합니다 **저장**.

1. 로 이동합니다 **장치** 탭하고 방금 구성한 장치를 확인합니다. 장치가 발견되면 확인란을 클릭하고 를 선택합니다 **승인**.

   >![이미지](/help/user-guide/assets/tizen/rms-3.png)

1. 필요한 정보를 입력하고 장치 그룹을 선택합니다. 클릭 **확인** 승인 프로세스를 완료합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-7.png)

1. 장치가 승인되면 장치 목록에 표시됩니다. 을(를) 클릭합니다. *정보* 장치 상자에 있는 단추, 즉 **i**&#x200B;아래 그림과 같이,

   >![이미지](/help/user-guide/assets/tizen/rms-6.png)

1. 장치 정보 대화 상자가 표시됩니다. 을(를) 선택합니다 **장치 정보** 탭을 클릭하고 **편집**.

   >![이미지](/help/user-guide/assets/tizen/rms-5.png)

1. 장치 옵션을 편집하고 **설정** 탭. 다음으로 이동 **URL 시작 관리자** 섹션을 입력하고 Wgt 및 를 호스팅하는 URL을 입력합니다. `SSSP config file` 를 설치하려면 `SSSP` 아래 그림에 표시된 대로 애플리케이션입니다.

   ![이미지](/help/user-guide/assets/tizen/rms-9.png)

1. 클릭 **저장** 변경 사항이 표시 화면에 나타납니다.

### 화면 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대한 자세한 내용은 다음을 참조하십시오. [화면 원격 제어](implementing-remote-control.md)
