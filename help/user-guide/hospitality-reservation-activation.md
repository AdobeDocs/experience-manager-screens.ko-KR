---
title: 숙박 예약 활성화
seo-title: 숙박 예약 활성화
description: 다음 사용 사례에서는 Google Sheets에서 입력한 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여 줍니다.
seo-description: 다음 사용 사례에서는 Google Sheets에서 입력한 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여 줍니다.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# 숙박 예약 활성화 {#hospitality-reservation-activation}

다음 사용 사례에서는 Google Sheets에서 입력한 값을 기반으로 병원 예약 활성화를 사용하는 방법을 보여 줍니다.

## 설명 {#description}

이 사용 사례의 경우, Google Sheet는 두 개의 레스토랑 Restaurant Restaurant1 **과 Restaurant2** 중 예약 비율이 **채워집니다**. 수식은 Restaurant1 및 Restaurant2의 값을 기반으로 적용되며 공식을 기준으로 값 1 또는 2가 AdTarget 열에 **할당됩니다** .

Restaurant1 **&gt;** Restaurant2 **의**&#x200B;값을 지정하면 **AdTaget이** Value **1에** 할당되고, 그 외의 경우에는 Value AdTarget **** ****&#x200B;이 지정된 값 20입니다. 값 1은 *스테이크 음식* 옵션을 생성하고 값 2는 *디스플레이 화면에 태국 음식* 옵션을 표시합니다.

## 전제 조건 {#preconditions}

예약 활성화를 구현하기 전에 AEM Screens 프로젝트에서 데이터 스토어, ***대상***&#x200B;세그멘테이션 ***및*** 채널에 ***대한 타깃팅*** 활성화를설정하는 방법에 대해 알아두어야 합니다.

자세한 내용은 [AEM Screens의](configuring-context-hub.md) ContextHub 구성을 참조하십시오.

## 기본 흐름 {#basic-flow}

아래 절차에 따라 AEM Screens 프로젝트에 대한 숙박 예약 활성화 사용 사례를 구현하십시오.

1. **Google Sheet를 채우고 공식을 추가합니다.**

   예를 들어 아래 그림과 같이 세 번째 열 AdTarget **에**&#x200B;공식을 적용합니다.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다(단계 ***2 참조:자세한 내용은 AEM Screens*** 에서 **[ContextHub를](configuring-context-hub.md)** 구성하는대상 세그멘테이션 설정을 참조하십시오.)

   1. 시트 A1 **을** 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서 연산자를** **동일하게** 선택합니다.

   1. 값을 **1** **로 입력합니다.**

   1. 마찬가지로 시트 A1 **2를** 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 연산자를 **2** 로 선택합니다 ****

1. 채널()을 탐색하고 선택하고 작업 **표시줄에서 편집을** 클릭합니다. 다음 예제에서는 **DataDrivenRestaurant**&#x200B;순차적 채널을 사용하여 기능을 표시합니다.

   >[!NOTE]
   >
   >채널에 이미 기본 이미지가 있어야 하며 대상은 AEM Screens에서 ContextHub 구성에 설명된 대로 미리 [구성해야 합니다](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 편집기에서 ******브랜드를** 선택하고 **드롭다운** 메뉴에서 **활동과**&#x200B;타깃팅 시작을클릭합니다.
1. **미리 보기 확인**

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheets를 열고 값을 업데이트합니다.
   1. Restaurant1 및 **Restaurant2** 열의 값을 **업데이트합니다** . Restaurant1 **** &gt; **Restaurant2** 를 *사용하면 스테이크* 푸드의 이미지를 볼 수 *있고, 그렇지 않으면 태국 음식* 이미지가 화면에 표시됩니다.
   ![result5](assets/result5.gif)

