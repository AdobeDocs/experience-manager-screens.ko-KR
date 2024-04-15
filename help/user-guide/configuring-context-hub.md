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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 1%

---

# AEM Screens에서 ContextHub 구성 {#configuring-contexthub-in-aem-screens}

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 에셋 변경 사항을 만들고 관리하는 데 중점을 둡니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반 채널을 만들고 관리하는 방법에 대한 자세한 내용을 살펴보기 전에 여러 시나리오에 대한 몇 가지 주요 용어를 알아보십시오.

**브랜드** - 높은 수준의 프로젝트 설명입니다.

**영역** - 디지털 광고 간판 등 AEM Screens 프로젝트 이름

**활동** - 재고 관리, 날씨 관리 또는 부서 가용성 관리와 같은 범주 규칙을 정의합니다.

**대상자** - 규칙을 정의합니다.

**세그먼트** - 주어진 규칙에 대해 재생할 에셋 버전. 예를 들어, 온도가 화씨 50도 미만이면 화면에는 뜨거운 음료, 아니면 차가운 음료의 이미지가 표시됩니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 일치하는 방식을 시각적으로 보여 줍니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 전제 조건 {#preconditions}

AEM Screens 프로젝트에 대한 Context Hub 구성을 시작하기 전에 데모용으로 Google Sheets를 설정하십시오.

>[!IMPORTANT]
>
>Google Sheets는 다음 예에서 값을 가져오는 샘플 데이터베이스 시스템으로 사용되며 교육용으로만 사용됩니다. Adobe은 프로덕션 환경에 Google Sheets 사용을 보증하지 않습니다.
>
>자세한 내용은 [API 키 가져오기](https://developers.google.com/maps/documentation/javascript/get-api-key) Google 설명서에서 확인할 수 있습니다.

## 1단계: 데이터 저장소 설정 {#step-setting-up-a-data-store}

데이터 저장소를 로컬 I/O 이벤트 또는 로컬 데이터베이스 이벤트로 설정할 수 있습니다.

다음 에셋 수준 데이터 트리거 예제는 ContextHub 구성 및 AEM Screens 채널에 대한 세그먼트 경로를 사용할 수 있도록 해 주는 Excel 시트와 같은 데이터 저장소를 설정하는 로컬 데이터베이스 이벤트를 보여 줍니다.

을(를) 설정한 후 `google` 아래 예에 표시된 대로 시트를 올바르게 작성합니다.

![이미지](/help/user-guide/assets/context-hub/context-hub1.png)

다음 유효성 검사는 두 값을 입력하여 연결을 확인할 때 표시되는 내용입니다. `*google sheet ID*` 및 `*API key*` 아래 형식으로:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![이미지](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>아래 특정 예제에서는 값이 100보다 크거나 50보다 작은 경우 자산 변경을 트리거하는 데이터 저장소인 google sheets를 보여 줍니다.

## 2단계: 저장소 구성 설정 {#step-setting-store-configurations}

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하여 왼쪽 사이드바에서 도구 아이콘을 클릭합니다. 클릭 **사이트** > **컨텍스트 허브**&#x200B;을 참조하십시오.

   ![이미지](/help/user-guide/assets/context-hub/context-hub3.png)

1. **ContextHub 저장소 구성 만들기**

   1. 이라는 구성 컨테이너로 이동합니다. **screens**.

   1. 선택 **만들기** > **구성 컨테이너 만들기** 제목을 다음으로 입력: **ContextHubDemo**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **탐색** 끝 **ContextHubDemo** > **만들기** **Content허브 구성** 및 클릭 **저장**.

      >[!NOTE]
      > 다음을 선택한 후 **저장**, 다음에 있습니다. **ContextHub 구성** 화면.

   1. 다음에서 **ContextHub 구성** 화면, 선택 **만들기** > **ContentHub 저장소 구성**

   ![이미지](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >AEM 6.5 기능 팩 4 또는 AEM 6.4 기능 팩 8의 일부로 고객은 를 업데이트해야 합니다 `/conf/screens/settings/cloudsettings` 끝 `sling:Folder`.
   >
   >아래 단계를 따르십시오.
   >
   >1. CRXDE Lite으로 이동한 다음 다음으로 이동 `/conf/screens/settings/cloudsettings`.
   >1. 다음을 확인: `cloudsettings jcr:primaryType` 다음에 있음 `sling:Folder`. 다음과 같은 경우 `jcr:primaryType` 이(가)에 없음 `sling:folder`를 클릭하고 다음 단계를 진행합니다.
   >1. 마우스 오른쪽 버튼 클릭 `/conf/screens/settings` 을 사용하여 노드를 만듭니다. *이름* 다음으로: **`cloudsettings1`** 및 *유형* 다음으로: **`sling:Folder`** 변경 내용을 저장합니다.
   >1. 아래의 모든 노드 이동 `/conf/screens/settings/cloudsettings` 끝 `cloudsettings1`.
   >1. 삭제 `cloudsettings` 저장하십시오.
   >1. 이름 바꾸기 `cloudsettings1` 끝 `cloudsettings` 저장하십시오.
   >1. 다음을 준수하십시오. `/conf/screens/settings/cloudsettings` 이(가) `jcr:primaryType` 다음으로: `sling:Folder`.
   >
   >업그레이드 전 또는 후에 작성자 및 게시에서 다음 단계를 수행합니다.

   1. 다음을 입력합니다. **제목** 다음으로: **Google Sheets**, **저장소 이름** 다음으로: **`googlesheets`**, 및 **저장소 유형** 다음으로: **c`ontexthub.generic-jsonp`** 및 클릭 **다음**.

      >[!CAUTION]
      >Adobe Experience Manager(AEM) 6.4를 사용하는 경우 **구성 제목** 다음으로: **`googlesheets`** 및 **저장소 유형** 다음으로: **c`ontexthub.generic-jsonp`**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 특정 JSON 구성을 입력합니다. 예를 들어 데모 목적으로 다음 json을 사용하고 을 선택할 수 있습니다. **저장**. 이라는 저장소 구성이 표시됩니다. **Google Sheets** ContextHub 구성에서.

      >[!IMPORTANT]
      >코드를 로 바꾸십시오. `*<Sheet ID>*` 및 `*<API Key>*`: Google Sheets를 설정하는 동안 가져온 것입니다.

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
      >위의 샘플 코드에서, **pollInterval** 값이 새로 고쳐지는 빈도(밀리초)를 정의합니다.
      >
      >코드를 다음으로 바꾸기 `*<Sheet ID>*` 및 `*<API Key>*`: Google Sheets를 설정하는 동안 가져온 것입니다.

      >[!CAUTION]
      >
      >전역 폴더 외부(예: 자체 프로젝트 폴더)에서 Google Sheets 스토어 구성을 생성하는 경우 타깃팅이 즉시 작동하지 않습니다.

1. **스토어 세분화 설정**

   1. 다음으로 이동 **ContentHub 저장소 구성** AEM Screens 구성 컨테이너에서 다른 저장소 구성을 만들고 **제목** 다음으로: **segmentation-contexthub**, **저장소 이름** 다음으로: **세분화** 및 **저장소 유형** 다음으로: **aem.segmentation**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 클릭 **다음** 그런 다음 **저장**.

      >[!NOTE]
      >JSON 정의 프로세스를 건너뛰고 비워 둡니다.


## 3단계: 대상에서 세그먼트 설정 {#setting-up-audience}

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 다음으로 이동 **개인화** > **대상** > **screens**.

   1. 클릭 **만들기** > **Context Hub 세그먼트 만들기** 다음 **새 ContextHub 세그먼트** 대화 상자가 열립니다.

   1. 다음을 입력합니다. **제목** 다음으로: `**Higherthan50**` 및 클릭 **만들기**. 마찬가지로 이라는 다른 세그먼트를 만듭니다. `**Lowerthan50**`.

      ![이미지](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 세그먼트 선택 `**Higherthan50**` 및 클릭 **속성** 작업 표시줄에서
      ![이미지](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 다음 항목 선택 **개인화** 의 탭 **세그먼트 속성**. 설정 **ContextHub 경로** 끝 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 및 **세그먼트 경로** 끝 `/conf/screens/settings/wcm/segments` 및 클릭 **저장**&#x200B;을 참조하십시오.

   ![이미지](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 마찬가지로, **ContextHub 경로** 및 **세그먼트 경로** 대상 `**Lowerthan50**` 세그먼트도 표시합니다.

## 4단계: 브랜드 및 영역 설정 {#setting-brand-area}

아래 단계에 따라 활동 및 브랜드 아래 영역에서 브랜드를 만드십시오.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 다음으로 이동 **개인화** > **활동**.

   1. 선택 **만들기** > **브랜드 만들기**.

   1. 선택 **브랜드** 다음에서 **페이지 만들기** 마법사 및 클릭 **다음**.

   1. 다음을 입력합니다. **제목** 다음으로: **ScreensBrand** 및 클릭 **만들기**. 이제 브랜드가 아래와 같이 생성되었습니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >알려진 문제:
      >영역을 추가하려면 URL에서 다음과 같이 기본 을 제거합니다.
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`

1. **브랜드에서 영역 만들기**

   브랜드에서 영역을 만들려면 아래 단계를 따르십시오.

   1. 선택 **만들기** 그런 다음 **영역 만들기**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 선택 **영역** 다음에서 **페이지 만들기** 마법사 및 선택 **다음**.

   1. 다음을 입력합니다. **제목** 다음으로: **화면 값** 및 선택 **만들기**.
브랜드에서 영역이 만들어집니다.

## 5단계: 활동에서 세그먼트 만들기 {#step-setting-up-audience-segmentation}

데이터 저장소를 설정하고 활동(브랜드 및 영역)을 정의한 후 아래 단계에 따라 활동에서 세그먼트를 만듭니다.

1. **활동에서 세그먼트 만들기**

   1. AEM 인스턴스에서 다음으로 이동 **개인화** > **활동** > **ScreensBrand** >**화면 값**.

   1. 선택 **만들기** > **활동을 만듭니다.** 다음 **활동 구성 마법사** 열림.

   1. 다음을 입력합니다. **제목** 다음으로: **ValueCheck50** 및 **이름** 다음으로: **valueccheck50**. 다음 항목 선택 **타겟팅 엔진** 다음으로: **ContextHub(AEM)** 드롭다운에서 을 선택하고 **다음**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 선택 **경험 추가** 다음에서 `**Configure Activity**` 마법사.

   1. 다음에서 **대상**&#x200B;를 선택하고 `**Higherthan50**` 및 선택 **경험 추가** 을(를) 입력한 후 **제목** 다음으로: `**higherthan50**` **이름** 다음으로: `**higherthan50**`. 선택 **확인**.

   1. 다음에서 **대상**&#x200B;를 선택하고 `**Lowerthan50**` 및 선택 **경험 추가** 을(를) 입력한 후 **제목** 다음으로: `**lowerthan50**` **이름** 다음으로: `**lowerthan50**`. 선택 **확인**.

   ![이미지](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 선택 **다음** 그런 다음 **저장**. `**ValueCheck50**` 이제 활동이 만들어지고 구성되었습니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub16.png)

## 5단계: 대상에서 세그먼트 편집{#editing-audience-segmentation}

1. **세그먼트 편집**

   1. AEM 인스턴스에서 다음으로 이동 **개인화** > **대상** > **screens**.

   1. 세그먼트 선택 `**Higherthan50**`, 및 선택 **편집** 작업 표시줄에서

   1. 을(를) 끌어다 놓습니다. **비교: 속성 - 값** 구성 요소를 편집기에 추가합니다.

   1. 렌치 아이콘을 클릭하여 **속성과 값 비교** 대화 상자.

   1. 선택 **구글시트/값/1/0** 의 드롭다운에서 **속성 이름**.

      >[!NOTE]
      > 다음 **구글시트/값/1/0** 에서 채워지는 대로 행 2 및 열을 참조합니다. `google` 아래 그림의 시트:

      ![이미지](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 다음 항목 선택 **연산자** 다음으로: **다음보다 큼** 드롭다운 메뉴에서 을(를) 선택합니다.

   1. 다음을 입력합니다. **값** 다음으로: **70**.

      >[!NOTE]
      >
      >AEM은 세그먼트를 녹색으로 표시하여 Google Sheet의 데이터를 확인합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub18.png)

   마찬가지로 속성 값을 다음으로 편집합니다. `**Lowerthan50**`.

   1. 을(를) 끌어다 놓습니다. **비교: 속성 - 값** 구성 요소를 편집기에 추가합니다.

   1. 렌치 아이콘을 선택합니다.

   1. 다음에서 **속성과 값 비교** 대화 상자에서 **구글시트/값/1/0** 의 드롭다운에서 **속성 이름**.

   1. 다음 항목 선택 **연산자** 다음으로: **보다 작음** 드롭다운 메뉴에서 을(를) 선택합니다.

   1. 다음을 입력합니다. **값** 다음으로: **50**.


## 채널에서 타깃팅 활성화 {#step-enabling-targeting-in-channels}

채널에서 타겟팅을 활성화하려면 아래 단계를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계에서는 을 사용하여 타깃팅을 활성화하는 방법을 보여 줍니다 **DataDrivenChannel** 이(가) AEM Screens 채널에서 만들어졌습니다.

1. 채널 선택 **TargetChannel** 및 클릭 **속성** 작업 표시줄에서

   ![이미지](/help/user-guide/assets/context-hub/context-hub19.png)

1. 다음 항목 선택 **개인화** 를 탭하여 ContextHub 구성을 설정할 수 있습니다.

   1. 설정 **ContextHub 경로** 끝 `/conf/screens/settings/wcm/segments` 및 **세그먼트 경로** 끝 `/conf/screens/settings/wcm/segments`.
   1. 브랜드를 다음으로 설정 **ScreensBrand** 드롭다운에서 **영역 참조 설정** 끝 **화면 값**.

   1. **저장 및 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      >
      >처음에 ContextHub 구성 및 세그먼트를 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. 다음 위치로 이동하여 선택합니다. **TargetChannel** 채널 및 클릭 **편집** 작업 표시줄에서

      >[!NOTE]
      >
      >모든 것을 올바르게 설정했으면 다음과 같이 표시됩니다 **타겟팅** 아래 그림과 같이 편집기에서 드롭다운에 있는 옵션입니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub21.png)

## 자세히 알아보기: 사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후 다양한 사용 사례에 따라 데이터가 트리거된 에셋이 다양한 산업에서 중요한 역할을 하는 방법을 이해할 수 있습니다.

1. **[소매 재고 타깃팅 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**
