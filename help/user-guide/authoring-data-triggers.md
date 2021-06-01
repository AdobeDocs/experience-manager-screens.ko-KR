---
title: 데이터 트리거를 사용하여 작성
seo-title: 데이터 트리거를 사용하여 작성
description: 데이터 트리거를 사용하여 작성하는 방법을 배우려면 이 페이지를 따르십시오.
feature: 스크린 작성
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 4%

---


# 데이터 트리거로 작성 {#authoring-with-data-triggers}

이 섹션에서는 채널에서 타깃팅을 활성화하는 방법을 소개합니다.

>[!IMPORTANT]
>
>AEM Screens 채널에서 데이터 트리거를 지원하는 최소 버전은 AEM 6.5.3 기능 팩 3입니다.

## 전제 조건 {#prereqs}

아래 절차에 따라 채널에서 타깃팅을 활성화하려면 먼저 AEM Screens에서 ContextHub 및 타깃팅을 이해하는 데 필요한 [AEM Screens의 구성에서 주요 용어](configuring-context-hub.md)를 학습해야 합니다.

>[!IMPORTANT]
>
>AEM Screens 채널에서 타깃팅을 활성화하기 전에 ContextHub 구성을 이해하고 설정하는 것이 좋습니다.

자세한 내용은 아래 링크를 참조하십시오.

1. **[데이터 저장소 설정](configuring-context-hub.md)**
1. **[대상 세그멘테이션 설정](configuring-context-hub.md)**

앞의 단계를 완료하면 채널에서 타깃팅을 활성화할 수 있습니다.

## 데이터 트리거로 작성 개요 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## AEM Screens 채널에서 타깃팅 활성화 {#enabling-targeting}

채널에서 타깃팅을 활성화하려면 아래 절차를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계는 AEM Screens 채널에서 만든 **DataDrivenRetail** *(시퀀스 채널)*&#x200B;을 사용하여 타깃팅을 활성화하는 방법을 보여줍니다.

1. 채널 **DataDrivenRetail**&#x200B;을 선택하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. **개인화** 탭을 선택하여 ContextHub 구성을 설정하고 ContextHub 및 세그먼트 경로를 선택합니다.

   1. **ContextHub 경로**&#x200B;를 **libs** > **설정** > **cloudsettings** > **기본** > **ContextHub 구성**&#x200B;을 선택하고 **선택**&#x200B;을 클릭합니다.

   1. **세그먼트 경로** 를 **conf** > **We.Retail** > **설정** > **wcm** > **세그먼트**&#x200B;로 선택하고 **선택**&#x200B;을 클릭합니다.

   1. **저장 후 닫기**&#x200B;를 클릭합니다.
   >[!NOTE]
   >
   >Context Hub 구성 및 세그먼트를 처음 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets** > **채널**&#x200B;에서 **DataDrivenRetail**&#x200B;을 탐색하고 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 채널 편집기에서 자산을 끌어다 놓습니다.

   >[!NOTE]
   >
   >모든 사항을 올바르게 설정한 경우 아래 그림과 같이 편집기에서 드롭다운에 **타깃팅** 옵션이 표시됩니다.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. **타깃팅**&#x200B;을 클릭합니다.

1. 드롭다운 메뉴에서 **Brand** 및 **Activity**&#x200B;를 선택하고 **타깃팅 시작**&#x200B;을 클릭합니다.

### 추가 정보:사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트용으로 ContextHub를 구성한 후에는 다른 사용 사례 를 따라 데이터가 트리거된 자산이 다양한 산업에서 어떻게 중요한 역할을 수행하는지 이해할 수 있습니다.

1. **[소매 재고 타깃팅된 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**
