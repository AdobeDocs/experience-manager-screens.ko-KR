---
title: 여행 센터 온도 활성화
seo-title: 여행 센터 온도 활성화
description: 다음 사용 사례는 Google Sheet에서 입력한 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
seo-description: 다음 사용 사례는 Google Sheet에서 입력한 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# 여행 센터 온도 활성화 {#travel-center-temperature-activation}

다음 사용 사례는 Google Sheet에서 입력한 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우, Google Sheet의 값이 50보다 낮으면 따뜻한 음료를 포함하는 이미지가 표시되고, 값이 50보다 크거나 같은 경우 차가운 음료를 포함하는 이미지가 표시됩니다. 다른 값 또는 값이 없는 경우 플레이어에 기본 이미지가 표시됩니다.

## 전제 조건 {#preconditions}

여행 센터 로컬 온도 활성화 구현을 시작하기 전에 AEM Screens 프로젝트에서 ***데이터 스토어***, ***대상 세그멘테이션*** 및 채널 ***에 대한 타깃팅*** 활성화를 설정하는 방법을배워야 합니다.

자세한 내용은 AEM Screens [의 ContextHub 구성을](configuring-context-hub.md) 참조하십시오.

## 기본 흐름 {#basic-flow}

이동 센터 지역 온도 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google Sheet로 이동합니다.
   1. 온도 값이 **Heading1인** 열을 추가합니다.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다( ***단계 2 참조:자세한 내용은 AEM Screens*** 페이지에서 ContextHub **[구성에서 대상 세그멘테이션](configuring-context-hub.md)** 설정)을 참조하십시오.

   1. 시트 **A1 1을** 선택하고 **편집을 클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **선택**

   1. 드롭다운 메뉴에서 **연산자****를** 보다 크거나같게 선택합니다

   1. 값을 **50** 으로 **입력합니다.**

   1. 마찬가지로 **시트 A1 2를** 선택하고 **편집을 클릭합니다**.

   1. 비교 **속성 - 값을** 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **선택**

   1. 드롭다운 메뉴에서 **보다** **작음** 연산자를 선택합니다.

   1. 값을 **50** 으로 **입력합니다.**

1. 채널()을 탐색하여 선택하고 작업 표시줄에서 **편집을** 클릭합니다. 다음 예제에서 **DataDrivenWeather는**&#x200B;순차적 채널을 사용하여 기능을 표시합니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 대상은 AEM Screens의 ContextHub [구성에 설명된 대로 미리 구성해야 합니다](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >채널 속성 —> Personalization **탭을** 사용하여 **ContextHub** **** **구성** 을설정해야합니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 편집기에서 ******** **브랜드** 및 **활동**&#x200B;을선택하고 드롭다운 메뉴에서 타깃팅 시작을클릭합니다.

   ![new_activity3](assets/new_activity3.gif)

1. **미리 보기 확인**

   1. 미리 **보기를 클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 값을 50세 미만으로 변경하면 여름 음료 이미지를 볼 수 있습니다. Google Sheet의 값이 50보다 큰 경우 따뜻한 음료 이미지를 볼 수 있어야 합니다.

   ![result3](assets/result3.gif)

