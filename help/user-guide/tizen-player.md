---
title: Tizen 플레이어
description: Tizen 플레이어의 설치 및 작업에 대해 알아봅니다.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 1%

---

# Tizen 플레이어 구현 {#tizen-player}

## Tizen 플레이어 설치 {#installing-tizen-player}

AEM Screens용 Tizen 플레이어를 구현하려면 아래 단계를 따르십시오.

1. Tizen 플레이어를 다운로드할 수 있도록 [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/) 페이지로 이동합니다.

1. 로컬 컴퓨터에서 Tizen 플레이어 *(.zip)* 파일을 설치하십시오.

## HTTP 서버 설정 {#setting-local-server}

>[!NOTE]
> zip 파일을 추출하고 `http server`을(를) 통해 Tizen 플레이어를 사용할 수 있도록 합니다. `http server`은(는) Local 또는 Apache 서버일 필요가 없습니다.

아래 단계를 따르십시오.

1. 추출된 두 파일(예: `AEMScreensPlayer.wgt` 및 `sssp_config.xml`)을 로컬 Apache 웹 서버의 루트 디렉터리에 복사합니다.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`은(는) 실제 Tizen 플레이어 응용 프로그램이며 `sssp_config.xml`에는 Tizen 장치에 설치하는 데 도움이 되는 이 맵에 대한 정보가 포함되어 있습니다.

1. 로컬 HTTP 서버의 IP 또는 URL을 가져옵니다(그리고 루트 폴더가 아닌 하위 폴더로 추출한 경우 2단계에서 추출한 파일이 포함된 폴더의 경로).

1. Tizen 플레이어는 로컬 서버에서 설치 관리자를 다운로드합니다.

### Tizen 플레이어 이름 지정 {#name-tizen}

사용자에게 친숙한 장치 이름을 Tizen 플레이어에 할당하여 할당된 장치 이름을 Adobe Experience Manager(AEM)로 보낼 수 있습니다. 이 기능을 사용하면 Tizen 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 콘텐츠를 쉽게 할당할 수도 있습니다.

>[!NOTE]
>등록하기 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 더 이상 플레이어 이름을 변경할 수 없습니다.

아래 단계에 따라 Tizen 플레이어에서 이름을 구성합니다.

1. 리모컨에서 메뉴 단추를 클릭합니다.
1. 플레이어에 이름을 할당할 수 있도록 **네트워크** > **장치 이름**(으)로 이동합니다.

### Samsung 장치에서 업데이트 구성 {#config-updates}

장치에서 AEM Screens 플레이어 설치를 완료할 수 있도록 Samsung 장치에서 아래 절차를 따르십시오.

1. Samsung 장치로 이동하여 켭니다.
1. 장치의 리모콘에서 **MENU** 단추를 클릭하고 왼쪽 탐색 막대에서 **시스템**(으)로 스크롤합니다.
1. 아래로 스크롤하여 **재생 방법** 옵션을 클릭하고 **URL 런처** 옵션으로 변경합니다.
   ![이미지](/help/user-guide/assets/tizen/rms-2.png)
1. URL 런처가 설정되면 리모콘에서 **Home** 단추를 누릅니다.
1. **URL 런처 설정**(으)로 이동하고 localhost 서버의 IP 주소를 입력한 다음 **완료**&#x200B;를 클릭합니다.

   >[!NOTE]
   >Tizen 플레이어가 HTTP 서버에 연결할 수 있어야 합니다.

1. AEM Screens 플레이어는 Samsung 장치에 자동으로 설치되고 실행됩니다.

   >[!NOTE]
   >Tizen 장치와 `http` 서버를 모두 서로 연결할 수 있어야 합니다. 즉, 서버가 Tizen 플레이어에 연결할 수 있어야 합니다.


## SameSite 쿠키 문제가 있는 사용자 에이전트 면제 {#exempting-user-agents}

>[!IMPORTANT]
>**이 섹션은 Adobe Experience Manager(AEM) 6.5.5부터 AEM 6.5.7까지 적용됩니다**
>
>일부 브라우저 엔진이 AEM 6.5.5에서 AEM 6.5.7로 발급한 로그인 토큰에 사용된 *`SameSite=None`* 특성과 호환되지 않습니다. 일반적으로 브라우저를 사용 가능한 최신 버전으로 업그레이드하여 문제를 해결할 수 있습니다. 스마트 디스플레이, 셋톱 박스 또는 내장 된 검색 엔진이 있는 기타 장치와 같이 때때로 이러한 업그레이드가 가능하지 않을 수 있습니다.

*SameSite=None*&#x200B;을 사용할 때 호환되지 않는 클라이언트를 제외하려면 아래 단계를 따르십시오.

1. Adobe Experience Manager(AEM) 서비스 팩 6.5.7로 업그레이드하십시오.

1. AEM을 다시 시작한 후 `/system/console/configMgr`(으)로 이동하여 **Adobe Granite 토큰 인증 처리기**&#x200B;를 검색하십시오. **SameSite** 값의 값을 **없음**(으)로 설정합니다.

1. 새 옵션 *`User agents to be exempted from samesite attribute`*&#x200B;이(가) 표시됩니다. 이 옵션을 *SameSite=None* 특성과 호환되지 않는 사용자 에이전트에 해당하는 정규 표현식으로 채웁니다.

   >[!NOTE]
   >
   >자세한 내용은 [SameSite=None: 알려진 호환되지 않는 클라이언트](https://www.chromium.org/updates/same-site/incompatible-clients)를 참조하십시오. Tizen 플레이어의 경우 정규 표현식 `(.*)Tizen(.*)`을(를) 사용합니다.

1. AEM 6.5.5 이상 인스턴스에 대해 Tizen 플레이어를 등록하면 콘텐츠를 정상적으로 등록하고 표시해야 합니다.

## Tizen 플레이어 원격 프로비저닝 {#remote-provisioning}

Tizen 플레이어를 원격으로 프로비저닝하면 많은 노력 없이 수백, 수천 개의 Samsung Tizen 디스플레이를 배포할 수 있습니다. 서버 URL 및 벌크 등록 코드 또는 기타 매개 변수를 사용하여 각 플레이어를 수동으로 구성하는 번거로움을 피할 수 있습니다. 또한 AEM Screens as a Cloud Service이 있는 경우 클라우드 모드 및 클라우드 토큰을 구성합니다.

이 기능을 사용하면 Tizen 플레이어를 원격으로 구성하고 필요한 경우 중앙에서 해당 구성을 업데이트할 수 있습니다. 필요한 것은 적절한 매개 변수와 함께 `config.json`을(를) 저장하기 위해 Tizen 응용 프로그램 `(wgt and xml file)`을(를) 호스팅하는 데 사용되는 `HTTP` 서버와 텍스트 편집기입니다.

Tizen 장치에서 URL 런처 주소를 구성했는지 확인하십시오. 홈 버튼 > URL 런처 설정을 클릭합니다.
Tizen 응용 프로그램을 호스팅하는 `HTTP` 서버에서 `config.json` 파일을 `wgt` 파일과 같은 위치에 배치합니다. 파일 이름은 `config.json`이어야 합니다.
Tizen 플레이어는 설치 및 실행 시(및 다시 부팅할 때마다) `config.json` 파일의 설정을 확인하고 적용합니다.

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

다음 표에는 정책과 해당 기능이 요약되어 있습니다.

>[!NOTE]
>플레이어의 관리 UI 정책 구성은 엄격하게 적용되며 수동으로 재정의되지 않습니다. 특정 정책에 대해 수동 플레이어 구성을 허용하려면 정책 구성에 정책을 지정하지 마십시오.
>>예를 들어 다시 부팅 일정에 대해 수동 구성을 허용하려면 정책 구성에 키 `rebootSchedule`을(를) 지정하지 마십시오. 플레이어를 다시 로드할 때마다 정책 구성을 읽습니다.

| **정책 이름** | **용도** |
|---|---|
| 서버 | Adobe Experience Manager(AEM) 서버의 URL입니다. |
| registrationKey | 미리 공유한 키를 사용하여 장치를 대량으로 등록하는 데 사용됩니다. |
| 해상도 | 장치의 해상도입니다. |
| rebootScheduling | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 관리자 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있도록 활성화합니다. 문제 해결을 위해 활성화하고, 완전히 구성되어 프로덕션에 있는 경우 비활성화합니다. |
| cloudMode | Tizen 플레이어가 Screens as a Cloud Service에 연결되도록 하려면 true로 설정합니다. AMS 또는 온프레미스 AEM에 연결하려면 false로 설정합니다. |
| cloudToken | Screens as a Cloud Service에 대해 등록할 등록 토큰입니다. |


## Tizen 장치를 Samsung RMS(원격 관리 서비스)에 등록 {#enroll-tizen-device-rms}

아래 단계에 따라 Tizen 장치를 Samsung RMS(원격 관리 서비스)에 등록하고 URL 런처를 원격으로 구성하십시오.

>[!NOTE]
>네트워크 설정 및 모니터를 확인합니다.

1. **메뉴** -> **네트워크** -> **서버 네트워크 설정**(으)로 이동한 다음 **Enter**&#x200B;를 누르십시오.

1. 서버 주소로 이동하고 MagicInfo URL 액세스를 입력한 다음 **완료**&#x200B;를 누릅니다.

1. 필요한 경우 TLS를 설정합니다. 포트로 이동하고 서버에서 포트 번호를 클릭한 다음 **저장**&#x200B;을 클릭합니다.

1. **장치** 탭으로 이동하여 구성한 장치를 확인합니다. 장치를 찾으면 확인란을 클릭한 다음 **승인**&#x200B;을 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-3.png)

1. 필요한 정보를 입력하고 장치 그룹을 클릭합니다. **확인**&#x200B;을 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-7.png)

1. 장치가 승인되면 장치 목록에 표시됩니다. 다음 그림과 같이 장치 상자에서 *정보*&#x200B;를 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-6.png)

1. 디바이스 정보 대화 상자가 표시됩니다. **장치 정보** 탭을 클릭하고 **편집**&#x200B;을 클릭합니다.

   >![이미지](/help/user-guide/assets/tizen/rms-5.png)

1. 장치 옵션을 편집하고 **설정** 탭을 클릭합니다. 아래 그림과 같이 `SSSP` 응용 프로그램을 설치할 수 있도록 **URL 런처** 섹션으로 이동하고 wgt 및 `SSSP config file`을(를) 호스팅하는 URL을 입력하십시오.

   ![이미지](/help/user-guide/assets/tizen/rms-9.png)

1. **저장**&#x200B;을 클릭합니다.

### Screens 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대해 자세히 알아보세요. [Screens 원격 제어](implementing-remote-control.md)
