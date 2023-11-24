---
title: AEM Screens과 Adobe Analytics 통합
seo-title: Adobe Analytics Integration with AEM Screens
description: 이 페이지를 따라 AEM Screens과 Adobe Analytics의 획기적인 통합에 대해 알아보고 재생 증명을 제공합니다.
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 97820c602885ecf581ae1e6bada6c104aeeb4c70
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 2%

---

# AEM Screens과 Adobe Analytics 통합 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>이 AEM Screens 기능은 최소 버전의 AEM 6.4.2 기능 팩 2 또는 AEM 6.3.3 기능 팩 4를 설치한 경우에만 사용할 수 있습니다. AEM Screens 클라우드 서비스 고객의 경우 Screens Cloud에서 Adobe Analytics을 활성화하려면 Adobe 관계 관리자에게 문의하십시오.

>[!NOTE]
>
>이러한 기능 팩 중 하나에 액세스하려면 Adobe 지원 센터에 문의하여 액세스를 요청해야 합니다. 에서 AEM Screens의 최신 기능 팩을 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe ID 사용.

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **아키텍처 세부 정보**
* **속성 구성**

## 개요 {#overview}

***AEM Screens*** 는 Adobe Analytics을 활용하므로 시장에서 독보적인 성과를 창출할 수 있습니다. 크로스 채널 분석 을 통해 위치에 표시된 콘텐츠를 다른 데이터 소스와 상호 연관시킬 수 있습니다.

AEM Screens은 Adobe Analytics과의 획기적인 통합을 제공하며 재생 증명을 제공합니다.

이 섹션에서는 Adobe Analytics과 AEM Screens 프로젝트 연결과 관련된 다음 기능에 대해 설명합니다.

* 장치별 재생 증명 보고 허용
* 자산별 재생 증명 보고 허용
* 모든 플레이어 이벤트가 캡처되고 타임스탬프가 지정되었는지 확인합니다.
* 플레이가 네트워크에 연결되어 있지 않은 경우 모든 플레이어 이벤트가 로컬에 저장되도록 합니다.
* 시간 경과에 따른 재생 이벤트를 추적하는 피드백 루프를 작성할 수 있도록 합니다.
* 시스템은 콘텐츠 작성자가 정의한 성공 기준에 따라 콘텐츠 및 레이아웃을 수정할 수 있습니다

AEM Screens과 Adobe Analytics 통합은 다음을 적용합니다 *목표*:

* 디지털 사이니지 구현에서 ROI 활성화
* 향후 사용 정보 수집 및 분석을 위한 기반으로 Analytics 통합

## 아키텍처 세부 정보 {#architectural-details}

AEM Screens 고객은 표시된 시간과 기간(집계된) 동안 표시되는 콘텐츠를 이해하려고 합니다. 이는 간판 솔루션의 일반적인 기능입니다. AEM Screens은 자체 분석을 구축하는 대신 Adobe Analytics을 활용하므로, 위치에 표시된 콘텐츠를 다른 데이터 소스와 상호 연관시키는 데 도움이 되는 크로스 채널 분석이라는 시장에서 고유한 기능을 달성할 수 있습니다.

다음 아키텍처 다이어그램은 AEM Screens과 Adobe Analytics 통합에 대해 설명합니다.

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## AEM Screens에서 Adobe Analytics 활성화 {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics 설정은 OSGi 콘솔에서 구성할 수 있습니다.

다음으로 이동 **Adobe Experience Manager 웹 콘솔 구성** 아래 그림과 같이 AEM Screens용 Adobe Analytics을 구성하려면 다음을 수행하십시오.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics: 지원 흐름 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>속성을 구성하기 전에 Adobe 관계 관리자에게 문의하여 티켓을 받으십시오. **Analytics API 키** 및 **Analytics 프로젝트** AEM Screens에서 사용할 수 있습니다.

![]()

### 속성 구성 {#configuring-the-properties}

>[!CAUTION]
>
>속성을 구성하기 전에 Adobe 관계 관리자에게 문의하여 티켓을 받으십시오. **Analytics API 키** 및 **Analytics 프로젝트** AEM Screens에서 사용할 수 있습니다.

다음 표에서는 Adobe Analytics for AEM Screens 구성에 대한 설명과 함께 속성을 강조 표시합니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>플레이어에서 분석 데이터를 게시할 URL입니다. <br>
   개발/무대용</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>프로덕션용</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API 키</strong></td>
   <td>Adobe Analytics 서버 인증을 위한 API 키(계정 관리자가 제공).</td>
  </tr>
  <tr>
   <td><strong>Analytics 프로젝트</strong></td>
   <td>데이터를 수신하도록 분석에 구성된 AEM Screens 프로젝트(계정 관리자가 제공).</td>
  </tr>
  <tr>
   <td><strong>환경</strong></td>
   <td><p>스테이지 또는 프로덕션 환경(스테이지 또는 프로덕션 선택).</p></td>
  </tr>
  <tr>
   <td><strong>Analytics 전송 빈도</strong></td>
   <td>플레이어에서 분석 데이터를 전송하는 빈도(분)입니다. 기본적으로 15분으로 설정되어 있습니다.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>기본적으로 **Analytics 전송 빈도** 15분입니다.

#### AEM Screens에서 Adobe Analytics 서비스 사용 {#using-adobe-analytics-service-in-aem-screens}

이 시나리오는 펌웨어 및 기기 화면 핵심 구성 요소에 있는 분석 서비스의 REST 호출을 통해 Analytics API를 호출하여 특정 사용 사례와 관련된 이벤트를 명시적으로 만들고 보내는 동시에 사용자 지정 개발 채널에서 Analytics로 사용자 지정 메시지를 보낼 수 있는 확장성을 허용합니다.

Analytics 이벤트는 indexedDB에 오프라인으로 저장되고 나중에 청크되어 클라우드로 전송됩니다.

>[!NOTE]
>
>에 대해 자세히 알아보려면 ***순서 지정*** 및 ***이벤트에 대한 표준 데이터 모델***, 다음을 참조하십시오. **[AEM Screens용 Adobe Analytics 구성](configuring-adobe-analytics-aem-screens.md)**.
