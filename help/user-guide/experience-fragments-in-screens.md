---
title: 경험 조각 사용
seo-title: 경험 조각 사용
description: 'AEM Screens에서 경험 구성요소 사용에 대해 알려면 이 페이지를 따르십시오. '
seo-description: 'AEM Screens에서 경험 구성요소 사용에 대해 알려면 이 페이지를 따르십시오. '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: 스크린 작성, 경험 조각
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 12%

---


# 경험 조각 사용 {#using-experience-fragments}

이 페이지에서는 다음 주제를 다룹니다.

* **개요**
* **AEM Screens에서의 경험 조각 사용**
* **페이지에 변경 사항 전파**

## 개요 {#overview}

***경험 조각***&#x200B;은 페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹입니다. 경험 조각은 단락 시스템 내에 어떤 것이든 포함할 수 있는 하나 이상의 구성 요소 등, 구성 요소를 포함할 수 있으며, 이러한 구성 요소는 완전한 경험에 참조되거나 세 번째 종단점에 의해 요청됩니다.


## AEM Screens에서의 경험 조각 사용 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>다음 예제에서는 **We.Retail**&#x200B;을 **Sites** 페이지에서 AEM Screens 프로젝트로 경험 조각을 활용하는 데모 프로젝트로 사용합니다.

예를 들어, 다음 워크플로우는 Sites에서 We.Retail의 경험 구성요소를 사용하는 방법을 보여줍니다. 웹 페이지를 선택하고 프로젝트 중 하나에서 AEM Screens 채널에서 해당 컨텐츠를 활용할 수 있습니다.

### 전제 조건 {#pre-requisites}

**채널을 사용하여 데모 프로젝트 만들기**

***프로젝트 만들기***

1. **스크린 프로젝트 만들기**&#x200B;를 클릭하여 새 프로젝트를 만듭니다.
1. 제목을 **DemoProject**&#x200B;로 입력합니다.
1. **저장**&#x200B;을 클릭합니다.

**DemoProject**&#x200B;가 AEM Screens에 추가됩니다.

***채널 생성***

1. 만든 **DemoProject** 로 이동하고 **채널** 폴더를 선택합니다.

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭하여 마법사를 엽니다.
1. 마법사에서 **시퀀스 채널** 템플릿을 선택하고 **다음**&#x200B;을 클릭합니다.

1. **제목** 을 **TestChannel** 로 입력하고 **만들기**&#x200B;를 클릭합니다.

**TestChannel**&#x200B;이 **DemoProject**&#x200B;에 추가됩니다.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### 경험 조각 생성 {#creating-an-experience-fragment}

아래 절차에 따라 **We.Retail**&#x200B;에서 **DemoProject**&#x200B;의 **TestChannel**&#x200B;에 콘텐츠를 활용하십시오.

1. **We.Retail에서 사이트 페이지로 이동합니다**

   1. 사이트 로 이동하고 **We.Retail** -> **미국** -> **영어** -> **장비**&#x200B;를 선택하고 이 페이지를 선택하여 스크린 채널에 대한 경험 조각으로 사용합니다.

   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 스크린 채널의 경험 조각으로 사용할 페이지를 엽니다.

1. **컨텐츠 다시 사용**

   1. 채널에 포함할 조각을 선택합니다.
   1. 오른쪽에서 마지막 아이콘을 클릭하여 **경험 조각**&#x200B;으로 변환 대화 상자를 엽니다.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **경험 조각 만들기**

   1. **작업**&#x200B;을 **새 경험 조각 만들기**&#x200B;로 선택합니다.

   1. **상위 경로**&#x200B;를 선택합니다.
   1. **템플릿**&#x200B;을 선택합니다. 여기서 **경험 조각 - 화면 변형** 템플릿을 선택합니다( `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens` 필드의 값).

   1. **조각 제목**&#x200B;을 **ScreensFragment**&#x200B;로 입력합니다.

   1. 확인 표시를 클릭하여 새 경험 조각 만들기를 완료합니다.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   참고:더 쉬운 옵션을 선택하려면 필드 오른쪽의 확인 표시를 클릭하여 선택 대화 상자를 엽니다.

