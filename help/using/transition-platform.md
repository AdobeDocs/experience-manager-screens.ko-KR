---
title: 플랫폼으로 전환
description: AEM Screens의 플랫폼으로의 전환에 대해 알아봅니다.
exl-id: e69f504f-d20b-4cdb-b567-5c9c1df4d331
TQID: https://experienceleague.adobe.com/xefeUV4bgG-I7zVOGcAnNkcdx1Y-XQfmAr2bFT5nFN0
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 0%

---

# 플랫폼으로 전환 {#transition-platform}

>[!IMPORTANT]
>이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

>[!NOTE]
>
>이 활동의 일반적인 이해 당사자는 AEM 구현자입니다.

프로젝트가 전략적 비전에서 와이어프레임 현실로 진행되었으므로 배포할 수 있는 AEM에서 실제 Screens 프로젝트 생성을 준비해야 합니다.

이 프로젝트에는 프로토타이핑 단계에서 정의된 느슨하게 정의된 요구 사항에 대한 플랫폼별 구성의 매핑이 포함됩니다.

예를 들면 다음과 같은 사용 방법 및 시기가 있습니다.

* 콘텐츠 그룹화를 만들기 위한 **경험 조각**.
* 텍스트 변형을 만들 **콘텐츠 조각**.
* 외부 데이터 저장소, 대화형 환경을 위한 SPA를 만들기 위한 **Context Hub**.
* 네트워크 경고에 대한 **OSGi 서비스**.
* Creative Cloud 소싱에 대한 **자산 링크**.
* 자산 할당을 위한 **네트워크 폴더**.
* 실시간 데이터에 대한 **텍스트 오버레이**.
* 디스플레이/채널 그룹화를 위한 **일정**.
* 자동화된 콘텐츠 편집을 위한 **워크플로**.

이 단계에서는 주의가 필요한 모든 필수 작업 및 활동을 검토하고 적절하게 문서화하여 배포 단계에서 할당된 작업을 올바르게 추적할 수 있도록 합니다.

또한 이 단계에서 자동화를 위한 가능한 후보로 사전 정의된 모든 활동을 검토하십시오.

