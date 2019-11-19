---
title: 출장 센터 온도 활성화
seo-title: 출장 센터 온도 활성화
description: 다음 사용 사례는 Google Sheets에 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
seo-description: 다음 사용 사례는 Google Sheets에 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 출장 센터 온도 활성화 {#travel-center-temperature-activation}

다음 사용 사례는 Google Sheets에 채워진 값을 기반으로 여행 센터 로컬 온도 활성화 사용을 보여줍니다.

## 설명 {#description}

이 사용 사례의 경우 Google Sheets의 값이 50보다 작으면 따뜻한 음료가 포함된 이미지가 표시되고 값이 50보다 크거나 같으면 차가운 음료가 포함된 이미지가 표시됩니다. 다른 값 또는 값이 없는 경우 플레이어에 기본 이미지가 표시됩니다.

## 전제 조건 {#preconditions}

여행 센터 로컬 온도 활성화 구현을 시작하기 전에 AEM Screens 프로젝트에서 ***데이터***&#x200B;스토어, 대상 세그멘테이션 ***및*** 채널에 ***대한 타깃팅*** 활성화를설정하는 방법에 대해배워야 합니다.

자세한 내용은 [AEM Screens의](configuring-context-hub.md) ContextHub 구성을 참조하십시오.

## 기본 흐름 {#basic-flow}

이동 센터 로컬 온도 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google Sheet로 이동합니다.
   1. 온도 값이 **있는 Heading1** 열을 추가합니다.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다(단계 ***2 참조:자세한 내용은 AEM Screens*** 에서 **[ContextHub를](configuring-context-hub.md)** 구성하는대상 세그멘테이션 설정을 참조하십시오.)

   1. 시트 A1 **을** 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 크거나 같음 **연산자를 선택합니다.

   1. 값을 **50으로** 입력합니다 ****

   1. 마찬가지로* Sheets A1 2 **를 선택하고 편집을 **클릭합니다**.

   1. 비교 **속성 - 값을** 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**

   1. 드롭다운 **메뉴에서** **less-than **으로 연산자를 선택합니다.

   1. 값을 **50으로** 입력합니다 ****

1. 채널()을 탐색하고 선택하고 작업 **표시줄에서 편집을** 클릭합니다. 다음 예제에서는 **순차적 채널인 DataDrivenWeather**&#x200B;를 사용하여 기능을 표시합니다.

   >[!NOTE]
   >
   >채널에 이미 기본 이미지가 있어야 하며 대상은 AEM Screens에서 ContextHub 구성에 설명된 대로 미리 [구성해야 합니다](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 편집기에서 ******브랜드를** 선택하고 **드롭다운** 메뉴에서 **활동과**&#x200B;타깃팅 시작을클릭합니다.

   ![new_activity3](assets/new_activity3.gif)

1. **미리 보기 확인**

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 값을 50세 미만으로 변경하면 여름 음료 이미지를 볼 수 있습니다. Google Sheet의 값이 50 이상인 경우, 핫 드링크의 이미지를 볼 수 있어야 합니다.
   ![result3](assets/result3.gif)

