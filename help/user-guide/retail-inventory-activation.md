---
title: 소매 재고 타깃팅된 활성화
seo-title: 소매 재고 타깃팅된 활성화
description: 이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝 셔츠에 대한 소매 재고 재고량을 보여줍니다. Google Sheets에 기록된 재고로 사용할 수 있는 운동화 수에 따라, 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 운동화)가 화면에 표시됩니다.
seo-description: 이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝 셔츠에 대한 소매 재고 재고량을 보여줍니다. Google Sheets에 기록된 재고로 사용할 수 있는 운동화 수에 따라, 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 운동화)가 화면에 표시됩니다.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: 스크린 작성
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 2%

---

# 소매 재고 타깃팅된 활성화 {#retail-inventory-targeted-activation}

다음 사용 사례에서는 Google Sheet의 값을 기반으로 세 가지 서로 다른 이미지를 보여줍니다.

## 설명 {#description}

이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝 셔츠에 대한 소매 재고 재고량을 보여줍니다. Google Sheets에 기록된 재고로 사용할 수 있는 운동화 수에 따라, 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 운동화)가 화면에 표시됩니다.

이 사용 사례의 경우 사용 가능한 스웨터 수의 가장 높은 값을 기준으로 빨간색, 녹색 또는 파란색 스웨터가 화면에 표시됩니다.

## 전제 조건 {#preconditions}

소매 인벤토리 타깃팅 활성화 구현을 시작하기 전에 AEM Screens 프로젝트에서 ***데이터 저장소***, ***대상 세그멘테이션*** 및 ***채널에 대한 타깃팅 활성화***&#x200B;를 설정하는 방법을 알고 있어야 합니다.

자세한 내용은 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md)을 참조하십시오.

## 기본 흐름 {#basic-flow}

소매 재고 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google 시트로 이동합니다.
   1. 세 개의 서로 다른 트레이닝 셔츠(빨간색, 녹색 및 파란색)에 해당 값이 있는 세 개의 열을 추가합니다.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **요구 사항에 따라 대상 구성**

   1. 대상의 세그먼트로 이동합니다( ***2단계 참조).**[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)**에서 대상 세그멘테이션 설정*** 을 참조하십시오.

   1. 세 개의 새 세그먼트 **For_Red**, **For_Green** 및 **For_Blue**&#x200B;를 추가합니다.

   1. **For_Red**&#x200B;을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   1. **비교 를 끌어다 놓습니다. 속성 - 편집기에 속성** 을 추가하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. **첫 번째 속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/2**&#x200B;을 선택합니다.

   1. 드롭다운 메뉴에서 **Operator** 를 **보다 큼** 로 선택합니다

   1. **데이터 유형**&#x200B;을 **숫자**&#x200B;로 선택합니다.

   1. **두 번째 속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/1**&#x200B;을 선택합니다.

   1. **다른 비교 를 끌어다 놓습니다. 속성 - 편집기에 속성** 을 추가하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. **첫 번째 속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/2**&#x200B;을 선택합니다.

   1. 드롭다운 메뉴에서 **Operator** 를 **보다 큼** 로 선택합니다

   1. **데이터 유형**&#x200B;을 **숫자**&#x200B;로 선택합니다.

   1. **두 번째 속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을 선택합니다.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 **For_Blue** 세그먼트에 추가하십시오.

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 ** For_Green **세그먼트에 추가합니다.

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >세그먼트 **For_Green** 및 **For_Green**&#x200B;의 경우 Google Sheet의 값에 따라 현재 첫 번째 비교만 유효하므로 편집기에서 데이터를 확인할 수 없습니다.

1. **DataDrivenRetail** 채널(시퀀스 채널)을 탐색하고 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >**속성** —> **개인화** 탭을 사용하여 **ContextHub** **구성**&#x200B;을 설정했어야 합니다.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   타깃팅 프로세스를 시작할 때 활동을 올바르게 나열하려면 **Brand** 및 **Area**&#x200B;를 모두 선택해야 합니다.

1. **기본 이미지 추가**

   1. 채널에 기본 이미지를 추가하고 **타깃팅**&#x200B;을 클릭합니다.
   1. 드롭다운 메뉴에서 **Brand** 및 **Activity**&#x200B;를 선택하고 **타깃팅 시작**&#x200B;을 클릭합니다.

   1. **타깃팅 시작**&#x200B;을 클릭합니다.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   타깃팅을 시작하기 전에 아래 그림과 같이 사이드 레일에서 **+ 경험 타깃팅 추가**&#x200B;를 클릭하여 세그먼트(**For_Green**, **For_Red** 및 **For_Blue**)를 추가해야 합니다.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 아래 표시된 것처럼 세 개의 서로 다른 시나리오 모두에 이미지를 추가합니다.

   ![retail_targeting](assets/retail_targeting.gif)

1. **미리 보기 확인**

   1. **미리 보기 를 클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 세 개의 서로 다른 열 모두에 대한 값을 변경하면 인벤토리에서 가장 높은 값에 따라 디스플레이 이미지 업데이트가 표시됩니다.
   ![retail_result](assets/retail_result.gif)
