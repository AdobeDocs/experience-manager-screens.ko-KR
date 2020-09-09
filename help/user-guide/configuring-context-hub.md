---
title: AEM Screens에서 ContextHub 구성
seo-title: AEM Screens에서 ContextHub 구성
description: 데이터 트리거 컨텐츠 변경을 위한 목적으로 데이터 저장소를 정의하는 타깃팅 엔진의 ContextHub에 대해 알려면 이 페이지를 따르십시오.
seo-description: 데이터 트리거 컨텐츠 변경을 위한 목적으로 데이터 저장소를 정의하는 타깃팅 엔진의 ContextHub에 대해 알려면 이 페이지를 따르십시오.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 2%

---


# AEM Screens에서 ContextHub 구성 {#configuring-contexthub-in-aem-screens}

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 것을 강조합니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반의 채널을 만들고 관리하는 데 대한 세부 사항을 살펴보려면 다양한 시나리오와 관련이 있는 주요 용어 중 몇 가지를 알아야 합니다.

**브랜드** 수준 높은 프로젝트 설명을 나타냅니다.

**영역** - 디지털 광고 간판 같은 AEM Screens 프로젝트 이름을 나타냅니다.

**활동** 재고 기반, 날씨 기반, 부서 가용성 기반 등과 같은 규칙 카테고리를 정의합니다.

**대상규칙을** 정의합니다.

