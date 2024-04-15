---
title: AEM SPA Editor를 사용하여 REACT 애플리케이션 임베드 및 AEM Screens Analytics와 통합
description: AEM SPA 편집기를 사용하여 REACT(또는 Angular)를 사용하여 대화형 단일 페이지 애플리케이션을 임베드하는 방법에 대해 알아봅니다.
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# AEM SPA Editor를 사용하여 REACT 애플리케이션 임베드 및 AEM Screens Analytics와 통합 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

REACT(또는 Angular)를 사용하여 대화형 단일 페이지 애플리케이션을 포함할 수 있습니다. AEM의 비즈니스 전문가가 구성한 AEM SPA 편집기를 사용하면 됩니다. 또한 대화형 애플리케이션을 오프라인 Adobe Analytics과 통합하는 방법을 배울 수도 있습니다.

## AEM SPA 편집기 사용 {#using-the-aem-spa-editor}

AEM SPA 편집기를 사용하려면 아래 단계를 따르십시오.

1. AEM SPA 편집기 저장소 복제 [https://github.com/adobe/aem-spa-project-archetype입니다.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >이 Archetype은 고유한 SPA 프로젝트의 시작점으로 최소 Adobe Experience Manager 프로젝트를 만듭니다. 이 Archetype을 사용할 때 제공해야 하는 속성을 사용하면 이 프로젝트의 모든 부분을 원하는 대로 지정할 수 있습니다.

1. AEM SPA editor archetype 프로젝트를 만들려면 추가 정보 지침을 따르십시오.

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >이 설명서는 **GroupId** 다음으로: ***com.adobe.aem.screens*** 및 **ArtifactId** 다음으로: ***내 샘플 SPA*** (기본값은 입니다.) 필요에 따라 원하는 대로 선택할 수 있습니다.

1. 프로젝트가 생성되면 원하는 IDE 또는 편집기를 사용하여 생성된 Maven 프로젝트를 가져옵니다.
1. 명령을 사용하여 로컬 AEM 인스턴스에 배포 ***mvn clean install -PatoInstallPackage***.

### REACT 앱에서 콘텐츠 편집 {#editing-content-in-the-react-app}

REACT 앱에서 콘텐츠를 편집하려면:

1. 다음으로 이동 `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` 호스트 이름, 포트 및 프로젝트 이름을 적절하게 바꿉니다.
1. Hello world 애플리케이션에 표시되는 텍스트를 편집할 수 있어야 합니다.

### AEM Screens에 대화형 REACT 앱 추가 {#adding-the-interactive-react-app-to-aem-screens}

AEM Screens에 대화형 REACT 앱을 추가하려면 아래 단계를 따르십시오.

1. AEM Screens 프로젝트를 만듭니다. 다음을 참조하십시오 [프로젝트 생성 및 관리](creating-a-screens-project.md) 을 참조하십시오.
1. 만들기 **응용 프로그램 채널** (권장 사항) (또는 1x1 템플릿, 또는 다중 영역 채널) **채널** AEM Screens 프로젝트 폴더

   >[!NOTE]
   >**시퀀스 채널** 기본적으로 경험의 대화형 속성과 충돌하는 슬라이드쇼 논리가 제공되므로 이 사용 사례에서는 권장되지 않습니다.
   >다음을 참조하십시오 [채널 만들기 및 관리](managing-channels.md) 을 참조하십시오.

1. 시퀀스 채널을 편집하고 포함된 페이지 구성 요소를 드래그 앤 드롭합니다.

   다음을 참조하십시오 [채널에 구성 요소 추가](adding-components-to-a-channel.md) 을 참조하십시오.

   >[!NOTE]
   >
   >채널을 디스플레이에 할당할 때 사용자 상호 작용 이벤트를 추가해야 합니다.

1. 클릭 **편집** 채널의 속성을 편집할 수 있도록 작업 표시줄에서 을 선택합니다.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 을(를) 끌어다 놓습니다. **포함된 페이지** 구성 요소 를 선택하거나, 응용 프로그램 채널에서 기존 구성 요소를 재사용하고, mysamplespa 응용 프로그램에서 홈 페이지를 선택합니다. 예를 들면 다음과 같습니다. ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 채널을 디스플레이에 할당합니다.

   >[!NOTE]
   >채널을 디스플레이에 할당할 때 사용자 상호 작용 이벤트를 추가해야 합니다.

1. 이 프로젝트에 대해 플레이어를 등록하고 디스플레이에 할당합니다. 이제 AEM Screens에서 실행 중인 대화형 애플리케이션을 확인할 수 있습니다.

   다음을 참조하십시오 [장치 등록](device-registration.md) 장치 등록에 대한 자세한 정보입니다.

## AEM Screens을 통해 SPA과 Adobe Analytics 통합 및 오프라인 기능 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

AEM Screens을 통해 SPA을 Adobe Analytics과 오프라인 기능을 통합하려면 아래 단계를 따르십시오.

1. AEM Screens에서 Adobe Analytics을 구성합니다.

   다음을 참조하십시오 [AEM Screens을 사용하여 Adobe Analytics 구성](configuring-adobe-analytics-aem-screens.md) AEM Screens을 사용하여 Adobe Analytics에서 시퀀싱을 수행하고 offline Adobe Analytics을 사용하여 사용자 지정 이벤트를 보내는 방법에 대한 자세한 내용을 참조하십시오.

1. 선택한 IDE/편집기(특히 텍스트 구성 요소 또는 이벤트 방출을 시작하려는 기타 구성 요소)에서 React 앱을 편집합니다.
1. 클릭 이벤트나 구성 요소에 대해 캡처하려는 다른 이벤트에서 표준 데이터 모델을 사용하여 분석 정보를 추가합니다.

   다음을 참조하십시오 [AEM Screens을 사용하여 Adobe Analytics 구성](configuring-adobe-analytics-aem-screens.md) 을 참조하십시오.

1. AEM Screens Analytics API를 호출하여 이벤트를 오프라인으로 저장하고 Adobe Analytics으로 버스트로 전송할 수 있습니다.

   예:

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >플레이어 펌웨어는 사용자가 전송하는 사용자 지정 분석 데이터에 플레이어 및 해당 런타임 환경에 대한 자세한 내용을 자동으로 추가합니다. 따라서 필요한 경우가 아니면 낮은 수준의 OS/디바이스 세부 정보를 캡처해야 할 수 있습니다. 비즈니스 분석 데이터에 집중합니다.
