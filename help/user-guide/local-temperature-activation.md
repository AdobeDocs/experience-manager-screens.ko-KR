---
title: 여행 센터 온도 활성화
seo-title: 여행 센터 온도 활성화
description: 다음 사용 사례는 Google Sheet에서 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
seo-description: 다음 사용 사례는 Google Sheet에서 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: 스크린 작성
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 여행 센터 온도 활성화 {#travel-center-temperature-activation}

다음 사용 사례는 Google Sheet에서 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우, Google Sheet의 값이 50보다 작으면 핫드링크가 있는 이미지가 표시되고, 값이 50보다 크거나 같으면 콜드 드링크가 있는 이미지가 표시됩니다. 다른 값 또는 값이 없는 경우 플레이어에 기본 이미지가 표시됩니다.

## 전제 조건 {#preconditions}

여행 센터 로컬 온도 활성화 구현을 시작하기 전에 AEM Screens 프로젝트에서 ***데이터 저장소***, ***대상 세그멘테이션*** 및 ***채널 타깃팅 활성화***&#x200B;를 설정하는 방법을 알고 있어야 합니다.

자세한 내용은 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md)을 참조하십시오.

## 기본 흐름 {#basic-flow}

여행 센터 로컬 온도 활성화 사용 사례를 구현하려면 아래 단계를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google 시트로 이동합니다.
   1. **Heading1**&#x200B;이 있는 열을 온도 값으로 추가합니다.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다( ***2단계 참조).**[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)**에서 대상 세그멘테이션 설정*** 을 참조하십시오.

   1. **시트 A1**&#x200B;를 선택하고 **편집**&#x200B;을 클릭합니다.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을 선택합니다.

   1. 드롭다운 메뉴에서 **Operator** 를 **보다 크거나 같은**&#x200B;로 선택합니다

   1. **값**&#x200B;을 **50**&#x200B;으로 입력합니다.

   1. 마찬가지로 **시트 A1 2**&#x200B;를 선택하고 **편집**&#x200B;을 클릭합니다.

   1. **비교 속성 - 값**&#x200B;을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을 선택합니다.

   1. 드롭다운 메뉴에서 **Operator** 를 **보다 작음**&#x200B;으로 선택합니다

   1. **값**&#x200B;을 **50**&#x200B;으로 입력합니다.

1. 채널()으로 이동하여 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 다음 예제에서 **DataDrivenWeather** 순차적 채널은 기능을 보여주는 데 사용됩니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 대상은 AEM Screens에서 [ContextHub 구성](configuring-context-hub.md)에 설명된 대로 미리 구성해야 합니다.

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >**속성** —> **개인화** 탭을 사용하여 **ContextHub** **구성**&#x200B;을 설정했어야 합니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 편집기에서 **타깃팅**&#x200B;을 선택하고 드롭다운 메뉴에서 **브랜드** 및 **활동**&#x200B;을 선택하고 **타깃팅 시작**&#x200B;을 클릭합니다.

   ![new_activity3](assets/new_activity3.gif)

1. **미리 보기 확인**

   1. **미리 보기 를 클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 값을 50세 미만으로 변경하세요. 여름 음료 이미지를 볼 수 있을 거예요. Google Sheet의 값이 50 이상이면 핫 음료 이미지를 볼 수 있습니다.
   ![result3](assets/result3.gif)
