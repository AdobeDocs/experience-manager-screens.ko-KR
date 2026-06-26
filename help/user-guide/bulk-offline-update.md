---
title: 벌크 오프라인 업데이트
description: 모든 채널을 일괄적으로 업데이트하는 방법을 알아봅니다.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
TQID: https://experienceleague.adobe.com/PxlKWiWPvedqs2krdj3UH5Chshni2X3RaTmZI1wW2-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 0%

---

# 벌크 오프라인 업데이트 {#bulk-offline-update}

>[!IMPORTANT]
>이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

이 섹션에서는 벌크 오프라인 업데이트에 대해 다음 주제를 다룹니다.

* **개요**
* **일괄 오프라인 업데이트 사용**

<!--
OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share.
-->

## 개요 {#overview}

벌크 오프라인 업데이트 를 사용하면 모든 채널을 일괄적으로 업데이트할 수 있습니다. 특정 채널로 이동해 콘텐츠를 업데이트하는 번거로움을 피할 수 있다. 대신 한 번에 하나의 특정 프로젝트에 대한 채널의 모든 콘텐츠를 업데이트할 수 있습니다.

네트워크 트래픽이 낮은 시간에 이 활동을 예약할 수도 있습니다.

>[!NOTE]
>
>벌크 오프라인 업데이트 기능은 수정된 채널만 업데이트하도록 최적화되었습니다.

## 벌크 오프라인 업데이트 사용 {#using-bulk-offline-update}

UI(사용자 인터페이스)에서 수동으로 벌크 오프라인 업데이트를 사용하거나 OSGi 서비스에서 벌크 업데이트를 예약할 수 있습니다.

### AEM Screens 사용자 인터페이스 사용 {#using-aem-screens-user-interface}

AEM Screens 프로젝트에 대해 벌크 오프라인 업데이트를 사용하려면 아래 단계를 따르십시오.

1. AEM Screens 프로젝트로 이동합니다.
1. 프로젝트를 클릭한 다음 작업 표시줄에서 **오프라인 콘텐츠 업데이트**&#x200B;를 클릭하여 채널 콘텐츠를 수동으로 업데이트할 수 있습니다.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager 웹 콘솔 구성 {#adobe-experience-manager-web-console-configuration}

AEM Screens 프로젝트에 대해 벌크 오프라인 업데이트를 사용하려면 아래 단계를 따르십시오.

1. Adobe Experience Manager 웹 콘솔 구성
1. 벌크 오프라인 업데이트 서비스를 검색합니다.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 다음 속성을 추가합니다.

   **프로젝트 경로** - AEM Screens 프로젝트의 경로를 지정합니다. 경로는 일반적으로 `/content/screens/<Name of your project>`입니다.

   *예:*, `/content/screens/we-retail`. AEM Screens 아래에서 프로젝트를 선택하여(아이콘을 클릭하지 마십시오) URL에서 이 경로를 찾을 수 있습니다.

   >[!NOTE]
   >
   >채널을 기준으로 프로젝트 경로를 지정합니다.

   **예약 빈도** - 이 서비스가 오프라인 콘텐츠를 업데이트해야 하는 시간(예: 오후 5:00 또는 오후 17:00)을 지정합니다.

1. 설정을 저장하려면 **저장**&#x200B;을 클릭하세요. 콘텐츠가 지정된 시간에 업데이트됩니다.

