---
title: AEM Screens에서 ContextHub 구성
seo-title: AEM Screens에서 ContextHub 구성
description: 데이터 트리거 컨텐츠 변경 목적으로 데이터 저장소를 정의하려면 타깃팅 엔진의 ContextHub에 대해 자세히 알아보십시오.
seo-description: 데이터 트리거 컨텐츠 변경 목적으로 데이터 저장소를 정의하려면 타깃팅 엔진의 ContextHub에 대해 자세히 알아보십시오.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: 화면 개발
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 2%

---

# AEM Screens {#configuring-contexthub-in-aem-screens}에서 ContextHub 구성

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 것을 강조합니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반 채널을 만들고 관리하는 세부 사항을 이해하려면 먼저 서로 다른 시나리오와 관련된 중요한 용어 중 일부를 알고 있어야 합니다.

**** 브랜드상위 수준 프로젝트 설명을 나타냅니다.

**** AreaDigital Ad Signage 와 같은 AEM Screens 프로젝트 이름을 나타냅니다

**** 활동재고 기반, 날씨 기반, 부서 가용성 기반 등의 규칙 카테고리를 정의합니다.

**** 대상규칙을 정의합니다.

**** 세그먼트주어진 규칙에 대해 재생할 자산 버전을 나타냅니다. 온도가 50도 미만이면 화면에 뜨거운 커피 이미지가 표시되고, 그렇지 않으면 차가운 음료수가 표시됩니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 어떻게 일치하는지에 대한 시각적 표현을 제공합니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 전제 조건 {#preconditions}

AEM Screens 프로젝트에 대한 Context Hub 구성 구성을 시작하기 전에 Google Sheet를 설정해야 합니다(데모용).

>[!IMPORTANT]
>
>다음 예에서 Google Sheet는 값을 가져오는 데 사용되는 샘플 데이터베이스 시스템으로 교육용으로만 사용됩니다. Adobe은 Google Sheet를 프로덕션 환경에 사용하는 것을 승인하지 않습니다.
>
>자세한 내용은 Google 설명서에서 [API 키 가져오기](https://developers.google.com/maps/documentation/javascript/get-api-key) 를 참조하십시오.

## 1단계:데이터 저장소 설정 {#step-setting-up-a-data-store}

데이터 저장소를 로컬 I/O 이벤트나 로컬 데이터베이스 이벤트로 설정할 수 있습니다.

다음 자산 수준 데이터 트리거 예에서는 ContextHub 구성 및 세그먼트 경로를 AEM Screens 채널에 사용할 수 있도록 해주는 Excel 시트와 같은 데이터 저장소를 설정하는 로컬 데이터베이스 이벤트를 보여줍니다.

아래와 같이 google 시트를 올바르게 설정했으면 다음과 같습니다.

![이미지](/help/user-guide/assets/context-hub/context-hub1.png)

다음 유효성 검사는 아래 형식으로 *google sheet ID* 및 *API 키*&#x200B;를 입력하여 연결을 확인할 때 표시되는 것입니다.

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![이미지](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>아래 특정 예제는 값이 100보다 크거나 50보다 작은 경우 자산 변경을 트리거하는 데이터 저장소인 google 시트를 보여줍니다.

## 2단계:저장소 구성 설정 {#step-setting-store-configurations}

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하고 왼쪽 사이드바에서 도구 아이콘을 클릭합니다. 아래 그림과 같이 **Sites** —> **ContextHub**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub3.png)

1. **새 ContextHub 저장소 구성 만들기**

   1. **screens**&#x200B;라는 구성 컨테이너로 이동합니다.

   1. **만들기** > **구성 컨테이너 만들기**&#x200B;를 클릭하고 제목을 **ContextHubDemo**&#x200B;로 입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** ContextHubDemo **>** CreateContentHub  **** **구성으로 이동한 후** 저장 ****&#x200B;을 클릭합니다.

      >[!NOTE]
      > **저장**&#x200B;을 클릭하면 **ContextHub 구성** 화면이 표시됩니다.

   1. **ContextHub 구성** 화면에서 **만들기** > **ContentHub 저장소 구성..** 을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >AEM 6.5 기능 팩 4 또는 AEM 6.4 기능 팩 8의 일부로, 고객은 `/conf/screens/settings/cloudsettings` 을 `sling:Folder`(으)로 업데이트해야 합니다.
      >
      >아래 단계를 따르십시오.
      >
      >1. CRXDE Lite으로 이동한 다음 `/conf/screens/settings/cloudsettings` 로 이동합니다.
      >1. `cloudsettings jcr:primaryType`이 `sling:Folder`에 있는지 확인합니다. `jcr:primaryType`이 `sling:folder`에 없는 경우 다음 단계로 진행합니다.
      >1. `/conf/screens/settings`을(를) 마우스 오른쪽 단추로 클릭하고 *name*&#x200B;을 **cloudsettings1**&#x200B;로 사용하고 *Type*&#x200B;을 **sling:Folder**&#x200B;로 사용하여 새 노드를 만들고 변경 내용을 저장합니다.
      >1. `/conf/screens/settings/cloudsettings` 아래의 모든 노드를 `cloudsettings1`(으)로 이동합니다.
      >1. `cloudsettings` 을(를) 삭제하고 저장합니다.
      >1. `cloudsettings1` 이름을 `cloudsettings`(으)로 변경하고 저장합니다.
      >1. 이제 /conf/screens/settings/cloudsettings에 `jcr:primaryType`이(가) `sling:Folder`으로 있음을 관찰해야 합니다.

      >
      >업그레이드 전 또는 후에 작성자 및 게시에서 다음 단계를 수행해야 합니다.

   1. **제목**&#x200B;을 **Google Sheets**, **이름**&#x200B;을 **Google Sheet**&#x200B;로 입력하고, **저장소 유형**&#x200B;을 **contexthub.generic-jsonp**&#x200B;로 입력하고 **다음**&#x200B;을 클릭합니다.

      >[!CAUTION]
      >Adobe Experience Manager(AEM) 6.4를 사용하는 경우 **구성 제목**&#x200B;을 **goglessheet**(으)로 입력하고 **저장소 유형**&#x200B;을 **contexthub.generic-jsonp**&#x200B;으로 입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 특정 json 구성을 입력합니다. 예를 들어 데모 목적으로 다음 json을 사용하고 **저장**&#x200B;을 클릭할 수 있으며, ContextHub 구성에서 **Google Sheets**&#x200B;라는 저장소 구성이 표시됩니다.

      >[!IMPORTANT]
      >Google Sheet를 설정하는 동안 가져온 코드를 *&lt;시트 ID>* 및 *&lt;API 키>*&#x200B;로 바꾸십시오.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      위의 샘플 코드에서 **pollInterval**&#x200B;은(는) 값을 새로 고치는 빈도를 정의합니다(ms).
      코드를 *&lt;시트 ID>* 및 *&lt;API 키>*&#x200B;로 바꿉니다. 이 경우 Google Sheet를 설정할 때 가져온 데이터입니다.

      >[!CAUTION]
      글로벌 폴더 외부의(예: 고유한 프로젝트 폴더)에 Google Sheet 저장소 구성을 만들면 타깃팅이 즉시 작동하지 않습니다.


1. **스토어 세그멘테이션 설정**

   1. **ContentHub 저장소 구성으로 이동합니다.** 및 screens 구성 컨테이너에서 다른 저장소 구성을 만들고  **** Titleas  **segmentation-contexthub**,  **Store** Namas  **** segmentationand  **Store** Typeas  **aem.segmentation**&#x200B;을 설정합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub7.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다.

      >[!NOTE]
json을 정의하는 프로세스를 건너뛰고 비워 두어야 합니다.


## 3단계:대상 {#setting-up-audience}에서 세그먼트 설정

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > **대상** > **screens**&#x200B;로 이동합니다.

   1. **만들기** > **Context Hub 세그먼트 만들기 를 클릭합니다.** 새  **ContextHub** 세그멘테이션 대화 상자가 열립니다.

   1. **제목**&#x200B;을 **Higherthan50**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다. 마찬가지로 **Lower than50**&#x200B;이라는 다른 세그먼트를 만듭니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 세그먼트 **Higher50**&#x200B;를 선택하고 작업 표시줄에서 **속성**을 클릭합니다.
      ![이미지](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **세그먼트 속성**&#x200B;에서 **개인화** 탭을 선택합니다. 아래 그림과 같이 **ContextHub 경로**&#x200B;를 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`(으)로 설정하고 **세그먼트 경로**&#x200B;를 `/conf/screens/settings/wcm/segments`로 설정하고 **저장**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 마찬가지로 **Lower than50** 세그먼트에 대한 **ContextHub 경로** 및 **세그먼트 경로**&#x200B;를 설정하십시오.

## 4단계:브랜드 및 영역 설정 {#setting-brand-area}

브랜드 아래에 있는 활동 및 영역에서 브랜드를 만드십시오.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 **개인화** > **활동**&#x200B;으로 이동합니다.

   1. **만들기** > **브랜드 만들기**&#x200B;를 클릭합니다.

   1. **페이지 만들기** 마법사에서 **브랜드**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을 **ScreensBrand**&#x200B;로 입력하고 **만들기**&#x200B;를 클릭합니다. 이제 브랜드가 아래와 같이 생성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      알려진 문제:
영역을 추가하려면 다음과 같이 URL에서 마스터를 제거합니다
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **브랜드에서 영역 만들기**

   브랜드에 영역을 만들려면 아래 단계를 수행하십시오.

   1. **만들기**&#x200B;를 클릭한 다음 **영역 만들기**&#x200B;를 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub9.png)

   1. **페이지 만들기** 마법사에서 **영역**&#x200B;을 선택하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을 **ScreensValue**&#x200B;로 입력하고 **만들기**를 클릭합니다.
브랜드에 영역이 만들어집니다.

## 5단계:활동에 세그먼트 만들기 {#step-setting-up-audience-segmentation}

데이터 저장소를 설정하고 활동(브랜드 및 영역)을 정의했으면 아래 단계에 따라 활동에 세그먼트를 만듭니다.

1. **활동에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > **활동** > **ScreensBrand** >**ScreensValue**&#x200B;로 이동합니다.

   1. **만들기** > **활동 만들기를 클릭합니다.** 활동  **구성 마법사** 가 열립니다.

   1. **제목**&#x200B;을 **ValueCheck50**(으)로 입력하고 **이름**&#x200B;을 **value50**&#x200B;으로 입력합니다. 드롭다운에서 **타깃팅 엔진**&#x200B;을 **ContextHub(AEM)**(으)로 선택하고 **다음**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub14.png)

   1. **활동 구성 마법사**&#x200B;에서 **경험 추가**&#x200B;를 클릭합니다.

   1. **대상**&#x200B;에서 **Higherthan50**&#x200B;을 선택하고 **경험 추가**&#x200B;를 클릭하고 **제목**&#x200B;을 **higherthan50** **이름**&#x200B;을 **가장 높임**&#x200B;을 입력합니다. **확인**&#x200B;을 클릭합니다.

   1. **대상**&#x200B;에서 **Lower than50**&#x200B;을 선택하고 **경험 추가**&#x200B;를 클릭한 다음 **제목**&#x200B;을 **50** **이름**&#x200B;이름을 **소문자로 &lt;a50**&#x200B;입력합니다. **확인**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub15.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다. **이제 ValueCheck50** 활동이 만들어지고 구성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub16.png)

## 5단계:대상{#editing-audience-segmentation}에서 세그먼트 편집

1. **세그먼트 편집**

   1. AEM 인스턴스에서 **개인화** > **대상** > **screens**&#x200B;로 이동합니다.

   1. 세그먼트 **Higher50**&#x200B;를 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   1. **비교를 끌어서 놓습니다.Property - Value** 구성 요소를 편집기에 추가합니다.

   1. 공구모양 아이콘을 클릭하여 **속성과 값** 비교 대화 상자를 엽니다.

   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을 선택합니다.

      >[!NOTE]
 **googlesheets/value/1/0** 은 아래 그림에서 google 시트에 채워진 대로 2행 및 열을 나타냅니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 드롭다운 메뉴에서 **연산자**&#x200B;보다 큼&#x200B;**를 선택합니다.**

   1. **값**&#x200B;을 **70**&#x200B;으로 입력합니다.

      >[!NOTE]
      AEM은 세그먼트를 녹색으로 표시하여 Google Sheet에서 데이터의 유효성을 검사합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub18.png)
   마찬가지로 속성 값을 **Lower than50**&#x200B;로 편집합니다.

   1. **비교를 끌어서 놓습니다.Property - Value** 구성 요소를 편집기에 추가합니다.

   1. 공구모양 아이콘을 클릭하여 **속성과 값** 비교 대화 상자를 엽니다.

   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을 선택합니다.

   1. 드롭다운 메뉴에서 **연산자**&#x200B;보다 작음&#x200B;**을 선택합니다.**

   1. **값**&#x200B;을 **50**&#x200B;으로 입력합니다.



## 채널 {#step-enabling-targeting-in-channels}에서 타깃팅 활성화

채널에서 타깃팅을 활성화하려면 아래 절차를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계는 AEM Screens 채널에서 만든 **DataDrivenChannel**&#x200B;을 사용하여 타깃팅을 활성화하는 방법을 보여줍니다.

1. 채널 **TargetChannel**&#x200B;을 선택하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub19.png)

1. **개인화** 탭을 선택하여 ContextHub 구성을 설정합니다.

   1. **ContextHub 경로**&#x200B;를 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`(으)로 설정하고 **세그먼트 경로**&#x200B;를 `/conf/screens/settings/wcm/segments`(으)로 설정하고 **저장**&#x200B;을 클릭합니다.

   1. **저장 후 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      Context Hub 구성 및 세그먼트를 처음 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub20.png)

   1. **TargetChannel** 채널을 탐색하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

      >[!NOTE]
      모든 사항을 올바르게 설정한 경우 아래 그림과 같이 편집기에서 드롭다운에 **타깃팅** 옵션이 표시됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub21.png)

## 추가 정보:사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트용으로 ContextHub를 구성한 후에는 다른 사용 사례 를 따라 데이터가 트리거된 자산이 다양한 산업에서 어떻게 중요한 역할을 수행하는지 이해할 수 있습니다.

1. **[소매 재고 타깃팅된 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**
