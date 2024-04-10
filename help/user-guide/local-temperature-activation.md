---
title: 여행 센터 온도 활성화
seo-title: Travel Center Temperature Activation
description: 다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 하여 트래블 센터 현지 온도 활성화 를 사용하는 방법을 보여줍니다.
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 여행 센터 온도 활성화 {#travel-center-temperature-activation}

다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 하여 트래블 센터 현지 온도 활성화 를 사용하는 방법을 보여줍니다.

## 설명 {#description}

이 사용 사례에서 Google Sheets의 값이 50보다 작은 경우 뜨거운 음료가 포함된 이미지가 표시되고, 값이 50보다 크거나 같은 경우 차가운 음료가 포함된 이미지가 표시됩니다. 값이 없거나 다른 경우에는 플레이어에 기본 이미지가 표시됩니다.

## 전제 조건 {#preconditions}

여행 센터 현지 온도 활성화 구현을 시작하기 전에 설정 방법을 배워야 합니다 ***데이터 저장소***, ***대상자 세분화*** 및 ***채널에 대한 타깃팅 활성화*** AEM Screens 프로젝트에서.

다음을 참조하십시오 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md) 을 참조하십시오.

## 기본 흐름 {#basic-flow}

아래 단계에 따라 Travel Center Local Temperature Activation 사용 사례를 구현합니다.

1. **Google 시트 채우기**

   1. ContextHubDemo Google 시트로 이동합니다.
   1. 다음을 사용하여 열 추가 **제목1** (온도에 대한 해당 값 포함)

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 Audiences에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다( 참조). ***2단계: 대상자 세분화 설정*** 위치: **[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)** 페이지 를 참조하십시오.

   1. 다음 항목 선택 **시트 A1 1** 및 클릭 **편집**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 선택 **구글시트/값/1/0** 의 드롭다운에서 **속성 이름**

   1. 다음 항목 선택 **연산자** 다음으로: **크거나 같음** 드롭다운 메뉴에서

   1. 다음을 입력합니다. **값** 다음으로: **50**

   1. 마찬가지로 **시트 A1 2** 및 클릭 **편집**.

   1. 다음 항목 선택 **비교 속성 - 값** 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 선택 **구글시트/값/1/0** 의 드롭다운에서 **속성 이름**

   1. 다음 항목 선택 **연산자** 다음으로: **보다 작음** 드롭다운 메뉴에서

   1. 다음을 입력합니다. **값** 다음으로: **50**

1. 이동하여 채널()을 선택하고 **편집** 작업 표시줄에서 다음 예제에서는 **DataDrivenWeather**&#x200B;기능을 보여주는 데 순차적 채널이 사용됩니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 다음에 설명된 대로 대상자를 사전 구성해야 합니다. [AEM Screens에서 ContextHub 구성](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >다음을 설정해야 합니다. **컨텍스트 허브** **구성** 채널 사용 **속성** > **개인화** 탭.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 선택 **타겟팅** 편집기에서 다음을 선택합니다. **브랜드** 및 **활동** 드롭다운 메뉴에서 **타깃팅 시작**.

   ![new_activity3](assets/new_activity3.gif)

1. **미리보기 확인**

   1. 클릭 **미리 보기.** 또한 Google 시트를 열고 값을 업데이트합니다.
   1. 50 미만으로 값을 변경하면 여름 음료의 이미지를 볼 수 있습니다. Google 시트의 값이 50 이상인 경우 뜨거운 음료의 이미지를 볼 수 있어야 합니다.

   ![result3](assets/result3.gif)
