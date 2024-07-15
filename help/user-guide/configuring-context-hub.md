---
title: AEM Screens에서 ContextHub 구성
description: 데이터 트리거 콘텐츠 변경을 위해 데이터 저장소를 정의할 수 있도록 타겟팅 엔진의 ContextHub에 대해 알아봅니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# AEM Screens에서 ContextHub 구성 {#configuring-contexthub-in-aem-screens}

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 에셋 변경 사항을 만들고 관리하는 데 중점을 둡니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반 채널을 만들고 관리하는 방법에 대한 자세한 내용을 살펴보기 전에 여러 시나리오에 대한 몇 가지 주요 용어를 알아보십시오.

**브랜드** - 높은 수준의 프로젝트 설명입니다.

**영역** - 디지털 광고 서명 등 AEM Screens 프로젝트 이름

**활동** - 재고 기반, 날씨 기반 또는 부서 가용성 기반 등의 범주 규칙을 정의합니다.

**대상** - 규칙을 정의합니다.

**세그먼트** - 지정된 규칙에 대해 재생할 에셋의 버전입니다. 예를 들어, 온도가 화씨 50도 미만이면 화면에는 뜨거운 음료, 아니면 차가운 음료의 이미지가 표시됩니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 일치하는 방식을 시각적으로 보여 줍니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 전제 조건 {#preconditions}

AEM Screens 프로젝트에 대한 ContextHub 구성을 시작하기 전에 데모용으로 Google Sheets를 설정하십시오.

>[!IMPORTANT]
>
>Google Sheets는 다음 예에서 값을 가져오는 샘플 데이터베이스 시스템으로 사용되며 교육용으로만 사용됩니다. Adobe은 프로덕션 환경에 Google Sheets 사용을 보증하지 않습니다.
>
>자세한 내용은 Google 설명서에서 [API 키 가져오기](https://developers.google.com/maps/documentation/javascript/get-api-key)를 참조하십시오.

## 1단계: 데이터 저장소 설정 {#step-setting-up-a-data-store}

데이터 저장소를 로컬 I/O 이벤트 또는 로컬 데이터베이스 이벤트로 설정할 수 있습니다.

다음 자산 수준 데이터 트리거 예제는 로컬 데이터베이스 이벤트를 보여 줍니다. 이 이벤트는 ContextHub 구성 및 AEM Screens 채널에 대한 세그먼트 경로를 사용할 수 있도록 해 주는 Excel 시트와 같은 데이터 저장소를 설정합니다.

아래 예와 같이 `google` 시트를 올바르게 설정한 후

![이미지](/help/user-guide/assets/context-hub/context-hub1.png)

아래 형식으로 두 값 `*google sheet ID*`과(와) `*API key*`을(를) 입력하여 연결을 확인할 때 표시되는 유효성 검사입니다.

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![이미지](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>아래 특정 예제에서는 값이 100보다 크거나 50보다 작은 경우 자산 변경을 트리거하는 데이터 저장소인 Google Sheets를 보여 줍니다.

## 2단계: 저장소 구성 설정 {#step-setting-store-configurations}

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하여 왼쪽 사이드바에서 도구 아이콘을 클릭합니다. 아래 그림과 같이 **사이트** > **ContextHub**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub3.png)

1. **ContextHub 저장소 구성 만들기**

   1. **screens**(으)로 제목이 지정된 구성 컨테이너로 이동합니다.

   1. **만들기** > **구성 컨테이너 만들기**&#x200B;를 클릭하고 제목을 **ContextHubDemo**(으)로 입력하십시오.

      ![이미지](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **탐색** **ContextHubDemo** > **만들기** **ContentHub 구성**&#x200B;로 이동하고 **저장**&#x200B;을 클릭합니다.

      >[!NOTE]
      > **저장**&#x200B;을 클릭하면 **ContextHub 구성** 화면에 표시됩니다.

   1. **ContextHub 구성** 화면에서 **만들기** > **ContentHub 저장소 구성**&#x200B;을 클릭합니다

   ![이미지](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >AEM 6.5 기능 팩 4 또는 AEM 6.4 기능 팩 8의 일부로 고객은 `/conf/screens/settings/cloudsettings`을(를) `sling:Folder`(으)로 업데이트해야 합니다.
   >
   >아래 단계를 따르십시오.
   >
   >1. CRXDE Lite으로 이동한 다음 `/conf/screens/settings/cloudsettings`(으)로 이동합니다.
   >1. `cloudsettings jcr:primaryType`이(가) `sling:Folder`에 있는지 확인하십시오. `jcr:primaryType`이(가) `sling:folder`에 없으면 다음 단계를 진행하십시오.
   >1. `/conf/screens/settings`을(를) 마우스 오른쪽 단추로 클릭하고 *name*&#x200B;을(를) **`cloudsettings1`**(으)로, *Type*&#x200B;을(를) **`sling:Folder`**(으)로 하는 노드를 만든 다음 변경 내용을 저장합니다.
   >1. `/conf/screens/settings/cloudsettings`의 모든 노드를 `cloudsettings1`(으)로 이동합니다.
   >1. `cloudsettings`을(를) 삭제하고 저장합니다.
   >1. `cloudsettings1`의 이름을 `cloudsettings`(으)로 변경하고 저장합니다.
   >1. `/conf/screens/settings/cloudsettings`에 `sling:Folder`(으)로 `jcr:primaryType`이(가) 있는지 확인하십시오.
   >
   >업그레이드 전 또는 후에 작성자 및 Publish에서 다음 단계를 수행합니다.

   1. **제목**&#x200B;을(를) **Google 시트**, **스토어 이름**&#x200B;을(를) **`googlesheets`**, **스토어 유형**&#x200B;을(를) **c`ontexthub.generic-jsonp`**(으)로 입력하고 **다음**&#x200B;을(를) 클릭합니다.

      >[!CAUTION]
      >Adobe Experience Manager(AEM) 6.4를 사용하는 경우 **구성 제목**&#x200B;을 **`googlesheets`**(으)로 입력하고 **스토어 유형**&#x200B;을(를) **c`ontexthub.generic-jsonp`**(으)로 입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 특정 JSON 구성을 입력합니다. 예를 들어 데모용으로 다음 json을 사용하고 **저장**&#x200B;을 클릭할 수 있습니다. ContextHub 구성에 **Google 시트**(으)로 제목이 지정된 저장소 구성이 표시됩니다.

      >[!IMPORTANT]
      >Google 시트를 설정하는 동안 가져온 코드를 `*<Sheet ID>*` 및 `*<API Key>*`(으)로 바꾸십시오.

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
      >
      >위의 샘플 코드에서 **pollInterval**&#x200B;은 값이 새로 고쳐지는 빈도(밀리초)를 정의합니다.
      >
      >Google 시트를 설정하는 동안 가져온 코드를 `*<Sheet ID>*` 및 `*<API Key>*`(으)로 바꿉니다.

      >[!CAUTION]
      >
      >전역 폴더 외부(예: 자체 프로젝트 폴더)에 구성을 저장하도록 Google 시트를 만드는 경우 타깃팅이 즉시 작동하지 않습니다.

1. **스토어 세분화 설정**

   1. **ContentHub 저장소 구성**(으)로 이동하여 AEM Screens 구성 컨테이너에서 다른 저장소 구성을 만들고 **Title**&#x200B;을(를) **segmentation-contexthub**(으)로, **저장소 이름**&#x200B;을(를) **segmentation**(으)로, **저장소 유형**&#x200B;을(를) **aem.segmentation**(으)로 설정합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub7.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다.

      >[!NOTE]
      >JSON 정의 프로세스를 건너뛰고 비워 둡니다.


## 3단계: 대상에서 세그먼트 설정 {#setting-up-audience}

1. **Audiences에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **Personalization** > **대상** > **화면**(으)로 이동합니다.

   1. **만들기** > **ContextHub 세그먼트 만들기를 클릭합니다.** **새 ContextHub 세그먼트** 대화 상자가 열립니다.

   1. **제목**&#x200B;을(를) `**Higherthan50**`(으)로 입력하고 **만들기**&#x200B;를 클릭합니다. 마찬가지로 `**Lowerthan50**`(으)로 제목이 지정된 다른 세그먼트를 만듭니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub11.png)

   1. `**Higherthan50**` 세그먼트를 클릭하고 작업 표시줄에서 **속성**을 클릭합니다.
      ![이미지](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **세그먼트 속성**&#x200B;에서 **Personalization** 탭을 클릭합니다. 아래 그림과 같이 **ContextHub 경로**&#x200B;을(를) `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`(으)로 설정하고 **세그먼트 경로**&#x200B;을(를) `/conf/screens/settings/wcm/segments`(으)로 설정하고 **저장**&#x200B;을(를) 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 마찬가지로 `**Lowerthan50**` 세그먼트에 대해 **ContextHub 경로** 및 **세그먼트 경로**&#x200B;도 설정하십시오.

## 4단계: 브랜드 및 영역 설정 {#setting-brand-area}

아래 단계에 따라 활동 및 브랜드 아래 영역에서 브랜드를 만드십시오.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 **Personalization** > **활동**(으)로 이동합니다.

   1. **만들기** > **브랜드 만들기**&#x200B;를 클릭합니다.

   1. **페이지 만들기** 마법사에서 **브랜드**&#x200B;를 클릭하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을(를) **ScreensBrand**(으)로 입력하고 **만들기**&#x200B;를 클릭합니다. 이제 브랜드가 아래와 같이 생성되었습니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >알려진 문제:
      >영역을 추가하려면 URL에서 다음과 같이 기본 을 제거합니다.
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`

1. **브랜드에서 영역 만들기**

   브랜드에서 영역을 만들려면 아래 단계를 따르십시오.

   1. **만들기**&#x200B;를 클릭한 다음 **영역 만들기**&#x200B;를 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub9.png)

   1. **페이지 만들기** 마법사에서 **영역**&#x200B;을 클릭하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을(를) **ScreensValue**(으)로 입력하고 **만들기**를 클릭합니다.
브랜드에서 영역이 만들어집니다.

## 5단계: 활동에서 세그먼트 만들기 {#step-setting-up-audience-segmentation}

데이터 저장소를 설정하고 활동(브랜드 및 영역)을 정의한 후 아래 단계에 따라 활동에서 세그먼트를 만듭니다.

1. **활동에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **Personalization** > **활동** > **ScreensBrand** >**ScreensValue**&#x200B;로 이동합니다.

   1. **만들기** > **활동 만들기를 클릭합니다.** **활동 구성 마법사**&#x200B;가 열립니다.

   1. **Title**&#x200B;을(를) **ValueCheck50**(으)로 입력하고 **Name**&#x200B;을(를) **valueccheck50**(으)로 입력하십시오. 드롭다운에서 **ContextHub(AEM)**(으)로 **타깃팅 엔진**&#x200B;을(를) 클릭하고 **다음**&#x200B;을(를) 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub14.png)

   1. `**Configure Activity**` 마법사에서 **경험 추가**&#x200B;를 클릭합니다.

   1. **대상**&#x200B;에서 `**Higherthan50**`을(를) 클릭하고 **경험 추가**&#x200B;를 클릭한 다음 **제목**&#x200B;을(를) `**higherthan50**` **이름**&#x200B;을(를) `**higherthan50**`(으)로 입력하십시오. **확인**&#x200B;을 클릭합니다.

   1. **대상**&#x200B;에서 `**Lowerthan50**`을(를) 클릭하고 **경험 추가**&#x200B;를 클릭한 다음 **제목**&#x200B;을(를) `**lowerthan50**` **이름**&#x200B;을(를) `**lowerthan50**`(으)로 입력하십시오. **확인**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub15.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다. 이제 `**ValueCheck50**` 활동이 만들어지고 구성되었습니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub16.png)

## 5단계: 대상에서 세그먼트 편집{#editing-audience-segmentation}

1. **세그먼트 편집**

   1. AEM 인스턴스에서 **Personalization** > **대상** > **화면**(으)로 이동합니다.

   1. `**Higherthan50**` 세그먼트를 클릭하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   1. **비교: 속성 - 값** 구성 요소를 편집기로 끌어서 놓습니다.

   1. 렌치 아이콘을 클릭하면 **속성과 값 비교** 대화 상자를 열 수 있습니다.

   1. **속성 이름**&#x200B;의 드롭다운에서 **googlesheets/value/1/0**&#x200B;을(를) 클릭합니다.

      >[!NOTE]
      > **googlesheets/value/1/0**&#x200B;은(는) 아래 그림에서 `google`장으로 채워진 행 2와 열을 참조합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 드롭다운 메뉴에서 **연산자**&#x200B;을(를) **보다 큼**(으)로 클릭합니다.

   1. **값**&#x200B;을(를) **70**(으)로 입력하십시오.

      >[!NOTE]
      >
      >AEM은 세그먼트를 녹색으로 표시하여 Google Sheet의 데이터를 확인합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub18.png)

   마찬가지로 속성 값을 `**Lowerthan50**`(으)로 편집합니다.

   1. **비교: 속성 - 값** 구성 요소를 편집기로 끌어서 놓습니다.

   1. 렌치 아이콘을 클릭합니다.

   1. **속성을 값과 비교** 대화 상자의 **속성 이름**&#x200B;에 있는 드롭다운에서 **googlesheets/value/1/0**&#x200B;을(를) 클릭합니다.

   1. 드롭다운 메뉴에서 **연산자**&#x200B;을(를) **다음보다 작음**(으)로 클릭합니다.

   1. **값**&#x200B;을(를) **50**(으)로 입력하십시오.


## 채널에서 타깃팅 활성화 {#step-enabling-targeting-in-channels}

채널에서 타겟팅을 활성화하려면 아래 단계를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계에서는 AEM Screens 채널에서 만든 **DataDrivenChannel**&#x200B;을 사용하여 타깃팅을 활성화하는 방법을 보여 줍니다.

1. **TargetChannel** 채널을 클릭하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub19.png)

1. ContextHub 구성을 설정하려면 **Personalization** 탭을 클릭하십시오.

   1. **ContextHub 경로**&#x200B;을(를) `/conf/screens/settings/wcm/segments`(으)로 설정하고 **세그먼트 경로**&#x200B;을(를) `/conf/screens/settings/wcm/segments`(으)로 설정합니다.
   1. 드롭다운에서 브랜드를 **ScreensBrand**(으)로 설정하고 **영역 참조 설정**&#x200B;을(를) **ScreensValue**(으)로 설정합니다.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      >
      >ContextHub 구성 및 세그먼트를 처음 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. **TargetChannel** 채널을 탐색하고 클릭한 다음 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

      >[!NOTE]
      >
      >모든 것을 올바르게 설정한 경우 아래 그림과 같이 편집기의 드롭다운에 **타깃팅** 옵션이 표시됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub21.png)

## 자세히 알아보기: 사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후 다양한 사용 사례에 따라 데이터가 트리거된 에셋이 다양한 산업에서 중요한 역할을 하는 방법을 이해할 수 있습니다.

1. **[소매 인벤토리 대상 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[접대 예약 활성화](hospitality-reservation-activation.md)**
