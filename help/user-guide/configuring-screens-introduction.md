---
title: AEM Screens 구성 및 배포
seo-title: 스크린 구성 및 배치
description: AEM Screens 플레이어는 Android, Chrome OS, iOS 및 Windows에서 사용할 수 있습니다. 이 페이지에서는 AEM Screens의 구성 및 배포에 대해 설명하고 플레이어 장치에 대한 h/w 선택 지침을 요약합니다.
seo-description: AEM Screens 플레이어는 Android, Chrome OS, iOS 및 Windows에서 사용할 수 있습니다. 이 페이지에서는 AEM Screens의 구성 및 배포에 대해 설명하고 플레이어 장치에 대한 h/w 선택 지침을 요약합니다.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: 83ce95e5dc530c5792ec9a00dcb758a424202a7a
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

이 페이지에서는 장치에 Screens 플레이어를 설치하고 구성하는 방법을 보여줍니다.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**중요 사항**:
>
>AEM Screens 플레이어는 CSRF(교차 사이트 요청 위조) 토큰을 사용하지 않습니다. 따라서 AEM Screens에 사용할 준비가 되도록 구성 및 AEM 서버를 구성하려면 빈 레퍼러를 허용하여 레퍼러 필터를 건너뜁니다.

## 상태 점검 프레임워크 {#health-check-framework}

사용자는 Health Check 프레임워크를 사용하여 AEM Screens 프로젝트를 실행하기 전에 두 개의 필수 구성이 설정되어 있는지 확인할 수 있습니다.

사용자는 다음 두 가지 구성 검사를 확인하여 AEM Screens 프로젝트를 실행할지, 즉 다음 두 필터의 상태를 확인할 수 있습니다.

1. **빈 레퍼러 허용**
2. **https**

다음 두 가지 필수 구성이 AEM Screens에 대해 활성화되었는지 확인하려면 아래 단계를 따르십시오.

1. Sling [Health Check로 이동합니다](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![자산](assets/health-check1.png)


2. 위에 나열된 두 **속성에 대한 유효성 검사를 실행하려면 [선택한 상태 검사** 실행]을 클릭합니다.

   두 개의 필터가 모두 활성화된 경우 **스크린 구성 상태 서비스** 에 **는** 결과 **가** 확인으로표시됩니다.

   ![자산](assets/health-check2.png)

   필터를 하나 또는 둘 다 비활성화하면 아래 그림과 같이 사용자에 대한 경고가 표시됩니다.

   다음 경고는 두 필터가 모두 비활성화되어 있는 경우 표시됩니다.
   ![자산](assets/health-check3.png)

>[!NOTE]
>
>* Apache Sling **레퍼러 필터를**&#x200B;활성화하려면 [빈 레퍼러 요청](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)허용을 참조하십시오.
>* HTTP **서비스를** 활성화하려면 [Apache Felix Jetty 기반 HTTP 서비스를 참조하십시오](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### 전제 조건 {#prerequisites}

아래 주요 사항은 AEM Screens에 사용할 수 있도록 AEM 서버와 서버를 구성하는 데 도움이 됩니다.

#### 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM 인스턴스 —> 망치 아이콘 —> 작업 **** —> **웹 콘솔** 을 통해 **Adobe Experience Manager 웹 콘솔 구성으로 이동합니다**.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성이** 열립니다. 슬링 레퍼러를 검색합니다.

   sling referrer 속성을 검색하려면 **Mac** 용 **Command+F** 를 누르고 **Windows용 Ctrl+F** 를 **누릅니다**.

1. 아래 그림과 같이 **빈** 허용 옵션을 선택합니다.

   ![이미지](assets/config/empty-ref2.png)

1. [ **저장** ]을 클릭하여 Apache Sling 레퍼러 필터 [비어 있음]을 활성화합니다.


#### Apache Felix Jetty 기반 HTTP 서비스 {#allow-apache-felix-service}

1. AEM 인스턴스 —> 망치 아이콘 —> 작업 **** —> **웹 콘솔** 을 통해 **Adobe Experience Manager 웹 콘솔 구성으로 이동합니다**.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성이** 열립니다. Apache Felix Jetty 기반의 HTTP 서비스를 검색합니다.

   이 속성을 검색하려면 **Mac** 용 Command+F **를 누르고****Windows용** Ctrl+F **를**&#x200B;누릅니다.

1. 아래 그림과 같이 **HTTP** 활성화 옵션을 선택합니다.

   ![이미지](assets/config/config-1.png)

1. [ **저장** ]을 클릭하여 *http* 서비스를 활성화합니다.

#### AEM Screens용 터치 UI 활성화 {#enable-touch-ui-for-aem-screens}

AEM Screens은 터치 UI가 필요하며 Adobe Experience Manager(AEM)의 클래식 UI에서는 작동하지 않습니다.

1. &lt; *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl으로 이동합니다.*
1. 아래 그림과 같이 **기본 작성** UI 모드가 **TOUCH로**&#x200B;설정되어 있는지 확인합니다.

또는 AuthorInstance *->* tools (icon) -> **Operations** -> **Web Console** 을 사용하여 동일한 설정을 수행하고 **WCM Authoring UI Mode Service를 검색할 수도 있습니다**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>사용자 환경 설정을 사용하여 특정 사용자에 대해 항상 클래식 UI를 활성화할 수 있습니다.

#### AEM in NOSAMPLECONCONTENT runmode {#aem-in-nosamplecontent-runmode}

프로덕션에서 AEM을 실행하면 **NOSAMPLECONTENT 런모드를** 사용합니다. X- *Frame-Options=SAMEORIGIN* 헤더(추가 응답 헤더 섹션에서)를

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

이는 AEM Screens 플레이어에서 온라인 채널을 재생하는 데 필요합니다.

#### 암호 제한 {#password-restrictions}

DeviceServiceImpl ***에***&#x200B;대한 최신 변경 사항이 있는 경우 암호 제한을 제거할 필요가 없습니다.

스크린 장치 사용자에 대한 암호를 만드는 동안 ***암호 제한을*** 사용하도록 아래 링크에서 DeviceServiceImpl을 구성할 수 있습니다.

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

아래 단계에 따라 DeviceServiceImpl을 ***구성하십시오***.

1. AEM 인스턴스 —> 망치 아이콘 —> 작업 **** —> **웹 콘솔** 을 통해 **Adobe Experience Manager 웹 콘솔 구성으로 이동합니다**.

1. **Adobe Experience Manager 웹 콘솔 구성이** 열립니다. 디바이스 *서비스*&#x200B;검색 속성을 검색하려면 macOS용 **Command+F** 를 누르고 Microsoft Windows용 **Ctrl+F** 를 누릅니다.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

AEM Screens 프로젝트에 대한 디스패처를 구성하는 방법을 알아보려면 AEM Screens 프로젝트에 [대한 발송자 구성을 참조하십시오](dispatcher-configurations-aem-screens.md).

#### Java 인코딩 {#java-encoding}

Java ***인코딩을 유니코드로*** 설정합니다. 예를 들어 *Dfile.encoding=Cp1252는* 작동하지 않습니다.

>[!NOTE]
>**추천:**
>프로덕션 환경에서 AEM Screens 서버용 HTTPS를 사용하는 것이 좋습니다.