**세그먼트** 해당 규칙에 대해 재생되는 자산 버전을 나타냅니다(예: 기온이 화씨 50도 미만인 경우, 화면에 뜨거운 커피 이미지가 표시되면 차가운 음료를 표시합니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 어떻게 일치하는지를 시각적으로 보여줍니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 전제 조건 {#preconditions}

AEM Screens 프로젝트에 대한 Context Hub 구성 구성을 시작하기 전에 Google Sheet를 설정해야 합니다(데모를 위해).

>[!IMPORTANT]
>
>Google Sheets는 다음 예에서 값을 가져오는 데 사용되는 샘플 데이터베이스 시스템으로 교육용으로만 사용됩니다. Adobe은 생산 환경을 위해 Google Sheets를 사용하는 것을 지지하지 않습니다.
>
>자세한 내용은 Google 설명서의 [API 키](https://developers.google.com/maps/documentation/javascript/get-api-key) 가져오기를 참조하십시오.

## 1단계:데이터 저장소 설정 {#step-setting-up-a-data-store}

데이터 저장소를 로컬 I/O 이벤트나 로컬 데이터베이스 이벤트로 설정할 수 있습니다.

다음 자산 수준 데이터 트리거 예는 ContextHub 구성 및 세그먼트 경로를 AEM Screens 채널에 사용할 수 있도록 해주는 Excel 시트와 같은 데이터 저장소를 설정하는 로컬 데이터베이스 이벤트를 보여줍니다.

아래와 같이 google 시트를 올바르게 설정했으면 다음을 수행하십시오.

![이미지](/help/user-guide/assets/context-hub/context-hub1.png)

다음 확인은 아래 형식으로 *google 시트 ID* 및 *API 키* 두 값을 입력하여 연결을 확인할 때 표시되는 것입니다.

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![이미지](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>아래 특정 예제는 값이 100보다 크거나 50보다 작으면 자산 변경을 트리거하는 데이터 저장소로서 google 시트를 보여줍니다.

## 2단계:스토어 구성 설정 {#step-setting-store-configurations}

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하고 왼쪽 세로 막대에서 도구 아이콘을 클릭합니다. 아래 그림과 같이 **사이트** —> **ContextHub**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub3.png)

1. **새 ContextHub 저장소 구성 만들기**

   1. 스크린 **으로 명명된 구성 컨테이너로 이동합니다**.

   1. 만들기 **** > **구성 컨테이너** 만들기를 클릭하고 제목을 **ContextHubDemo로**&#x200B;입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **ContextHubDemo** **>** Create **** ContentHub 구성 **만들기** 및 ClickFacebook Save ****&#x200B;로 이동합니다.

      >[!NOTE]
      > 저장을 **클릭하면** ContextHub 구성 **화면에** 나타납니다.

   1. ContextHub **구성** 화면에서 **만들기** > **ContentHub 저장소 구성..을 클릭합니다.**

      ![이미지](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >AEM 6.5 Feature Pack 4 또는 AEM 6.4 Feature Pack 8의 일부로 고객은 로 업데이트해야 `/conf/screens/settings/cloudsettings` 합니다 `sling:Folder`.
      > 
      >아래 단계를 따르십시오.
      >
      >1. CRXDE Lite으로 이동한 다음 로 이동합니다 `/conf/screens/settings/cloudsettings`.
      >1. 안에 `cloudsettings jcr:primaryType` 있는지 확인하십시오 `sling:Folder`. 가 `jcr:primaryType` 없는 경우 `sling:folder`다음 단계로 진행합니다.
      > 1. 마우스 오른쪽 단추 `/conf/screens/settings` 를 클릭하고 *이름* 을 cloudsettings1 **** 로 *새 노드를 만들고 sling:Folder변경 내용을 저장하고* Type **** Type을 만듭니다.
      >1. 다음 위치로 모든 노드 `/conf/screens/settings/cloudsettings` 를 `cloudsettings1`이동합니다.
      >1. 삭제 `cloudsettings` 및 저장
      >1. 이름을 `cloudsettings1` 변경하여 `cloudsettings` 저장합니다.
      >1. 이제 /conf/screens/settings/cloudsettings가 다음과 같이 있음을 `jcr:primaryType` 관찰해야 합니다 `sling:Folder`.
업그레이드 전 또는 후에 작성자의 다음 단계에 따라 게시해야 합니다.


   1. 제목 **을** Google ******** Google **Store 이름**&#x200B;으로 입력하고 **GoogleEsign 및 Google Store** 유형 **** ****&#x200B;으로 GoogleEtranthub StoreType asContexthub.genericjsonpV.JeckNext를 클릭합니다.

      >[!CAUTION]
      >Adobe Experience Manager(AEM) 6.4를 사용 중인 경우 **구성 제목** 을 **구문시트로** 입력하고 **스토어 유형** 을 **contexthub-jsonp.generic로 입력합니다**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub6.png)



   1. 특정 json 구성을 입력합니다. 예를 들어 다음 json을 데모 목적으로 사용하고 **저장을** 클릭하면 ContextHub 구성에서 Google Sheets **라는** 스토어 구성이 표시됩니다.

      >[!IMPORTANT]
      >Google Sheets를 설정하는 동안 가져온 코드를 *&lt;Sheet ID>* *및*&lt;API Key>(으)로 바꾸십시오.

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
      위의 샘플 코드에서 pollInterval은 **값이 새로 고쳐지는 빈도** (ms)를 정의합니다.
Google Sheets를 설정하는 동안 가져온 *&lt;Sheet ID>* *및*&lt;API키>로 코드를 바꿉니다.

      >[!CAUTION]
      Google Sheets 저장소 구성을 전역 폴더 외부에 만드는 경우(예: 자체 프로젝트 폴더), 타깃팅은 곧바로 작동하지 않습니다.

1. **스토어 세그멘테이션 설정**

   1. ContentHub **저장소 구성으로 이동합니다.** 그리고 스크린 구성 컨테이너에 다른 스토어 구성을 만들고, **Store** **Title을****** 세그멘테이션 **으로** 설정하고, **Store Name** 을 **a** mexentation및Type Segmentation Storeas aem.segmentation과 같이를 세그멘테이션으로 설정합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
json을 정의하는 과정을 건너뛰고 공백으로 두어야 합니다.


## 3단계:대상의 세그먼트 설정 {#setting-up-audience}

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > 대상 **> 화면** 으로 **이동합니다**.

   1. 만들기 **** > **컨텍스트 허브 세그먼트 만들기를 클릭합니다.** 새 **ContextHub 세그먼트** 대화 상자가 열립니다.

   1. Enter the **Title** as **Higherthan50** and click **Create**. 유사하게, 50보다 **소문자로 제목이 있는 다른 세그먼트를 만듭니다**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 세그먼트 Higher50 **을** 선택하고 작업 **표시줄에서** 속성을 클릭합니다.
      ![이미지](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 세그먼트 **속성에서 개인화** 탭을 **선택합니다**. 아래 그림에 표시된 대로 **ContextHub 경로를** 및 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 세그먼트 경로 **로** 설정하고 `/conf/screens/settings/wcm/segments` 저장을 ****&#x200B;클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 마찬가지로 **50보다 낮은 세그먼트에** 대한 ContextHub 경로 **및** 세그먼트 **** 경로도설정합니다.

## 4단계:브랜드 및 영역 설정 {#setting-brand-area}

아래 절차에 따라 브랜드 아래의 활동 및 영역에서 브랜드를 만드십시오.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 **개인화** > 활동 **으로 이동합니다**.

   1. 만들기 **** > 브랜드 **만들기를 클릭합니다**.

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. 이제 브랜드가 아래와 같이 생성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      알려진 문제:영역을 추가하려면
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **브랜드에서 영역 만들기**

   브랜드의 영역을 만들려면 아래 절차를 따르십시오.

   1. 만들기 **를** 클릭한 다음 영역 **만들기를 클릭합니다**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
브랜드에 영역이 만들어집니다.

## 5단계:활동에서 세그먼트 만들기 {#step-setting-up-audience-segmentation}

데이터 저장소를 설정하고 활동(브랜드 및 영역)을 정의했으면 아래 단계에 따라 활동에 세그먼트를 만듭니다.

1. **활동에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > **활동****>** ScreensBrand **>** ScreensValue로 이동합니다.

   1. 만들기 **** > 활동 **만들기를 클릭합니다.** 활동 **구성 마법사가** 열립니다.

   1. 제목 **을** ValueCheck50 **** 및 **이름** 으로 **valuecheck50**&#x200B;으로입력합니다. 드롭다운 **에서** 타깃팅 엔진 **을** ContextHub(AEM) **로 선택하고**&#x200B;다음을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 활동 **구성** 마법사에서 경험 **추가를 클릭합니다**.

   1. 대상자 **에서** 50 **보다** **높음을** 선택하고 경험 **추가** 를 클릭하고 50보다 높은선이라Twitter **Twitter 50** **** ****&#x200B;보다 높은선이라VertiselyVerify50보다 높은VertisingVerityVerify로 하는 TiserHealthanHealthan 5ExperienceHealthelyHealtheldsHealtheldsHealthelyHealthelyExperienceHealthanHealthelyHealthelyHealthelyHealthelyHealthelyBeatHealthelyHealthelyHealthelyHealthelyHealthelyHealthely Click **Ok**.

   1. 대상에서 **50****미만** 을 **선택하고 추가** 를 클릭한 다음 **추가** 를 클릭하고 Title 5 **as lowerLowerelerTitle50보다** **** ****&#x200B;낮은 TitleAsLowerelerJelemanVernelyAs 5Finn5보다 낮은5입니다. Click **Ok**.

      ![이미지](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **이제 ValueCheck50** 활동이 만들어지고 구성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub16.png)

## 5단계:대상에서 세그먼트 편집{#editing-audience-segmentation}

1. **세그먼트 편집**

   1. AEM 인스턴스에서 **개인화** > 대상 **> 화면** 으로 **이동합니다**.

   1. 세그먼트 **Higher50**&#x200B;을 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기의 값** 구성 요소입니다.

   1. 렌치 아이콘을 클릭하여 값을 **사용한 속성 비교 대화 상자를** 엽니다.

   1. 속성 이름 **의 드롭다운에서 워크시트/값/1/0** 을 **선택합니다**.

      >[!NOTE]
Google **Sheet/value/1/0** 은 아래 그림에서 google 시트에 채워진 행 2와 열을 나타냅니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 드롭다운 메뉴에서 **보다** **큼** 연산자를 선택합니다.

   1. 값을 **70** 으로 **입력합니다**.

      >[!NOTE]
      AEM은 세그먼트를 녹색으로 표시하여 Google Sheet에서 데이터의 유효성을 확인합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub18.png)
   마찬가지로 속성 값을 Lower than **50으로 편집합니다**.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기의 값** 구성 요소입니다.

   1. 렌치 아이콘을 클릭하여 값을 **사용한 속성 비교 대화 상자를** 엽니다.

   1. 속성 이름 **의 드롭다운에서 워크시트/값/1/0** 을 **선택합니다**.

   1. 드롭다운 메뉴에서 **보다** **작음** 연산자를 선택합니다.

   1. 값을 **50** 으로 **입력합니다**.



## 채널에서 타깃팅 활성화 {#step-enabling-targeting-in-channels}

채널에서 타깃팅을 활성화하려면 아래 절차를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계는 AEM Screens 채널에서 만든 **DataDrivenChannel을 사용하여** 타깃팅을 활성화하는 방법을 보여줍니다.

1. 채널 **TargetChannel을** 선택하고 작업 **표시줄에서** 속성을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub19.png)

1. 개인화 **탭을** 선택하여 ContextHub 구성을 설정합니다.

   1. ContextHub 경로 **를** 및 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 세그먼트 경로 **로** 설정하고 `/conf/screens/settings/wcm/segments` 저장을 ****&#x200B;클릭합니다.

   1. **저장 후 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      ContextHub 및 세그먼트 경로를 사용합니다. 여기서 처음에 컨텍스트 허브 구성 및 세그먼트를 저장했습니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub20.png)

   1. TargetChannel **채널을** 탐색하여 선택하고 작업 **모음에서** 편집을 클릭합니다.

      >[!NOTE]
      모든 것을 올바르게 설정한 경우 아래 그림과 같이 편집기의 **드롭다운에 타깃팅** 옵션이 표시됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub21.png)

## 자세한 내용:사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후에는 다른 사용 사례를 따라 데이터가 트리거된 자산이 다양한 산업 분야에서 중요한 역할을 수행하는 방식을 이해할 수 있습니다.

1. **[소매 재고 타깃팅 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**
