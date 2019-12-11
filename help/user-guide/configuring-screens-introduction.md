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
source-git-commit: 323e2df2419cc65de7bfe88648ffd1dbd3a91aec

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

이 페이지에서는 장치에 Screens 플레이어를 설치하고 구성하는 방법을 보여줍니다.

## 서버 구성 {#server-configuration}

>[!NOTE]
>
>**중요 사항**:
>
>AEM Screens 플레이어는 CSRF(교차 사이트 요청 위조) 토큰을 사용하지 않습니다. 따라서 AEM Screens에 사용할 수 있도록 AEM 서버를 구성하고 준비하려면 빈 레퍼러를 허용하여 레퍼러 필터를 건너뜁니다.

### 전제 조건 {#prerequisites}

아래 주요 사항은 AEM Screens에 사용할 수 있도록 AEM 서버를 구성하고 구성하는 데 도움이 됩니다.

#### 빈 레퍼러 요청 허용 {#allow-empty-referrer-requests}

1. AEM **인스턴스 —&gt; 망치 아이콘 —&gt; 작업** —&gt; 웹 **콘솔을** 통해 Adobe Experience Manager 웹 콘솔 구성으로 **이동합니다**.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Adobe Experience Manager 웹 콘솔 구성이** 열립니다. 슬링 레퍼러를 검색합니다.

   Mac용 Command+F를 누르고 **Windows용** Ctrl+F **를**********&#x200B;누르면 Windows가검색됩니다.

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. 아래 그림과 같이 **빈 **허용 옵션을 선택합니다.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Apache **Sling** Referrer Filter Allow Empty를 활성화하려면 저장을 클릭합니다.

#### AEM Screens용 터치 UI 활성화 {#enable-touch-ui-for-aem-screens}

AEM Screens에는 터치 UI가 필요하며 AEM(Adobe Experience Manager)의 클래식 UI에서는 작동하지 않습니다.

1. &lt;yourAuthorInstance&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl으로 *이동합니다.*
1. 아래 그림과 같이 기본 **작성** UI 모드가 **TOUCH로**&#x200B;설정되어 있는지 확인합니다.

또는 *&lt;yourAuthorInstance&gt;*-&gt;*tools (* 해머아이콘 -&gt; **작업** -&gt; **Web ConsoleWeb Console** **** UI 작성 UI 모드 서비스 작성에 대한 검색 및 검색을 사용하여 동일한 설정을 수행할 수도 있습니다.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>사용자 환경 설정을 사용하여 특정 사용자에 대해 항상 클래식 UI를 활성화할 수 있습니다.

#### NOSAMPLECONTENT 런타임 모드의 AEM {#aem-in-nosamplecontent-runmode}

프로덕션에서 AEM을 실행하면 NOSAMPLECONTENT **런모드가** 사용됩니다. Removethe *X-Frame-Options=SAMEORIGIN* 헤더(추가 응답 헤더 섹션)를

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

AEM Screens 플레이어에서 온라인 채널을 재생하려면 필요합니다.

#### 암호 제한 {#password-restrictions}

DeviceServiceImpl ***에 대한***&#x200B;최신 변경 사항을 사용하면 암호 제한을 제거할 필요가 없습니다.

화면 장치 ***사용자에 대한*** 암호를 만드는 동안 암호 제한을 사용하도록 아래 링크에서 DeviceServiceImpl을 구성할 수 있습니다.

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

아래 절차에 따라 DeviceServiceImpl을 ***구성하십시오***.

1. AEM **인스턴스 —&gt; 망치 아이콘 —&gt; 작업** —&gt; 웹 **콘솔을** 통해 Adobe Experience Manager 웹 콘솔 구성으로 **이동합니다**.

1. **Adobe Experience Manager 웹 콘솔 구성 **이 열립니다. 디바이스 서비스 검색 속성을 검색하려면 Command+F **for** Mac **및** Ctrl+F **를******&#x200B;눌러 Windows를 선택합니다.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

AEM Screens 프로젝트에 대한 디스패처를 구성하는 방법에 대한 자세한 내용은 AEM [Screens 프로젝트에](dispatcher-configurations-aem-screens.md)대한 디스패처 구성을 참조하십시오.

#### Java 인코딩 {#java-encoding}

Java ***인코딩을*** 유니코드로 설정합니다. 예를 들어 Dfile. *encoding=Cp1252는* 작동하지 않습니다.

>[!NOTE]
>
>**추천:**
>
>제작 시 AEM Screens Server용 HTTPS를 사용하는 것이 좋습니다.

