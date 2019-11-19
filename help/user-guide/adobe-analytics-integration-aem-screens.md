---
title: AEM Screens와 Adobe Analytics 통합
seo-title: AEM Screens와 Adobe Analytics 통합
description: AEM Screens와 Adobe Analytics의 기본 통합에 대해 알아보고 재생 증거를 제공하려면 이 페이지를 따르십시오.
seo-description: AEM Screens와 Adobe Analytics의 기본 통합에 대해 알아보고 재생 증거를 제공하려면 이 페이지를 따르십시오.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens와 Adobe Analytics 통합 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.4.2 기능 팩 2 및 AEM 6.3.3 기능 팩 4를 설치한 경우에만 사용할 수 있습니다.

>이러한 기능 팩을 이용하려면 Adobe 지원 센터에 문의하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.
>
이 섹션에서는 다음과 같은 주제를 다룹니다.

* **개요**
* **건축 세부 사항**
* **속성 구성**

## 개요 {#overview}

***AEM*** Screens는 Adobe Analytics를 활용하므로 시장에서 고유한 것을 얻을 수 있습니다. 크로스 채널 분석은 위치에 표시된 컨텐츠를 다른 데이터 소스와 상호 연관시킬 수 있습니다.

AEM Screens는 Adobe Analytics와 기본적으로 통합되어 있으며 재생 증거를 제공합니다.

이 섹션에서는 AEM Screens 프로젝트를 Adobe Analytics와 연결하는 것과 관련된 다음 기능에 대해 설명합니다.

* 장치별 재생 결과 보고 허용
* 자산별 재생 보고 증명 허용
* 모든 플레이어 이벤트가 캡처되고 타임스탬프가 지정되었는지 확인
* 재생이 네트워크에 연결되지 않은 경우 모든 플레이어 이벤트가 로컬에 저장되도록 합니다.
* 시간 경과에 따른 재생 이벤트를 추적하는 피드백 루프를 만들 수 있습니다.
* 시스템에서 컨텐츠 작성자가 정의한 성공 기준을 기반으로 컨텐츠 및 레이아웃을 수정할 수 있습니다.

AEM Screens와 Adobe Analytics 통합은 다음과 같은 *목표를*&#x200B;적용합니다.

* 디지털 서명 구현의 ROI 활성화
* Analytics를 향후 사용 정보 수집 및 분석을 위한 기반

## 건축 세부 사항 {#architectural-details}

AEM Screens 고객은 표시되는 컨텐츠의 시간 및 기간(집계됨)을 파악하려고 합니다. 사이니지 솔루션의 일반적인 기능입니다. AEM Screens는 자체 분석을 작성하는 대신 Adobe Analytics를 활용하고, 이를 통해 Adobe는 시장에서 고유한 것을 얻을 수 있습니다. 크로스 채널 분석은 위치에 표시된 컨텐츠를 다른 데이터 소스와 상호 연관시킬 수 있습니다.

다음 아키텍처 다이어그램은 AEM Screens와 Adobe Analytics 통합에 대해 설명합니다.

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## AEM Screens에서 Adobe Analytics 활성화 {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics 설정은 OSGi 콘솔에서 구성할 수 있습니다.

아래 그림과 **같이 Adobe Experience Manager** 웹 콘솔 구성으로 이동하여 AEM Screens용 Adobe Analytics를 구성합니다.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 스크린 분석:활성화 흐름 {#screens-analytics-enablement-flow}

>[!CAUTION]
속성을 구성하려면 먼저 Adobe 관계 관리자에게 문의하여 AEM Screens에서 사용할 Analytics API 키 및 **Analytics** 프로젝트를 **얻기** 위한 티켓을 받으십시오.

![]()

### 속성 구성 {#configuring-the-properties}

>[!CAUTION]
속성을 구성하려면 먼저 Adobe 관계 관리자에게 문의하여 AEM Screens에서 사용할 Analytics API 키 및 **Analytics** 프로젝트를 **얻기** 위한 티켓을 받으십시오.

다음 표에서는 AEM Screens용 Adobe Analytics 구성에 대한 설명과 함께 속성을 강조 표시합니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>분석 URL</strong></td>
   <td>플레이어에서 분석 데이터를 게시하기 위한 URL<br /> </td>
  </tr>
  <tr>
   <td><strong>Analytics API 키</strong></td>
   <td>Adobe Analytics 서버에 인증하기 위한 API 키(계정 관리자에서 제공)</td>
  </tr>
  <tr>
   <td><strong>분석 프로젝트</strong></td>
   <td>데이터를 수신하도록 분석에 구성된 AEM Screens 프로젝트(계정 관리자가 제공)</td>
  </tr>
  <tr>
   <td><strong>환경</strong></td>
   <td><p>스테이지 또는 프로덕션 환경.</p> <p><em>개발/스테이지의</em> 경우 - https://cc-api-data-stage.adobe.io/ingest/제작<br /> <em>용</em> - https://cc-api-data.adobe.io/ingest/</p> </td>
  </tr>
  <tr>
   <td><strong>Analytics 전송 빈도</strong></td>
   <td>플레이어에서 분석 데이터를 보내는 빈도(분)입니다. 기본적으로 15분으로 설정됩니다.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
기본적으로 **Analytics 전송 빈도 **는 15분입니다.

#### AEM Screens에서 Adobe Analytics Service 사용 {#using-adobe-analytics-service-in-aem-screens}

이 시나리오는 펌웨어 및 계측 화면 코어 구성 요소의 분석 서비스에서 REST 호출을 통해 Analytics API를 호출하여 특정 사용 사례와 관련된 이벤트를 명시적으로 만들고 전송하면서 사용자 지정 메시지를 사용자 지정 개발 채널에서 Analytics로 보낼 수 있는 확장성을 허용합니다.

Analytics 이벤트는 indexedDB 파섹

>[!NOTE]
이벤트에 대한 시퀀스 ***및 표준*** 데이터 ***모델에 대한 자세한***&#x200B;내용은 AEM Screens **[에 대한 Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**&#x200B;구성을 참조하십시오.

