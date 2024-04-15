---
title: AEM Screens 구성 및 배포
description: AEM Screens 플레이어는 Android&trade;, Chrome OS, iOS 및 Windows에서 사용할 수 있습니다. AEM Screens 구성 및 배포에 대해 알아봅니다.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---

# AEM Screens 구성 및 배포 {#configuring-and-deploying-aem-screens}

이 페이지에서는 장치에 Screens 플레이어를 설치하고 구성하는 방법을 보여 줍니다.

## 서버 구성 {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens 플레이어는 CSRF(크로스 사이트 요청 위조) 토큰을 사용하지 않습니다. 따라서 AEM Screens에 사용할 준비가 되도록 AEM 서버를 구성하려면 빈 레퍼러를 허용하여 레퍼러 필터를 건너뜁니다.

## 상태 확인 프레임워크 {#health-check-framework}

상태 확인 프레임워크를 사용하면 AEM Screens 프로젝트를 실행하기 전에 필요한 두 구성이 설정되어 있는지 확인할 수 있습니다.

이를 통해 사용자는 AEM Screens 프로젝트를 실행하기 위한 다음의 두 가지 구성 검사를 확인할 수 있습니다. 즉, 다음 두 필터의 상태를 확인할 수 있습니다.

1. **빈 레퍼러 허용**
2. **https**

AEM Screens에 대해 이러한 두 가지 중요한 구성이 활성화되어 있는지 확인하려면 아래 단계를 따르십시오.

1. 다음으로 이동 [Adobe Experience Manager 웹 콘솔 Sling 상태 확인](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![assets](assets/health-check1.png)


2. 선택 **선택한 상태 검사 실행** 위에 나열된 두 속성에 대해 유효성 검사를 실행할 수 있습니다.

   두 필터가 모두 활성화된 경우 **화면 구성 상태 서비스** 다음을 표시합니다. **결과** 다음으로: **확인** 두 구성이 모두 활성화되었습니다.

   ![assets](assets/health-check2.png)

   하나 또는 두 필터가 모두 비활성화된 경우 아래 그림과 같이 사용자에 대한 경고가 표시됩니다.

   다음 경고는 두 필터가 모두 비활성화된 경우를 보여 줍니다.
   ![assets](assets/health-check3.png)

>[!NOTE]
>
>* 활성화하려면 **Apache Sling Referrer 필터**, 참조 [빈 레퍼러 요청 허용](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* 활성화하려면 **HTTP** 서비스, 참조 [Apache Felix Jetty 기반 HTTP 서비스](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).

### 사전 요구 사항 {#prerequisites}

아래의 주요 사항은 AEM Screens에 사용할 수 있도록 및 AEM 서버를 구성하는 데 도움이 됩니다.

#### 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** AEM 인스턴스 > hammer 아이콘 > **작업** > **웹 콘솔**.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성** 열림. Sling 레퍼러를 검색합니다.

   sling 레퍼러 속성을 검색하려면 **Command+F** 대상 **Mac** 및 **Ctrl+F** 대상 **Windows**.

1. 다음 확인: **빈 항목 허용** 아래 그림과 같은 옵션입니다.

   ![이미지](assets/config/empty-ref2.png)

1. 선택 **저장** apache Sling Referrer 필터를 활성화하려면 Allow Empty를 사용하십시오.


#### Apache Felix Jetty 기반 HTTP 서비스 {#allow-apache-felix-service}

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** AEM 인스턴스 > hammer 아이콘 > **작업** > **웹 콘솔**.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성** 열림. Apache Felix Jetty 기반 HTTP 서비스를 검색합니다.

   이 속성을 검색하려면 **Command+F** 대상 **Mac** 및 **Ctrl+F** 대상 **Windows**.

1. 다음 확인: **HTTP 활성화** 아래 그림과 같은 옵션입니다.

   ![이미지](assets/config/config-1.png)

1. 선택 **저장** 을(를) 활성화하려면 *http* 서비스.

#### AEM Screens용 Touch UI 활성화 {#enable-touch-ui-for-aem-screens}

AEM Screens은 TOUCH UI가 필요하며 Adobe Experience Manager(AEM)의 클래식 UI에서 작동하지 않습니다.

1. 다음으로 이동 `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. 다음을 확인합니다. **기본 작성 UI 모드** 이(가) (으)로 설정됨 **터치**&#x200B;아래 그림과 같이

또는 authorInstance를 사용하여 동일한 설정을 수행할 수도 있습니다 *>* 도구(망치 아이콘) > **작업** > **웹 콘솔** 및 검색 **WCM 작성 UI 모드 서비스**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>사용자 환경 설정을 사용하여 특정 사용자에 대해 클래식 UI를 항상 활성화할 수 있습니다.

#### NOSAMPLECONTENT 실행 모드의 AEM {#aem-in-nosamplecontent-runmode}

프로덕션에서 AEM을 실행하면 **NOSAMPLECONTENT** 실행 모드. 제거 *X-Frame-Options=SAMEORIGIN* 의 헤더(추가 응답 헤더 섹션)

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`

AEM Screens Player가 온라인 채널을 재생하는 데 필요합니다.

#### 암호 제한 {#password-restrictions}

에 대한 최신 변경 사항 포함 ***DeviceServiceImpl***, 암호 제한 사항을 제거할 필요가 없습니다.

다음을 구성할 수 있습니다. ***DeviceServiceImpl*** 화면 장치 사용자의 암호를 만드는 동안 암호 제한을 활성화하려면 아래 링크를 클릭하십시오.

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

아래 단계에 따라 구성하십시오. ***DeviceServiceImpl***:

1. 다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** AEM 인스턴스 > hammer 아이콘 > **작업** > **웹 콘솔**.

1. **Adobe Experience Manager 웹 콘솔 구성** 열림. `*deviceservice*`을 검색합니다. 속성을 검색하려면 **Command+F** macOS 및 **Ctrl+F** Microsoft® Windows용

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 구성 {#dispatcher-configuration}

AEM Screens 프로젝트에 대한 Dispatcher를 구성하는 방법에 대해 알아보려면 를 참조하십시오. [AEM Screens 프로젝트에 대한 Dispatcher 구성](dispatcher-configurations-aem-screens.md).

#### Java™ 인코딩 {#java-encoding}

설정 ***Java™ 인코딩*** 유니코드로 이동합니다. 예를 들어, `*Dfile.encoding=Cp1252*` 작동하지 않습니다.

>[!NOTE]
>
>프로덕션에서 AEM Screens 서버에 HTTPS를 사용합니다.
