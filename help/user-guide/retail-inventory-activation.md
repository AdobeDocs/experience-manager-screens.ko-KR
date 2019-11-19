---
title: 소매 인벤토리 대상 활성화
seo-title: 소매 인벤토리 대상 활성화
description: 이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝셔츠에 대한 소매 재고 재고 재고가 표시됩니다. Google Sheets에 기록되어 있는 Stock에서 사용 가능한 스웨터 수에 따라 화면에 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 스웨터)가 표시됩니다.
seo-description: 이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝셔츠에 대한 소매 재고 재고 재고가 표시됩니다. Google Sheets에 기록되어 있는 Stock에서 사용 가능한 스웨터 수에 따라 화면에 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 스웨터)가 표시됩니다.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 소매 인벤토리 대상 활성화 {#retail-inventory-targeted-activation}

다음 사용 사례에서는 Google Sheet의 값을 기준으로 세 개의 다른 이미지를 보여 줍니다.

## 설명 {#description}

이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝셔츠에 대한 소매 재고 재고 재고가 표시됩니다. Google Sheets에 기록되어 있는 Stock에서 사용 가능한 스웨터 수에 따라 화면에 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 스웨터)가 표시됩니다.

이 사용 사례의 경우 사용 가능한 스웨터 수의 최고 값에 따라 화면에 빨간색, 녹색 또는 파란색 스웨터가 표시됩니다.

## 전제 조건 {#preconditions}

소매 인벤토리 타깃팅 활성화를 구현하기 전에 AEM Screens 프로젝트에서 ***데이터***&#x200B;스토어, 대상 세그멘테이션 ***및*** 채널에 대한 타깃팅 ***활성화를*** 설정하는 방법에 대해배워야 합니다.

자세한 내용은 [AEM Screens의](configuring-context-hub.md) ContextHub 구성을 참조하십시오.

## 기본 흐름 {#basic-flow}

소매 인벤토리 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google Sheet로 이동합니다.
   1. 세 개의 서로 다른 스웨터에 해당하는 값과 함께 세 개의 열(빨강, 녹색 및 파랑)을 추가합니다.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **요구 사항에 따라 대상 구성**

   1. 대상의 세그먼트로 이동합니다(단계 ***2 참조:자세한 내용은 AEM Screens*** 에서 **[ContextHub를](configuring-context-hub.md)** 구성하는대상 세그멘테이션 설정을 참조하십시오.)

   1. 세 개의 새 세그먼트 For_ **Red**, **For_Green**&#x200B;및 **For_Blue를**&#x200B;추가합니다.

   1. For_ **Red를** 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   1. 비교를 드래그하여 **놓습니다.속성 -** 편집기에 대한 속성 및 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 첫 **번째 속성 이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 큼 **로 연산자를 선택합니다.

   1. 데이터 **유형을** **번호로 선택**

   1. 두 **번째 속성 이름의 드롭다운에서 워크시트/값/1/1** **을 선택합니다.**

   1. 드래그 앤 드롭 **또 다른 비교:속성 - 속성 **을 편집기에 입력하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 첫 **번째 속성 이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 큼 **로 연산자를 선택합니다.

   1. 데이터 **유형을** **번호로 선택**

   1. 두 **번째 속성 이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 **For_Blue** 세그먼트에 추가합니다.

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 ** For_Green **segment에 추가합니다.

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >For_Green 및 **For_Green** 세그먼트의 경우 ****&#x200B;현재 Google Sheet의 값에 따라 첫 번째 비교만 유효하므로 편집기에서 데이터를 확인할 수 없습니다.

1. DataDrivenRetail **채널** (시퀀스 채널)을 찾아 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   타깃팅 프로세스를 시작할 때 **활동이** 제대로 나열되도록 하려면 브랜드와 영역을 **** 모두 선택해야 합니다.

1. **기본 이미지 추가**

   1. 채널에 기본 이미지를 추가하고 타깃팅을 **클릭합니다**.
   1. 드롭다운 **메뉴에서** 브랜드와 **활동을** 선택하고 타깃팅 **시작을**&#x200B;클릭합니다.

   1. **타깃팅 시작**&#x200B;을 클릭합니다.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   타게팅을 시작하기 전에 아래 그림과 같이 사이드 레일에서 경험 타게팅 추가&#x200B;******(For_Green**, For_Red 및 **For_Blue**)를 클릭하여 세그먼트를 추가해야 합니다 **** .

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 아래 표시된 대로 세 가지 다른 영역에 이미지를 추가합니다.

   ![retail_targeting](assets/retail_targeting.gif)

1. **미리 보기 확인**

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 세 개의 서로 다른 열 모두에 대한 값을 변경하면 재고 중 가장 높은 값에 따라 표시 이미지가 업데이트됩니다.
   ![retail_result](assets/retail_result.gif)

