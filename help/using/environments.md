---
title: '[!UICONTROL AEM Screens]에 대한 환경'
seo-title: '[!UICONTROL AEM Screens]에 대한 환경'
description: 이 페이지에서는 AEM Screens 프로젝트의 환경에 대해 설명합니다.
seo-description: 이 페이지에서는 AEM Screens 프로젝트의 환경을 강조 표시합니다.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---


# 환경 {#environments}

*development* 및 *deployment*&#x200B;에 대해 클라이언트가 사용하고 싶은 AEM 환경을 미리 결정합니다.

>[!NOTE]
>
>AEM Screens에서는 프로젝트가 작동하려면 여러 패키지가 필요합니다. 모든 환경에서 동일한 버전의 Adobe Experience Manager을 실행해야 합니다.

AEM Screens 프로젝트에 대한 환경을 설정하려면 아래 지침을 따르십시오.

1. 사용 중인 Adobe Experience Manager 버전에 대해 다음 패키지의 최신 버전을 실행합니다.

   * **AEM 서비스 팩**
   * **스크린 기능 팩**
   * **AEM Cumulative 수정 팩**

1. 필요한 모든 개발 패키지(예: WCM 핵심 구성 요소) 또는 타사 도구 키트(예: SAP Hybris)를 식별합니다.

1. 로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다.

1. 클라이언트가 모든 QA, Stage 및 Production 서버에서 동일한 구성을 채택하도록 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.
