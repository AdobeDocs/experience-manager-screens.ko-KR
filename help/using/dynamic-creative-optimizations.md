---
title: 데이터 트리거
description: AEM Screens의 데이터 트리거에 대해 알아봅니다.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 0%

---

# Dynamic Creative 최적화 {#dynamic-creative}

>[!IMPORTANT]
>이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

>[!NOTE]
>
>이 활동의 일반적인 이해 당사자는 AEM 구현자입니다.

**Dynamic Creative Optimization** 또는 DCO를 사용하여 지정된 시간과 지정된 사용자에 대해 지정된 위치의 고유한 상황을 반영하는 디지털 서명 경험을 만듭니다.

이러한 사용을 콘텐츠의 클라이언트측 병합이라고도 합니다.

이유는 각 플레이어 장치 또는 끝점이 데이터 세트를 사용하여 다양한 다양한 요소를 기반으로 자동으로 재생할 최상의 콘텐츠를 결정할 수 있도록 하기 위한 것입니다.

이 기능을 사용하면 콘텐츠 작성 시 사용자가 지속적으로 개입할 필요가 없습니다. 또한 네트워크 운영을 위한 총소유비용(TCO)을 절감하고 디지털 환경을 더욱 관련성 있고 상황에 맞는 방식으로, 더욱 효과적으로 만들 수 있습니다.

해당 예는 다음과 같습니다.

* 기능 제품의 현재 재고 수준 사용
* 외부 온도 또는 날씨
* 로컬 미디어 광고 캠페인 유무
* 웹 트래픽과 고객이 제품을 검사하기 위해 픽업하는 것과 같은 로컬 이벤트

이러한 모든 예 및 그 이상을 사용하여 더 높은 수준의 컨텍스트 및 개인화를 제공할 수 있습니다.

DCO를 포함하는 시각적 머천다이징 전략을 사용하면 네트워크 시청률을 크게 높일 수 있습니다.

데이터 트리거에는 두 가지 기본 유형이 있습니다.

* **로컬 데이터 트리거**: 이러한 데이터 트리거는 장치에서 로컬입니다. 예를 들어, 화면을 터치하면 로컬 데이터 에셋 또는 채널 전환을 트리거하는 센서가 활성화됩니다.
* **원격 데이터 트리거**: 여기에는 웹 서비스 API에서 반환된 값을 기반으로 하는 데이터 트리거된 채널 스위치 또는 에셋 스위치가 포함됩니다.