1. **경험 조각의 Live Copy 생성**

   1. AEM 홈 페이지로 이동합니다.
   1. **경험 구성요소**&#x200B;를 선택하고 **ScreensFragment**&#x200B;를 강조 표시하고 아래 그림과 같이 **변형을 Live Copy**&#x200B;로 클릭합니다.

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. **Live Copy 만들기** 마법사에서 **ScreensFragment**&#x200B;을 선택하고 **다음**&#x200B;을 클릭합니다.

   d.**제목** 및 **이름**&#x200B;을 **화면**&#x200B;으로 입력합니다.

   e.**만들기**&#x200B;를 클릭하여 Live Copy를 만듭니다.

   f.**완료**&#x200B;를 클릭하여 **ScreensFragment** 페이지로 돌아갑니다.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >스크린 조각을 만들면 조각의 속성을 편집할 수 있습니다. 조각을 선택하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   **스크린 조각의 속성 편집**

   1. **ScreensFragment**(이전 단계에서 만든 경우)로 이동하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   1. 아래 그림과 같이 **오프라인 구성** 탭을 선택합니다.

   **클라이언트측 라이브러리**(java 및 css) 및 **정적 파일**&#x200B;을 경험 조각에 추가할 수 있습니다.

   다음 예에서는 경험 조각에 정적 파일의 일부로서 클라이언트측 라이브러리와 글꼴을 추가하는 것을 보여줍니다.  ![조각](assets/fragment.gif)

1. **스크린 채널에서 경험 조각을 구성 요소로 사용**

   1. **Screens** 조각을 사용할 스크린 채널로 이동합니다.
   1. **TestChannel**&#x200B;을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   1. 사이드 탭에서 구성 요소 아이콘을 클릭합니다.
   1. **경험 조각**&#x200B;을 채널에 끌어다 놓습니다.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.**경험 조각** 구성 요소를 선택하고 맨 위의 왼쪽(공구모양) 아이콘을 선택하여 **경험 조각** 대화 상자를 엽니다.

   f.**경로**&#x200B;의 *단계 3*&#x200B;에서 만든 조각의 **Screens** 라이브 카피를 선택합니다.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.**경험 조각**&#x200B;의 *3단계*&#x200B;에서 만든 조각의 **Screens** 라이브 카피를 선택합니다.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.**기간**&#x200B;에 밀리초 값을 입력합니다.

   나.**경험 조각** 대화 상자에서 **오프라인 구성**&#x200B;을 선택하여 클라이언트측 라이브러리와 정적 파일을 정의합니다.

   >[!NOTE]
   >
   >(4) 단계에서 구성한 것 외에 클라이언트 측 라이브러리 또는 정적 파일을 추가하려는 경우 **경험 조각** 대화 상자의 **오프라인 구성** 탭에서 추가할 수 있습니다.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.확인 표시를 클릭하여 프로세스를 완료합니다.

### 결과 {#validating-the-result} 확인

이전 단계가 완료되면 다음 방법으로 **ChannelOne**&#x200B;에서 경험 조각의 유효성을 확인할 수 있습니다.

1. **TestChannel**&#x200B;로 이동합니다.
1. 작업 표시줄에서 **미리 보기**&#x200B;를 선택합니다.

아래 그림과 같이 채널의 **사이트** 페이지(경험 조각의 Live Copy)에서 컨텐츠를 볼 수 있습니다.\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## {#propagating-changes-from-the-master-page} 페이지에 변경 사항을 전파합니다.

***Live*** Copy는 롤아웃 구성에 정의된 대로 동기화 작업에 의해 유지 관리되는 소스의 사본을 나타냅니다.

경험 조각 이후, 생성된 는 **사이트** 페이지의 Live Copy이므로, 마스터 페이지에서 해당 특정 조각을 변경하는 경우 경험 조각을 사용한 채널 또는 대상의 변경 사항을 볼 수 있습니다.

>[!NOTE]
>
>Live Copy에 대한 자세한 내용은 컨텐츠 재사용 을 참조하십시오.다중 사이트 관리자 및 Live Copy.

아래 절차에 따라 마스터 채널의 변경 내용을 대상 채널에 전파합니다.

1. **사이트** (마스터) 페이지에서 경험 조각을 선택하고 연필 아이콘을 클릭하여 경험 조각의 항목을 편집합니다.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 경험 조각을 선택하고 공구모양 아이콘을 클릭하여 이미지를 편집할 대화 상자를 엽니다.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. **제품 표** 대화 상자가 열립니다.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 이미지를 편집할 수 있습니다. 예를 들어 이 조각에서 첫 번째 이미지가 대체됩니다.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 경험 조각을 선택하고 롤아웃 아이콘을 클릭하여 채널에서 사용되는 조각에 변경 사항을 전파합니다.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 롤아웃 을 클릭하여 변경 사항을 확인합니다.

   그러면 변경 사항이 롤아웃됩니다.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 변경 사항 확인 {#validating-the-changes}

아래 절차에 따라 채널의 변경 사항을 확인하십시오.

1. **Screens** -> **채널** -> **TestChannel**&#x200B;로 이동합니다.

1. 작업 표시줄에서 **미리 보기**&#x200B;를 클릭하여 변경 내용을 확인합니다.

다음 이미지는 **TestChannel**&#x200B;의 변경 사항을 보여줍니다.\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

