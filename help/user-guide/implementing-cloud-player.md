---
title: Cloud Player 구현
description: Cloud Player 구현에 대해 알아봅니다.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Cloud Player 구현  {#implementing-cloud-player}

AEM Screens은 전통적으로 ChromeOS, Windows, Android™ 및 `Tizen`. 그러나 사용자의 변화하는 요구에 따라 Adobe은 혁신적인 솔루션인 AEM Screens Cloud Player를 도입했습니다.

Cloud Player는 Adobe의 이전 기본 애플리케이션에서 크게 벗어난 것입니다. 서버에서 호스팅되는 점진적 웹 앱(PWA)입니다. 이 혁신적인 접근 방식은 웹 브라우저 내에서 직접 실행되는 플랫폼 독립적인 플레이어로 고객에게 힘을 줍니다.

Cloud Player에 액세스하는 방법은 방문하기만 하면 됩니다 `https://player.adobescreens.com`. 사용자는 플랫폼에 관계없이 장치에 설치할 수 있으며 원활한 디지털 사이니지 경험을 누릴 수 있습니다. Cloud Player의 호환성은 PWA을 지원하는 최신 브라우저가 있는지 여부에 따라 달라지므로, 다양한 디바이스에서 일관된 성능을 보장합니다. 수동 업데이트와 함께 수정 사항 및 기능을 자동으로 제공하는 플레이어에 대한 인사를 전해 언제든지 최신 기능을 이용할 수 있습니다. PWA 기반 Cloud Player로의 전환은 Adobe의 디지털 사이니지 제품의 놀라운 발전을 보여주며, 그 어느 때보다 접근성, 활용성, 사용자 친화성이 향상되었습니다.

이 섹션에서는 Cloud Player를 구현하는 방법을 설명합니다.

>[!NOTE]
>
>Cloud Player의 호환성에는 다양한 디바이스에서 일관된 성능을 보장하기 위해 PWA을 지원하는 최신 브라우저가 필요합니다.

## Cloud Player 설치 {#installing-cloud-player}

Cloud Player 설치는 플랫폼에 따라 다를 수 있습니다. 일반적으로 최신 브라우저를 사용하는 모든 플랫폼은 다음 단계에 따라 클라우드 플레이어 애플리케이션을 실행할 수 있습니다.

1. 브라우저를 열고 를 입력합니다. [클라우드 플레이어 URL](https://player.adobescreens.com) 주소창에.
1. 브라우저는 클라우드 플레이어가 설치 가능한지 확인한 다음 주소 표시줄에 설치 아이콘을 표시합니다.

   ![이미지](/help/user-guide/assets/cloud-player-install.png)

1. 확인 대화 상자에서 설치 아이콘 및 설치 버튼을 선택합니다. Cloud Player는 디바이스에 독립 실행형 애플리케이션으로 설치되며, 아이콘을 사용하여 시작할 수 있습니다.

>[!NOTE]
>
>### Cloud Player 설치 옵션 {#cloud-player-install-option}
>
1. PWA에 대한 설치 옵션을 &quot;홈 화면에 추가&quot; 또는 A2HS 기능이라고도 합니다. 웹에서 PWA 설치에 대한 지원은 브라우저와 플랫폼마다 다릅니다.
1. 모든 브라우저에는 PWA 앱 설치 가능 여부를 확인하는 기준이 다릅니다. 일반적으로 브라우저는 다음을 확인합니다(자세한 내용은 여기 참조).
>
* 애플리케이션에 플랫폼에 앱 설치에 필요한 최소한의 키가 있는 매니페스트 json 파일(이름, 아이콘, start_url, display)이 있는 경우
* 응용 프로그램에 가져오기 이벤트 리스너가 있는 서비스 작업자 파일이 있는 경우
* 앱은 https를 통해 제공되어야 합니다.
>
1. 설치 옵션은 브라우저와 장치 유형이 다른 위치에 표시될 수 있습니다. 일부 브라우저에서는 옵션 메뉴 표시줄에 설치 아이콘을 숨길 수 있습니다.

## Cloud Player 벌크 프로비저닝 {#bulk-provisioning}

여러 디바이스에서 클라우드 플레이어의 대량 프로비저닝을 수행하려면 다음을 수행합니다.

1. 키오스크 모드에서 URL로 브라우저 실행을 지원하는 MDM 솔루션을 선택합니다.
1. 다음 단계에 따라 모든 장치에 동일한 구성을 적용할 수 있습니다.

   1. 다음과 같이 액세스할 수 있도록 서버에 config.json을 호스팅합니다. `https://<config_server_host>/config.json`
   1. 클라우드 플레이어를 설치하고 호스팅된 구성을 적용하려면 다음과 같은 클라우드 플레이어 URL을 사용하십시오. `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. Cloud Player 애플리케이션은 의 루트에서 config.json을 찾습니다. &lt;config_server_host>, config.json을 구문 분석하여 사용자 지정 구성을 가져오고 해당 구성을 적용합니다.
   1. 이러한 구성은 플레이어를 다시 로드할 때마다 적용됩니다.

## Chrome OS에서 일괄 프로비저닝 {#bulk-provisioning-chrome}

Chrome OS의 대량 프로비저닝에 대한 자세한 내용은 다음을 참조하십시오. [Chrome OS에 Cloud Player 설치](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM 인스턴스에 필요한 구성 {#bulk-provisioning-config-aem}

AEM 인스턴스 유형에 따라 다음 안내서 중 하나를 선택하여 CORS b/w AEM &amp; cloud player를 활성화합니다.
* [AEM 온-프레미스/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Google의 Chrome 앱 사용 중단
>
1. Chrome OS 하드웨어의 Chrome 앱:
>
Google은 2025년 1월까지 마이그레이션을 계획하고 있으며 PWA 앱을 위해 Chrome 앱을 적극적으로 사용하지 않고 있습니다. 따라서 Chrome OS의 AEM Screens 플레이어 앱은 공유된 타임라인을 기반으로 더 이상 작동하지 않습니다. Adobe은 현재 프로덕션에서 Chrome 플레이어를 사용 중인 사용자에게 Screens Cloud Player로의 전환을 계획하도록 촉구합니다.
>
1. Mac, Windows 및 Linux®의 Chrome 확장 프로그램:
>
Google의 사용 중단 프로세스로 인해 Google Chrome 버전 114부터 Screens Chrome 확장 프로그램 플레이어가 더 이상 지원되지 않습니다. Adobe은 모든 개발 및 테스트 요구 사항을 충족하기 위해 해당 Screens Cloud Player로 전환하는 것이 좋습니다.

## 외부 콘텐츠 검색에 대한 오프라인 지원 {#offline-support}

다양한 사용 시나리오에서 채널은 기본적으로 오프라인 지원을 제공할 수 없는 외부 소스(예: 날씨 위젯 또는 상거래 통합 단일 페이지 애플리케이션)에서 콘텐츠를 검색해야 할 수 있습니다. 이러한 특정 사용 사례에 대해 오프라인 기능을 활성화하기 위해 Cloud Player에서는 사용자 지정 헤더에 대한 지원을 제공합니다.

Cloud Player는 네트워크 우선 캐시 전략을 사용합니다. 즉, 네트워크에서 콘텐츠를 가져온 다음(그런 다음 캐시를 최신 버전으로 업데이트) 사용 가능한 경우 캐시된 콘텐츠로 다시 폴백합니다. 이러한 컨텐츠 검색에 대한 오프라인 지원을 구현하려면 사용자 지정 헤더를 요청에 포함해야 합니다. 그런 다음 사용자 지정 헤더가 있는 요청이 플레이어에 캐시되어 네트워크 우선 캐시 전략을 유지하면서 콘텐츠에 대한 오프라인 액세스를 용이하게 합니다.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## 피드백

Adobe은 피드백을 소중히 여깁니다. 이를 통해 귀하의 의견을 공유하십시오. [양식](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
