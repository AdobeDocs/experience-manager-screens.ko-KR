---
title: 여행 센터 온도 활성화
description: AEM Screens을 사용하여 이 사용 사례가 Google Sheets에 채워진 값을 기반으로 여행 센터 로컬 온도 활성화의 사용을 보여 주는 방법을 알아봅니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# 여행 센터 온도 활성화 {#travel-center-temperature-activation}

다음 사용 사례에서는 Google Sheets에 채워진 값을 기반으로 하여 트래블 센터 현지 온도 활성화 를 사용하는 방법을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우, Google Sheets 의 값이 50 미만이면 뜨거운 음료가 포함된 이미지가 표시됩니다. 값이 50보다 크거나 같으면 차가운 음료가 포함된 이미지가 표시됩니다. 다른 값이 있거나 값이 전혀 없으면 플레이어가 기본 이미지를 표시합니다.

## 전제 조건 {#preconditions}

여행 센터 로컬 온도 활성화를 구현하기 전에 AEM Screens 프로젝트에서 ***데이터 저장소***, ***대상 세분화*** 및 ***채널에 대한 타깃팅 사용***&#x200B;을 설정하는 방법에 대해 알아보세요.

자세한 내용은 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md)을 참조하십시오.

## 기본 흐름 {#basic-flow}

아래 단계에 따라 Travel Center Local Temperature Activation 사용 사례를 구현합니다.

1. **Google 시트 채우기**

   1. ContextHubDemo Google 시트로 이동합니다.
   1. 온도에 대한 해당 값이 있는 **`Heading1`**&#x200B;이(가) 있는 열을 추가합니다.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 Audiences에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다(자세한 내용은 **[AEM Screens에서 ContextHub 구성](configuring-context-hub.md)** 페이지의 ***2단계: 대상 세분화 설정*** 참조).

   1. **시트 A1 1**&#x200B;을 클릭하고 **편집**&#x200B;을 클릭합니다.

   1. 비교 등록 정보를 클릭하고 구성 아이콘을 클릭합니다.
   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을(를) 클릭합니다.

   1. 드롭다운 메뉴에서 **연산자**&#x200B;을(를) **다음보다 크거나 같음**(으)로 클릭합니다

   1. **값**&#x200B;을(를) **50**(으)로 입력

   1. 마찬가지로 **시트 A1 2**&#x200B;을 선택하고 **편집**&#x200B;을 클릭합니다.

   1. **비교 속성 - 값**&#x200B;을 클릭하고 구성 아이콘을 선택합니다.
   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을(를) 클릭합니다.

   1. 드롭다운 메뉴에서 **연산자**&#x200B;을(를) **다음보다 작음**(으)로 클릭합니다.

   1. **값**&#x200B;을(를) **50**(으)로 입력

1. 이동하여 채널()을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 다음 예인 **DataDrivenWeather**&#x200B;에서는 기능을 보여 주는 데 순차적 채널이 사용됩니다.

   >[!NOTE]
   >
   >채널에는 이미 기본 이미지가 있어야 하며 [AEM Screens에서 ContextHub 구성](configuring-context-hub.md)에 설명된 대로 대상을 미리 구성해야 합니다.

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >채널 **속성** > **Personalization** 탭을 사용하는 **ContextHub** **구성**&#x200B;이(가) 이미 설정되어 있습니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 편집기에서 **타깃팅**&#x200B;을 클릭하고 드롭다운 메뉴에서 **브랜드** 및 **활동**&#x200B;을 클릭한 다음 **타깃팅 시작**&#x200B;을 클릭합니다.

   ![new_activity3](assets/new_activity3.gif)

1. **미리 보기 확인**

   1. **미리 보기를 클릭합니다.** 또한 Google 시트를 열고 값을 업데이트합니다.
   1. 값을 50 미만으로 변경합니다. 차가운 음료수의 이미지를 볼 수 있습니다. Google 시트의 값이 50 이상이면 뜨거운 음료의 이미지가 표시됩니다.

   ![결과3](assets/result3.gif)
