---
title: 데이터 트리거를 사용하여 작성
description: AEM Screens 채널에서 데이터 트리거를 사용하여 작성하는 방법에 대해 자세히 알아보십시오.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 1%

---

# 데이터 트리거를 사용하여 작성 {#authoring-with-data-triggers}

이 섹션에서는 채널에서 타겟팅을 활성화하는 방법을 중점적으로 다룹니다.

>[!IMPORTANT]
>
>AEM Screens 채널에서 데이터 트리거를 지원하는 최소 버전은 AEM 6.5.3 기능 팩 3입니다.

## 사전 요구 사항 {#prereqs}

아래 단계에 따라 채널에서 타깃팅을 활성화하기 전에 ContextHub 및 AEM Screens의 타깃팅을 이해하는 데 필요한 [AEM Screens에서 구성](configuring-context-hub.md)의 주요 용어를 알아보십시오.

>[!IMPORTANT]
>
>AEM Screens 채널에서 타깃팅을 활성화하기 전에 ContextHub 구성을 이해하고 설정하는 것이 좋습니다.

자세한 내용은 아래 링크를 참조하십시오.

1. **[데이터 저장소 설정](configuring-context-hub.md)**
1. **[대상자 세분화 설정](configuring-context-hub.md)**

이전 단계를 완료하면 채널에서 타겟팅을 활성화할 수 있습니다.

## 데이터 트리거를 사용한 작성 개요 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## AEM Screens 채널에서 타깃팅 활성화 {#enabling-targeting}

채널에서 타겟팅을 활성화하려면 아래 단계를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계에서는 AEM Screens 채널에서 만든 **DataDrivenRetail** *(시퀀스 채널)*&#x200B;을(를) 사용하여 타깃팅을 활성화하는 방법을 보여 줍니다.

1. **DataDrivenRetail** 채널을 클릭하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. ContextHub 구성을 설정하고 ContextHub 및 세그먼트 경로를 클릭할 수 있도록 **Personalization** 탭을 클릭합니다.

   1. **libs** > **설정** > **cloudsettings** > **기본** > **ContextHub 구성**(으)로 **ContextHub 경로**&#x200B;를 클릭하고 **클릭**&#x200B;을(를) 클릭합니다.

   1. **세그먼트 경로**&#x200B;을(를) **conf** > **`We.Retail`** > **설정** > **wcm** > **세그먼트**(으)로 클릭하고 **클릭**&#x200B;합니다.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >처음에 ContextHub 구성 및 세그먼트를 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets** > **채널**&#x200B;에서 **DataDrivenRetail**&#x200B;을(를) 탐색하고 클릭한 다음 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 채널 편집기에서 에셋을 끌어다 놓습니다.

   >[!NOTE]
   >
   >모든 것을 올바르게 설정한 경우 아래 그림과 같이 편집기의 드롭다운에 **타깃팅** 옵션이 표시됩니다.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. **타깃팅**&#x200B;을 클릭합니다.

1. 드롭다운 메뉴에서 **브랜드** 및 **활동**&#x200B;을 클릭하고 **타깃팅 시작**&#x200B;을 클릭합니다.

### 자세히 알아보기: 사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후 다양한 사용 사례에 따라 데이터가 트리거된 에셋이 다양한 산업에서 중요한 역할을 하는 방법을 이해할 수 있습니다.

1. **[소매 인벤토리 대상 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[접대 예약 활성화](hospitality-reservation-activation.md)**
