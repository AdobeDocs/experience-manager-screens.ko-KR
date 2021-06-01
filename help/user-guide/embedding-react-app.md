---
title: AEM SPA 편집기를 사용하여 REACT 애플리케이션 포함 및 AEM Screens Analytics와 통합
seo-title: AEM SPA 편집기를 사용하여 REACT 애플리케이션 포함 및 AEM Screens Analytics와 통합
description: AEM에서 비즈니스 전문가가 구성할 수 있는 AEM SPA 편집기를 사용하여 REACT(또는 Angular)을 사용하여 대화형 단일 페이지 애플리케이션을 포함하는 방법과 대화형 애플리케이션을 오프라인 Adobe Analytics과 통합하는 방법을 배우려면 이 페이지를 따르십시오.
seo-description: AEM에서 비즈니스 전문가가 구성할 수 있는 AEM SPA 편집기를 사용하여 REACT(또는 Angular)을 사용하여 대화형 단일 페이지 애플리케이션을 포함하는 방법과 대화형 애플리케이션을 오프라인 Adobe Analytics과 통합하는 방법을 배우려면 이 페이지를 따르십시오.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: 화면 개발
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---


# AEM SPA 편집기를 사용하여 REACT 애플리케이션을 포함 및 AEM Screens Analytics와 통합 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

이 섹션에서는 AEM에서 비즈니스 전문가가 구성할 수 있는 AEM SPA 편집기를 사용하여 REACT(또는 Angular)을 사용하여 대화형 단일 페이지 애플리케이션을 포함하는 방법과 대화형 애플리케이션을 오프라인 Adobe Analytics과 통합하는 방법에 대해 설명합니다.

## AEM SPA 편집기 사용 {#using-the-aem-spa-editor}

아래 절차에 따라 AEM SPA 편집기를 사용하십시오.

1. [https://github.com/adobe/aem-spa-project-archetype에서 AEM SPA 편집기 보고서를 복제합니다.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >이 원형 은 고유한 SPA 프로젝트의 시작점으로 최소한의 Adobe Experience Manager 프로젝트를 만듭니다. 이 원형 사용 시 제공해야 하는 속성을 사용하여 이 프로젝트의 모든 부분에서 원하는 이름으로 지정할 수 있습니다.

1. readme 지침에 따라 AEM SPA 편집기 원형 프로젝트를 생성합니다.

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
   >**GroupId** 를 ***com.adobe.aem.screens***(으)로 사용하고 **ArtifactId** 를 ***My Sample SPA***(기본값)로 사용합니다. 필요에 따라 원하는 대로 선택할 수 있습니다.

1. 프로젝트가 만들어지면 선택한 IDE 또는 편집기를 사용하고 생성된 Maven 프로젝트를 가져옵니다.
1. ***mvn clean install -AutoInstallPackage*** 명령을 사용하여 로컬 AEM 인스턴스에 배포합니다.

### REACT 앱에서 컨텐츠 편집 {#editing-content-in-the-react-app}

REACT 앱에서 컨텐츠를 편집하려면:

1. `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` 로 이동합니다(해당하는 호스트 이름, 포트 및 프로젝트 이름을 바꿉니다.).
1. Hello world 응용 프로그램에서 표시되는 텍스트를 편집할 수 있어야 합니다.

### AEM Screens {#adding-the-interactive-react-app-to-aem-screens}에 대화형 REACT 앱 추가

아래 절차에 따라 AEM Screens에 대화형 REACT 앱을 추가하십시오.

1. 새 AEM Screens 프로젝트를 만듭니다. 자세한 내용은 [프로젝트 만들기 및 관리](creating-a-screens-project.md)를 참조하십시오.

   >[!NOTE]
   >
   >스크린 프로젝트의 **채널** 폴더에서 채널을 만드는 동안 **시퀀스 채널**&#x200B;을 만듭니다.
   >
   >
   >자세한 내용은 [채널 만들기 및 관리](managing-channels.md)를 참조하십시오.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. 시퀀스 채널을 편집하고 포함된 페이지 구성 요소를 드래그하여 놓습니다.

   자세한 내용은 [채널](adding-components-to-a-channel.md)에 구성 요소 추가 를 참조하십시오.

   >[!NOTE]
   >
   >채널을 디스플레이에 할당할 때 사용자 상호 작용 이벤트를 추가해야 합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 시퀀스 채널의 속성을 편집합니다.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. **Embedded Page** 구성 요소를 끌어다 놓고 mymsamplespa 응용 프로그램 아래에서 홈 페이지를 선택합니다(예: ***/content/mysamplespa/en/home***).

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 이 프로젝트에 대해 플레이어를 등록하면 이제 AEM Screens에서 실행 중인 대화형 애플리케이션을 볼 수 있습니다.

   장치 등록에 대한 자세한 내용은 [장치 등록](device-registration.md) 을 참조하십시오.

## AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}을 통해 SPA과 Adobe Analytics의 오프라인 기능 통합

AEM Screens을 통해 SPA을 Adobe Analytics과 오프라인 기능과 통합하려면 아래 단계를 따르십시오.

1. AEM Screens에서 Adobe Analytics을 구성합니다.

   AEM Screens을 사용하여 Adobe Analytics에서 시퀀스를 수행하고 오프라인 Adobe Analytics을 사용하여 사용자 지정 이벤트를 전송하는 방법에 대해 알아보려면 [AEM Screens을 사용하여 Adobe Analytics 구성](configuring-adobe-analytics-aem-screens.md) 을 참조하십시오.

1. 원하는 IDE/편집기에서 React 앱을 편집합니다(특히 이벤트를 시작하려는 텍스트 구성 요소 또는 기타 구성 요소).
1. 구성 요소에 대해 캡처할 클릭 이벤트 또는 기타 이벤트에서 표준 데이터 모델을 사용하여 분석 정보를 추가합니다.

   자세한 내용은 [AEM Screens](configuring-adobe-analytics-aem-screens.md)에서 Adobe Analytics 구성 을 참조하십시오.

1. AEM Screens Analytics API를 호출하여 이벤트를 오프라인으로 저장하고 Adobe Analytics으로 버스트합니다.

   예,

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
   >플레이어 펌웨어는 사용자가 전송하는 사용자 지정 분석 데이터에 플레이어 및 런타임 환경에 대한 자세한 정보를 자동으로 추가합니다. 따라서 반드시 필요한 경우가 아니면 낮은 수준의 OS/장치 세부 사항을 캡처할 필요가 없습니다. 비즈니스 분석 데이터에 집중하기만 하면 됩니다.

