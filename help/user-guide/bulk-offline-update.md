---
title: 대량 오프라인 업데이트
seo-title: 대량 오프라인 업데이트
description: 모든 채널을 일괄적으로 업데이트하는 방법을 배우려면 이 페이지를 따르십시오.
seo-description: 모든 채널을 일괄적으로 업데이트하는 방법을 배우려면 이 페이지를 따르십시오.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: 스크린 작성
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 11%

---


# 벌크 오프라인 업데이트 {#bulk-offline-update}

이 섹션에서는 벌크 오프라인 업데이트에 대해 다음 주제를 다룹니다.

* **개요**
* **벌크 오프라인 업데이트 사용**

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.3 기능 팩 3 또는 AEM 6.4 Screens 기능 팩 1을 설치한 경우에만 사용할 수 있습니다.
>
>이 Feature Pack에 액세스하려면 Adobe 지원 센터에 연락하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.

## 개요 {#overview}

벌크 오프라인 업데이트에서는 모든 채널을 일괄적으로 업데이트할 수 있습니다. 특정 채널로 이동하고 컨텐츠를 업데이트하는 번거로움이 발생하지 않습니다. 대신 한 번에 하나의 특정 프로젝트에 대한 채널의 모든 콘텐츠를 업데이트할 수 있습니다.

네트워크 트래픽이 낮은 시간에 대해 이 활동을 예약할 수도 있습니다.

>[!NOTE]
>
>벌크 오프라인 업데이트 기능은 수정된 채널만 업데이트하도록 최적화되었습니다.

## 대량 오프라인 업데이트 사용 {#using-bulk-offline-update}

UI(사용자 인터페이스)에서 수동으로 벌크 오프라인 업데이트를 사용하거나 OSGi 서비스에서 벌크 업데이트를 예약할 수 있습니다.

### AEM Screens 사용자 인터페이스 사용 {#using-aem-screens-user-interface}

AEM Screens 프로젝트에 대해 벌크 오프라인 업데이트를 사용하려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트로 이동합니다.
1. 프로젝트를 선택하고 작업 표시줄에서 **오프라인 컨텐츠 업데이트**&#x200B;를 클릭하여 채널 컨텐츠를 수동으로 업데이트합니다.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager 웹 콘솔 구성 {#adobe-experience-manager-web-console-configuration}

AEM Screens 프로젝트에 대해 벌크 오프라인 업데이트를 사용하려면 아래 절차를 따르십시오.

1. Adobe Experience Manager 웹 콘솔 구성.
1. 대량 오프라인 업데이트 서비스를 검색합니다.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 다음 속성을 추가합니다.

   **프로젝트** 경로: AEM Screens 프로젝트의 경로를 지정합니다. 경로는 일반적으로 `/content/screens/<Name of your project>`입니다.

   *예*, `/content/screens/we-retail`. AEM Screens 아래에서 프로젝트를 선택하여 URL에서 이 경로를 찾을 수 있습니다(아이콘을 클릭하지 않음).

   >[!NOTE]
   >
   >채널에 상대적인 프로젝트 경로를 지정합니다.

   **일정** 빈도이 서비스가 오프라인 콘텐츠를 업데이트할 시간(예: 오후 5시 또는 17시)을 지정합니다.

1. 설정을 저장하려면 **저장**&#x200B;을 클릭하십시오. 그러면 지정된 시간에 컨텐츠가 업데이트됩니다.

