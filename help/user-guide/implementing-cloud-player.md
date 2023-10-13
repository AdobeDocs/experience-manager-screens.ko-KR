---
title: Cloud Player 구현
seo-title: Implementing Cloud Player
description: 이 페이지를 따라 Cloud Player 구현에 대해 알아보십시오.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: 718ef76b620accd7096be2e4b7ac53658cb7fce7
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Cloud Player 구현  {#implementing-cloud-player}

이 섹션에서는 Cloud Player를 구현하는 방법을 설명합니다.

>[!NOTE]
>
>Cloud Player의 호환성에는 다양한 디바이스에서 일관된 성능을 보장하기 위해 PWA을 지원하는 최신 브라우저가 필요합니다.

## Cloud Player 설치 {#installing-cloud-player}

Cloud Player 설치는 플랫폼에 따라 다를 수 있습니다. 일반적으로 최신 브라우저를 사용하는 모든 플랫폼은 다음 단계에 따라 클라우드 플레이어 애플리케이션을 실행할 수 있습니다.

1. 브라우저를 열고 를 입력합니다. [클라우드 플레이어 URL](https://player.adobescreens.com) 주소창에.
1. 브라우저는 클라우드 플레이어가 설치 가능한지 확인한 다음 주소 표시줄에 설치 아이콘을 표시합니다.

![이미지](/help/user-guide/assets/cloud-player-install.png)

1. 확인 대화 상자에서 설치 아이콘 및 설치 버튼을 클릭합니다. Cloud Player는 디바이스에 독립 실행형 애플리케이션으로 설치되며, 아이콘을 사용하여 시작할 수 있습니다.

### Cloud Player 설치 옵션 {#cloud-player-install-option}

1. PWA에 대한 설치 옵션을 &quot;홈 화면에 추가&quot; 또는 A2HS 기능이라고도 합니다.  웹에서 PWA 설치에 대한 지원은 브라우저와 플랫폼마다 다릅니다.
1. 모든 브라우저에는 PWA 앱 설치 가능 여부를 확인하는 기준이 다릅니다. 일반적으로 브라우저는 다음을 확인합니다(자세한 내용은 여기 참조).
   * 애플리케이션에 플랫폼에 앱을 설치하기 위한 최소한의 필수 키(예: name, icons, start_url, display)가 있는 매니페스트 json 파일이 있는 경우
   * 응용 프로그램에 가져오기 이벤트 리스너가 있는 서비스 작업자 파일이 있는 경우
   * 앱은 https를 통해 제공되어야 합니다.
1. 설치 옵션은 브라우저와 장치 유형이 다른 위치에 표시될 수 있습니다. 일부 브라우저는 옵션 메뉴 표시줄에 설치 아이콘을 숨길 수 있습니다.

## Cloud Player 벌크 프로비저닝 {#bulk-provisioning}

여러 디바이스에서 클라우드 플레이어의 대량 프로비저닝을 수행하려면 다음을 수행합니다.

1. 키오스크 모드에서 URL로 브라우저 실행을 지원하는 MDM 솔루션을 선택합니다.
1. 다음 단계에 따라 모든 장치에 동일한 구성을 적용할 수 있습니다.
   1. 다음과 같이 액세스할 수 있도록 서버에 config.json을 호스팅합니다. https://&lt;config_server_host>/config.json
   1. 클라우드 플레이어를 설치하고 호스팅된 구성을 적용하려면 https://player.adobescreens.com?playerConfigAddress=https://과 같은 클라우드 플레이어 URL을 사용하십시오.&lt;config_server_host>
   1. Cloud Player 애플리케이션은 의 루트에서 config.json을 찾습니다. &lt;config_server_host>, config.json을 구문 분석하여 사용자 지정 구성을 가져오고 해당 구성을 적용합니다.
   1. 이러한 구성은 플레이어를 다시 로드할 때마다 적용됩니다.

## Chrome OS에서 일괄 프로비저닝 {#bulk-provisioning-chrome}

Chrome OS의 대량 프로비저닝에 대한 자세한 내용은 다음을 참조하십시오. [Chrome OS에 Cloud Player 설치](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM 인스턴스에 필요한 구성 {#bulk-provisioning-config-aem}

AEM 인스턴스 유형에 따라 다음 안내서 중 하나를 선택하여 CORS b/w AEM &amp; cloud player를 활성화합니다.
* [AEM 온-프레미스/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

