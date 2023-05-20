---
title: 환경 [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: 이 페이지에서는 AEM Screens 프로젝트 환경에 대해 설명합니다.
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# 환경 {#environments}

클라이언트가 보유하고 있으며 이 두 가지 모두를 사용할 AEM 환경을 미리 결정합니다. *개발* 및 *배포*.

>[!NOTE]
>
>AEM Screens이 작동하려면 여러 패키지가 필요합니다. 모든 환경에서 동일한 버전의 Adobe Experience Manager을 실행해야 합니다.

AEM Screens 프로젝트에 대한 환경을 설정하려면 아래 지침을 따르십시오.

1. 사용 중인 Adobe Experience Manager 버전에 대해 최신 버전의 다음 패키지를 실행합니다.

   * **AEM Service Pack**
   * **화면 기능 팩**
   * **AEM 누적 수정 팩**

1. 필요한 모든 개발 패키지(예: WCM 핵심 구성 요소) 또는 서드파티 툴 키트(예: SAP Hybris)를 식별합니다.

1. 로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다.

1. 모든 QA, 스테이지 및 프로덕션 서버에서 동일한 구성을 채택하도록 클라이언트에 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.
