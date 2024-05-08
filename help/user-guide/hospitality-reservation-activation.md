---
title: 숙박 예약 활성화
description: 이 사용 사례에서 Google Sheets에 채워진 값을 기반으로 한 접대 예약 활성화의 사용을 보여 주는 방법을 알아봅니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 숙박 예약 활성화 {#hospitality-reservation-activation}

다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우 Google Sheet에 두 개의 레스토랑 예약 비율이 채워집니다 **`Restaurant1`** 및 **`Restaurant2`**. 수식은 다음 값을 기반으로 적용됩니다. `Restaurant1` 및 `Restaurant2` 그리고 수식을 기반으로 값 1 또는 2가 **AdTarget** 열.

다음 값: **`Restaurant1`** > **`Restaurant2`**, 그런 다음 **AdTarget** 이(가) 값을 할당함 **1** 그렇지 않은 경우 **AdTarget** 이(가) 값을 할당함 **2**. 값 1은 다음을 생성합니다. *스테이크 요리* option과 value 2를 사용하면 결과가 표시됩니다. *태국 음식* 옵션을 선택합니다.

## 전제 조건 {#preconditions}

예약 활성화 구현을 시작하기 전에 설정 방법을 알아보십시오 ***데이터 저장소***, ***대상자 세분화*** 및 ***채널에 대한 타깃팅 활성화*** AEM Screens 프로젝트에서.

다음을 참조하십시오 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md) 을 참조하십시오.

## 기본 흐름 {#basic-flow}

아래 사용 사례 단계에 따라 AEM Screens 프로젝트에 대한 접대 예약 활성화를 구현합니다.

1. **Google 시트 채우기 및 공식 추가**.

   예를 들어 세 번째 열에 공식을 적용합니다 **AdTarget**&#x200B;을 참조하십시오.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **요구 사항에 따라 Audiences에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다( 참조). ***2단계: 대상자 세분화 설정*** 위치: **[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)** 페이지 를 참조하십시오.
   1. 다음을 클릭합니다. **시트 A1 1** 및 클릭 **편집**.
   1. 비교 속성을 클릭하고 **구성** 아이콘.
   1. 클릭 **googlesheets/value/1/2** 의 드롭다운에서 **속성 이름**.
   1. 다음을 클릭합니다. **연산자** 다음으로: **같음** 드롭다운 메뉴에서 을(를) 선택합니다.
   1. 다음을 입력합니다. **값** 다음으로: **1**.
   1. 마찬가지로 **시트 A1 2** 및 클릭 **편집**.
   1. 비교 속성을 클릭하고 **구성** 아이콘.
   1. 클릭 **googlesheets/value/1/2** 의 드롭다운에서 **속성 이름**.
   1. 다음을 클릭합니다. **연산자** 다음으로: **2**.

1. 내 채널()로 이동하여 클릭한 다음 **편집** 작업 표시줄에서 다음 예제에서는 **DataDrivenRestaurant**&#x200B;기능을 보여주는 데 순차적 채널이 사용됩니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 다음에 설명된 대로 대상자를 사전 구성해야 합니다. [AEM Screens에서 ContextHub 구성](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >다음을 설정해야 합니다. **컨텍스트 허브** **구성** 채널 사용 **속성** > **개인화** 탭.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 클릭 **타겟팅** 편집기에서 **브랜드** 및 **활동** 드롭다운 메뉴에서 **타깃팅 시작**.
1. **미리보기 확인**

   1. 클릭 **미리 보기.** 또한 Google Sheets 를 열고 값을 업데이트합니다.
   1. 에서 값 업데이트 **`Restaurant1`** 및 **`Restaurant2`** 열. If **`Restaurant1`** > **`Restaurant2`,** 의 이미지를 볼 수 있어야 합니다. *스테이크* 그렇지 않으면, *태국인* 화면에 음식 이미지가 표시됩니다.

   ![결과5](assets/result5.gif)
