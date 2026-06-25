---
title: 지원 모니터링
description: AEM Screens 모범 사례 안내서의 지원 모니터링에 대해 알아봅니다.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 0%

---

# 지원 모니터링 {#support-monitoring}

>[!IMPORTANT]
>이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

이 섹션에서는 디지털 사이니지 프로젝트의 장치 및 콘텐츠 예외 항목 관리와 관련된 모범 사례를 제공합니다.

지원 모니터링에는 다음이 포함됩니다.

* **장치 모니터링**
* **콘텐츠 모니터링**

## 콘텐츠 모니터링 {#content-monitoring}

콘텐츠 모니터링을 사용하면 화면에 제대로 표시되지 않는 콘텐츠와 관련된 문제를 해결할 수 있습니다.

1. 빈 화면 문제가 발생하는 경우:

   * 채널이 검정색 화면을 표시하는지 확인할 수 있도록 *미리 보기*&#x200B;를 확인하세요.
   * 해당 디스플레이에 랩톱의 *로컬 Chrome 플레이어*(확장)을 등록하고 검정색 화면이 표시되는지 확인하십시오.
   * 마우스 오른쪽 단추를 클릭하고 *적용 가능한 로그*&#x200B;를 검사하고 확인하십시오.

   또한 문제가 로컬 플레이어에서 발생하지 않고 디바이스에서만 발생하는 경우:

   * 해당 장치에서 문제가 있을 수 있는 *미디어 유형*(사용 중)을 확인하고 콘텐츠가 로컬로 다운로드되었는지 확인합니다(관리 UI 채널 캐시 지우기).
   * 빠른 문제 해결을 위해 티켓에 *장치 로그*&#x200B;를 포함하십시오.
   * AEM의 장치에서 *로그 수집*.

## 장치 모니터링 {#device-monitoring}

빈 화면 문제가 발생하는 경우 물리적 디바이스 모니터링과 관련된 디바이스 모니터링:

1. 빈 화면 문제가 발생하는 경우:

   * *디스플레이*&#x200B;의 전원이 켜져 있는지 확인하십시오.
   * *컴퓨터*&#x200B;의 전원이 켜져 있고 신호를 보내고 있는지 확인하십시오.
   * *적용 가능한 로그*&#x200B;를 마우스 오른쪽 단추로 클릭하고 검사하고 확인합니다.
