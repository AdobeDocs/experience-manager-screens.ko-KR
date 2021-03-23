---
title: AEM Screens 구성 및 배포
seo-title: 스크린 구성 및 배치
description: AEM Screens 플레이어는 Android, Chrome OS, iOS 및 Windows에서 사용할 수 있습니다. 이 페이지에서는 AEM Screens의 구성 및 배포에 대해 설명하고 플레이어 장치에 대한 h/w 선택 지침을 요약한 것입니다.
seo-description: AEM Screens 플레이어는 Android, Chrome OS, iOS 및 Windows에서 사용할 수 있습니다. 이 페이지에서는 AEM Screens의 구성 및 배포에 대해 설명하고 플레이어 장치에 대한 h/w 선택 지침을 요약한 것입니다.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: 관리자
level: 중간
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 2%

---


# AEM Screens {#configuring-and-deploying-aem-screens} 구성 및 배포

이 페이지에서는 장치에 Screens 플레이어를 설치하고 구성하는 방법을 보여줍니다.

## 서버 구성 {#server-configuration}

>[!NOTE]
>
>**중요 사항**:
>
>AEM Screens 플레이어는 CSRF(교차 사이트 요청 위조) 토큰을 사용하지 않습니다. 따라서 AEM Screens에 사용할 준비가 되도록 구성 및 AEM 서버를 만들려면 빈 레퍼러를 허용하여 레퍼러 필터를 건너뜁니다.

## 상태 확인 프레임워크 {#health-check-framework}

Health Check 프레임워크를 사용하면 AEM Screens 프로젝트를 실행하기 전에 두 개의 필수 구성이 설정되어 있는지 확인할 수 있습니다.

사용자는 다음 2개의 구성 검사를 확인하여 AEM Screens 프로젝트를 실행할지, 즉 다음 2개의 필터의 상태를 확인할 수 있습니다.

1. **빈 레퍼러 허용**
2. **https**

아래 절차에 따라 AEM Screens에 대해 두 가지 중요 구성이 활성화되었는지 확인하십시오.

1. [Adobe Experience Manager 웹 콘솔 Sling 상태 검사](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)로 이동합니다.

   ![자산](assets/health-check1.png)


2. 위에 나열된 두 속성에 대한 유효성 검사를 실행하려면 **선택한 상태 검사 실행**&#x200B;을 클릭합니다.

   두 개의 필터가 모두 활성화된 경우 **Screens 구성 상태 서비스**&#x200B;에 **Result**&#x200B;가 **OK**&#x200B;로 표시되고 두 구성이 모두 활성화되어 있습니다.

   ![자산](assets/health-check2.png)

   필터를 하나 또는 둘 다 비활성화하면 아래 그림과 같이 사용자에 대한 경고가 표시됩니다.

   다음 경고는 두 필터가 모두 비활성화되어 있는 경우에 표시됩니다.
   ![자산](assets/health-check3.png)

>[!NOTE]
>
>* **Apache Sling 레퍼러 필터**&#x200B;를 활성화하려면 [빈 레퍼러 요청 허용](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)을 참조하십시오.
>* **HTTP** 서비스를 활성화하려면 [Apache Felix Jetty 기반 HTTP 서비스](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)를 참조하십시오.


### 전제 조건 {#prerequisites}

아래 주요 사항은 AEM Screens에 사용할 수 있도록 AEM 서버를 구성하고 구성하는 데 도움이 됩니다.

#### 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM 인스턴스를 통해 **Adobe Experience Manager 웹 콘솔 구성** 망치 아이콘 —> **작업** —> **웹 콘솔**&#x200B;로 이동합니다.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성** 이 열립니다. sling 레퍼러를 검색합니다.

   sling 레퍼러 속성을 검색하려면 **Mac** Command+F **및** Windows **의** Control+F **를 누릅니다.**

1. 아래 그림과 같이 **비어 있음** 옵션을 선택합니다.

   ![이미지](assets/config/empty-ref2.png)

