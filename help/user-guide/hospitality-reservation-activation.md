---
title: 숙박 예약 활성화
seo-title: Hospitality Reservation Activation
description: 다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여줍니다.
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# 숙박 예약 활성화 {#hospitality-reservation-activation}

다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우, Google Sheet에 두 개의 레스토랑 예약 비율이 채워집니다 **Restaurant1** 및 **Restaurant2**. Restaurant1과 Restaurant2의 값을 기준으로 공식이 적용되고 공식에 따라 값 1 또는 2가 **AdTarget** 열.

다음 값: **Restaurant1** > **Restaurant2**, 그런 다음 **AdTarget** 이(가) 값을 할당함 **1** 그렇지 않은 경우 **AdTarget** 이(가) 값을 할당함 **2**. 값 1은 다음을 생성합니다. *스테이크 요리* 옵션 및 값 2를 선택하면 *태국 음식* 옵션을 선택합니다.

## 전제 조건 {#preconditions}

예약 활성화 구현을 시작하기 전에 설정 방법을 알아두어야 합니다 ***데이터 저장소***, ***대상자 세분화*** 및 ***채널에 대한 타깃팅 활성화*** AEM Screens 프로젝트에서.

다음을 참조하십시오 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md) 을 참조하십시오.

## 기본 흐름 {#basic-flow}

아래 단계에 따라 AEM Screens 프로젝트에 대한 접대 예약 활성화 사용 사례를 구현합니다.

1. **Google 시트 채우기 및 수식 추가.**

   예를 들어 세 번째 열에 공식을 적용합니다 **AdTarget**&#x200B;을 참조하십시오.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **요구 사항에 따라 Audiences에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다( 참조). ***2단계: 대상자 세분화 설정*** 위치: **[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)** 페이지 를 참조하십시오.

   1. 다음 항목 선택 **시트 A1 1** 및 클릭 **편집**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 선택 **googlesheets/value/1/2** 의 드롭다운에서 **속성 이름**

   1. 다음 항목 선택 **연산자** 다음으로: **같음** 드롭다운 메뉴에서

   1. 다음을 입력합니다. **값** 다음으로: **1**

   1. 마찬가지로 **시트 A1 2** 및 클릭 **편집**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 선택 **googlesheets/value/1/2** 의 드롭다운에서 **속성 이름**

   1. 다음 항목 선택 **연산자** 다음으로: **2**

1. 이동하여 채널()을 선택하고 **편집** 작업 표시줄에서 다음 예제에서는 **DataDrivenRestaurant**&#x200B;기능을 보여주는 데 순차적 채널이 사용됩니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 다음에 설명된 대로 대상자를 사전 구성해야 합니다. [AEM Screens에서 ContextHub 구성](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >다음을 설정해야 합니다. **컨텍스트 허브** **구성** 채널 사용 **속성** > **개인화** 탭.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 선택 **타겟팅** 편집기에서 다음을 선택합니다. **브랜드** 및 **활동** 드롭다운 메뉴에서 **타깃팅 시작**.
1. **미리보기 확인**

   1. 클릭 **미리 보기.** 또한 Google Sheets 를 열고 값을 업데이트합니다.
   1. 에서 값 업데이트 **Restaurant1** 및 **Restaurant2** 열. If **Restaurant1** > **Restaurant2,** 의 이미지를 볼 수 있어야 합니다. *스테이크* 그렇지 않으면, *태국인* 화면에 음식 이미지가 표시됩니다.

   ![결과5](assets/result5.gif)
