---
title: 2일 지원 및 유지 관리
description: 2일차 AEM Screens 지원 및 유지 관리에 대해 알아봅니다.
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
TQID: https://experienceleague.adobe.com/IMuRCxE7v8DyK-T4Q3lehhclfgGtu0VIHyIsODOpEzA
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 140
ht-degree: 0%

---

# 2일 플랫폼 지원 및 유지 관리 {#day-two-support-maintenance}

AEM Screens이 작동하려면 프로젝트가 작동하는 여러 패키지가 필요합니다. 모든 환경에서 동일한 버전의 Adobe Experience Manager을 실행해야 합니다.

프로젝트 개발 단계 2일차에 대한 지원 및 유지 관리에 대한 지침을 따르십시오.

1. 사용 중인 Adobe Experience Manager 버전에 대해 최신 버전의 다음 패키지를 실행합니다.

   * **AEM 서비스 팩**
   * **Screens 기능 팩**
   * **AEM 누적 수정 팩**

1. 필요한 모든 개발 패키지(예: WCM 핵심 구성 요소) 또는 서드파티 툴 키트(예: SAP Hybris)를 식별합니다.

1. 로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다.

1. 모든 QA, 스테이지 및 프로덕션 서버에서 동일한 구성을 채택하도록 클라이언트에 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.