1. **저장**&#x200B;을 클릭하여 Apache Sling 레퍼러 필터 비어 있음 허용을 활성화합니다.


#### Apache Felix Jetty 기반 HTTP 서비스 {#allow-apache-felix-service}

1. AEM 인스턴스를 통해 **Adobe Experience Manager 웹 콘솔 구성** 망치 아이콘 —> **작업** —> **웹 콘솔**&#x200B;로 이동합니다.

   ![이미지](assets/config/empty-ref1.png)

1. **Adobe Experience Manager 웹 콘솔 구성** 이 열립니다. Apache Felix Jetty 기반의 HTTP 서비스를 검색합니다.

   이 속성을 검색하려면 **Mac**&#x200B;의 경우 **Command+F**, **Windows**&#x200B;의 경우 **Control+F**&#x200B;를 누르십시오.

1. 아래 그림과 같이 **ENABLE HTTP** 옵션을 선택합니다.

   ![이미지](assets/config/config-1.png)

1. **저장**&#x200B;을 클릭하여 *http* 서비스를 활성화합니다.

#### AEM Screens {#enable-touch-ui-for-aem-screens}에 대해 터치 UI 사용

AEM Screens을 사용하려면 터치 UI가 필요하며 Adobe Experience Manager(AEM)의 클래식 UI에서는 작동하지 않습니다.

1. *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*&#x200B;으로 이동합니다.
1. 아래 그림과 같이 **기본 작성 UI 모드**&#x200B;이 **TOUCH**&#x200B;으로 설정되어 있는지 확인합니다.

또는 AuthorInstance ** 도구(망치 아이콘) -> **작업** -> **웹 콘솔**&#x200B;을 사용하여 동일한 설정을 수행하고 **WCM 작성 UI 모드 서비스**&#x200B;를 검색할 수도 있습니다.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>사용자 환경 설정을 사용하여 특정 사용자에 대해 항상 클래식 UI를 활성화할 수 있습니다.

#### NOSAMPLECONTENT 런타임 모드의 AEM {#aem-in-nosamplecontent-runmode}

프로덕션에서 AEM을 실행하면 **NOSAMPLECONTENT** 실행 모드가 사용됩니다. *X-Frame-Options=SAMEORIGIN* 헤더(추가 응답 헤더 섹션에서)를

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

AEM Screens Player에서 온라인 채널을 재생하는 데 필요합니다.

#### 암호 제한 사항 {#password-restrictions}

***DeviceServiceImpl***&#x200B;에 대한 최신 변경 사항이 있는 경우 암호 제한을 제거할 필요가 없습니다.

스크린 장치 사용자에 대한 암호를 만드는 동안 암호 제한을 사용하도록 아래 링크에서 ***DeviceServiceImpl***&#x200B;을 구성할 수 있습니다.

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

아래 절차에 따라 ***DeviceServiceImpl***&#x200B;을 구성합니다.

1. AEM 인스턴스를 통해 **Adobe Experience Manager 웹 콘솔 구성** 망치 아이콘 —> **작업** —> **웹 콘솔**&#x200B;로 이동합니다.

1. **Adobe Experience Manager 웹 콘솔 구성** 이 열립니다. *deviceservice*&#x200B;을(를) 검색합니다. 속성을 검색하려면 macOS의 경우 **Command+F**, Microsoft Windows의 경우 **Control+F**&#x200B;를 누릅니다.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### 발송자 구성 {#dispatcher-configuration}

AEM Screens 프로젝트에 대한 디스패처를 구성하는 방법에 대해 알아보려면 [AEM Screens 프로젝트에 대한 디스패처 구성](dispatcher-configurations-aem-screens.md)을 참조하십시오.

#### Java 인코딩 {#java-encoding}

***Java 인코딩***&#x200B;을 유니코드로 설정합니다. 예를 들어 *Dfile.encoding=Cp1252*&#x200B;는 작동하지 않습니다.

>[!NOTE]
>**추천:**
>제작 시 AEM Screens Server용 HTTPS를 사용하는 것이 좋습니다.








