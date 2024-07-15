---
title: '[!UICONTROL AEM Screens]용 환경'
description: AEM Screens 프로젝트 환경에 대해 자세히 알아보십시오.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 환경 {#environments}

*개발* 및 *배포*&#x200B;에 대해 클라이언트가 가지고 있고 사용자가 사용해야 하는 AEM 환경을 미리 결정하십시오.

>[!NOTE]
>
>AEM Screens이 작동하려면 프로젝트가 작동하는 여러 패키지가 필요합니다. 모든 환경에서 동일한 버전의 Adobe Experience Manager을 실행해야 합니다.

AEM Screens 프로젝트에 대한 환경을 설정하려면 아래 지침을 따르십시오.

1. 사용 중인 Adobe Experience Manager 버전에 대해 최신 버전의 다음 패키지를 실행합니다.

   * **AEM 서비스 팩**
   * **Screens 기능 팩**
   * **AEM 누적 수정 팩**

1. 필요한 모든 개발 패키지(예: WCM 핵심 구성 요소) 또는 서드파티 툴 키트(예: SAP Hybris)를 식별합니다.

1. 로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다.

1. 모든 QA, 스테이지 및 프로덕션 서버에서 동일한 구성을 채택하도록 클라이언트에 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.
