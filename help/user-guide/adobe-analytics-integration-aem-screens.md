---
title: AEM Screens과 Adobe Analytics 통합
seo-title: AEM Screens과 Adobe Analytics 통합
description: 이 페이지를 따라 Adobe Analytics과 AEM Screens을 통합한 기본 제공 방법에 대해 알아보고 재생 증명을 제공합니다.
seo-description: 이 페이지를 따라 Adobe Analytics과 AEM Screens을 통합한 기본 제공 방법에 대해 알아보고 재생 증명을 제공합니다.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: 화면 관리
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 2%

---


# AEM Screens과 Adobe Analytics 통합 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.4.2 기능 팩 2 또는 AEM 6.3.3 기능 팩 4의 최소 버전을 설치한 경우에만 사용할 수 있습니다.

>[!NOTE]
>
>이러한 기능 팩에 액세스하려면 Adobe 지원에 문의하고 액세스 권한을 요청해야 합니다. Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens에 대한 최신 기능 팩을 다운로드할 수 있습니다.

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **아키텍처 세부 사항**
* **속성 구성**

## 개요 {#overview}

***AEM*** 는 Adobe Analytics을 스크린으로 분류하고 이를 통해 위치에 표시된 컨텐츠를 다른 데이터 소스와 상호 연관시킬 수 있도록 지원하는 크로스 채널 분석 등 시장에서 고유한 사항을 달성할 수 있습니다.

AEM Screens은 Adobe Analytics과 즉시 통합된 기능을 제공하며 재생 증명을 제공합니다.

이 섹션에서는 AEM Screens 프로젝트를 Adobe Analytics과 연결하는 데 관련된 다음 기능에 대해 설명합니다.

* 장치별 재생 보고 증명을 허용합니다
* 자산별 재생 보고 증명을 허용합니다
* 모든 플레이어 이벤트가 캡처되고 타임스탬프가 지정되는지 확인합니다
* 재생이 네트워크에 연결되어 있지 않은 경우 모든 플레이어 이벤트가 로컬로 저장되도록 합니다
* 시간 경과에 따라 재생 이벤트를 추적하는 피드백 루프를 만들 수 있습니다
* 시스템에서 컨텐츠 작성자가 정의한 성공 기준에 따라 컨텐츠 및 레이아웃을 수정할 수 있습니다

Adobe Analytics과 AEM Screens 통합은 따라서 다음 *목표*&#x200B;를 적용합니다.

* 디지털 서명 구현에서 ROI 활성화
* 나중에 사용 정보를 수집하고 분석할 수 있도록 Analytics를 기초 자료로 통합합니다

## 아키텍처 세부 사항 {#architectural-details}

AEM Screens 고객은 표시되는 컨텐츠가 언제 그리고 얼마나 오래(집계됨) 동안 이해하려고 합니다. 이것은 사이니지 솔루션의 일반적인 기능입니다. AEM Screens은 자체 분석을 구축하는 대신 Adobe Analytics을 활용하며, 이를 통해 시장에 고유한 사항(위치에 표시된 컨텐츠를 다른 데이터 소스와 상호 연관시킬 수 있도록 지원하는 크로스 채널 분석)을 달성할 수 있습니다.

다음 아키텍처 다이어그램은 AEM Screens과 Adobe Analytics 통합을 설명합니다.

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## AEM Screens에서 Adobe Analytics 활성화 {#enabling-adobe-analytics-in-aem-screens}

OSGi 콘솔에서 Adobe Analytics 설정을 구성할 수 있습니다.

아래 그림과 같이 **Adobe Experience Manager Web Console 구성**&#x200B;으로 이동하여 AEM Screens용 Adobe Analytics을 구성합니다.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics:사용 흐름 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>속성을 구성하기 전에 Adobe 관계 관리자에게 연락하여 **Analytics API 키** 및 **Analytics Project**&#x200B;를 얻기 위한 티켓을 만드십시오.

![]()

### 속성 구성 {#configuring-the-properties}

>[!CAUTION]
>
>속성을 구성하기 전에 Adobe 관계 관리자에게 연락하여 **Analytics API 키** 및 **Analytics Project**&#x200B;를 얻기 위한 티켓을 만드십시오.

다음 표에서는 Adobe Analytics for AEM Screens 구성을 위한 설명으로 속성을 강조 표시합니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>플레이어에서 분석 데이터를 게시할 URL입니다. <br>
   개발/스테이지의 경우</em>  - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>프로덕션</em>  - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API 키</strong></td>
   <td>Adobe Analytics 서버(계정 관리자에서 제공)를 인증하기 위한 API 키.</td>
  </tr>
  <tr>
   <td><strong>Analytics 프로젝트</strong></td>
   <td>AEM Screens 프로젝트가 데이터를 수신하도록 analytics에 구성되었습니다(계정 관리자에서 제공).</td>
  </tr>
  <tr>
   <td><strong>환경</strong></td>
   <td><p>스테이지 또는 프로덕션 환경(스테이지 또는 프로덕션 선택)</p></td>
  </tr>
  <tr>
   <td><strong>Analytics 전송 빈도</strong></td>
   <td>플레이어에서 분석 데이터를 전송하는 빈도(분)입니다. 기본적으로 15분으로 설정되어 있습니다.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>기본적으로 **Analytics 전송 빈도**&#x200B;는 15분입니다.

#### AEM Screens에서 Adobe Analytics 서비스 사용 {#using-adobe-analytics-service-in-aem-screens}

이 시나리오는 사용자 지정 개발 채널에서 Analytics로 사용자 지정 메시지를 보낼 수 있는 확장성을 허용하면서 펌웨어 및 기기 화면 코어 구성 요소의 analytics 서비스에서 REST 호출을 통해 Analytics API를 호출하여 특정 사용 사례별 이벤트를 명시적으로 만들고 전송하도록 합니다.

Analytics 이벤트는 indexedDB에 오프라인으로 저장되고 나중에 청크되어 클라우드로 전송됩니다.

>[!NOTE]
>
>***Sequencing*** 및 ***Standard Data Model for Events***&#x200B;에 대한 자세한 내용은 **[Adobe Analytics for AEM Screens 구성](configuring-adobe-analytics-aem-screens.md)**&#x200B;을 참조하십시오.

