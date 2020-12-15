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
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 2%

---


# AEM Screens {#configuring-contexthub-in-aem-screens}에서 ContextHub 구성

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 것을 강조합니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반의 채널을 만들고 관리하는 방법에 대한 세부 사항을 살펴보려면, 서로 다른 시나리오와 관련이 있는 중요한 용어 중 일부를 알아야 합니다.

**브랜드** 수준 높은 프로젝트 설명을 참조하십시오.

**영역** 디지털 광고 간판 같은 AEM Screens 프로젝트 이름을 나타냅니다.

**활동** 재고 기반, 날씨 기반, 부서 가용성 기반 등과 같은 규칙 범주를 정의합니다.

**대상규칙** 을 정의합니다.

**세그먼트** 특정 규칙에 대해 재생되는 자산 버전을 나타냅니다. 온도가 화씨 50도 미만인 경우 화면에 따뜻한 커피 이미지가 표시되고 그렇지 않으면 차가운 음료수가 표시됩니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 어떻게 일치하는지를 시각적으로 보여줍니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 조건 {#preconditions}

AEM Screens 프로젝트에 대한 Context Hub 구성 구성을 시작하기 전에 Google Sheet를 설정해야 합니다(데모용).

>[!IMPORTANT]
>
>Google Sheet는 다음 예제에서 값을 가져와서 교육용 목적으로만 사용할 수 있는 샘플 데이터베이스 시스템으로 사용됩니다. Adobe은 프로덕션 환경에서 Google Sheet를 사용하는 것을 승인하지 않습니다.
>
>자세한 내용은 Google 설명서의 [API 키 가져오기](https://developers.google.com/maps/documentation/javascript/get-api-key)를 참조하십시오.

## 1단계:데이터 저장소 설정 {#step-setting-up-a-data-store}

데이터 저장소를 로컬 입출력 이벤트나 로컬 데이터베이스 이벤트로 설정할 수 있습니다.

다음 에셋 수준 데이터 트리거 예제에서는 ContextHub 구성 및 AEM Screens 채널의 세그먼트 경로를 사용할 수 있는 Excel 시트와 같은 데이터 저장소를 설정하는 로컬 데이터베이스 이벤트를 보여 줍니다.

아래와 같이 google 시트를 올바르게 설정했으면 다음을 수행하십시오.

![이미지](/help/user-guide/assets/context-hub/context-hub1.png)

다음 확인은 아래 형식으로 *google sheet ID* 및 *API 키*&#x200B;의 두 값을 입력하여 연결을 확인할 때 볼 내용입니다.

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![이미지](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>아래 특정 예제는 값이 100보다 크거나 50보다 작으면 자산 변경을 트리거하는 데이터 저장소로서 google 시트를 보여줍니다.

## 2단계:스토어 구성 설정 {#step-setting-store-configurations}

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하고 왼쪽 세로 막대에서 도구 아이콘을 클릭합니다. 아래 그림과 같이 **사이트** —> **ContextHub**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub3.png)

1. **새 ContextHub 저장소 구성 만들기**

   1. **screens**&#x200B;라는 구성 컨테이너로 이동합니다.

   1. **만들기** > **구성 컨테이너 만들기**&#x200B;를 클릭하고 제목을 **ContextHubDemo**&#x200B;로 입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** ContextHubDemo  **> CreateContentHub 구성**  **** **으로 이동하고** 저장을  **클릭합니다**.

      >[!NOTE]
      > **저장**&#x200B;을 클릭하면 **ContextHub 구성** 화면에 표시됩니다.

   1. **ContextHub 구성** 화면에서 **만들기** > **ContentHub 저장소 구성..**

      ![이미지](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >AEM 6.5 기능 팩 4 또는 AEM 6.4 기능 팩 8의 일부로 고객은 `/conf/screens/settings/cloudsettings`을 `sling:Folder`로 업데이트해야 합니다.
      >
      >아래 단계를 따르십시오.
      >
      >1. CRXDE Lite으로 이동한 다음 `/conf/screens/settings/cloudsettings`으로 이동합니다.
      >1. `cloudsettings jcr:primaryType`이(가) `sling:Folder`에 있는지 확인합니다. `jcr:primaryType`이(가) `sling:folder`에 없는 경우 다음 단계로 진행합니다.
      >1. `/conf/screens/settings`을(를) 마우스 오른쪽 단추로 클릭하고 *name*&#x200B;이(가) **cloudsettings1** 및 *Type*&#x200B;을 **sling:Folder**&#x200B;으로 새 노드를 만들고 변경 내용을 저장합니다.
      >1. `/conf/screens/settings/cloudsettings` 아래의 모든 노드를 `cloudsettings1`(으)로 이동합니다.
      >1. `cloudsettings`을(를) 삭제하고 저장합니다.
      >1. `cloudsettings1`의 이름을 `cloudsettings`로 변경하고 저장합니다.
      >1. 이제 /conf/screens/settings/cloudsettings에 `jcr:primaryType`이(가) `sling:Folder`(으)로 있음을 관찰해야 합니다.

      >
      >업그레이드 전 또는 후에 작성자와 게시에서 다음 단계를 수행해야 합니다.

   1. **제목** Google Sheets **,**&#x200B;스토어 이름&#x200B;**을** googessheet **으로 입력하고**&#x200B;스토어 유형&#x200B;**을** contexthub.generic-jsonp **을(를) 클릭하고**&#x200B;다음&#x200B;**을 클릭합니다.**

      >[!CAUTION]
      >Adobe Experience Manager(AEM) 6.4를 사용하는 경우 **구성 제목**&#x200B;을 **googessheet** 및 **스토어 유형**&#x200B;을 **contexthub.generic-jsonp**&#x200B;으로 입력합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 특정 json 구성을 입력합니다. 예를 들어 다음 json을 데모 목적으로 사용하고 **저장**&#x200B;을 클릭하면 ContextHub 구성에 **Google Sheets**&#x200B;라는 이름의 스토어 구성이 표시됩니다.

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
      위의 샘플 코드에서 **pollInterval**&#x200B;은 값이 새로 고쳐지는 빈도(ms)를 정의합니다.
      Google Sheet를 설정하는 동안 가져온 *&lt;시트 ID>* 및 *&lt;API 키>*&#x200B;로 코드를 바꿉니다.

      >[!CAUTION]
      글로벌 폴더 외부에 Google Sheets 저장소 구성을 만드는 경우(예: 자체 프로젝트 폴더), 타깃팅은 즉시 작동하지 않습니다.


1. **스토어 세그멘테이션 설정**

   1. **ContentHub 저장소 구성으로 이동합니다..** 그리고 스크린 구성 컨테이너에 다른 스토어 구성을 만들고  **** Title as  **segmentation-contexthub**,  **Store Nameas** , Store Nameas  **** 및  ****   **** Store 세그멘테이션aem.segmentation를 설정합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub7.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다.

      >[!NOTE]
json을 정의하는 프로세스를 건너뛰고 공백으로 유지해야 합니다.


## 3단계:대상 {#setting-up-audience}에서 세그먼트 설정

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > **대상** > **screens**&#x200B;로 이동합니다.

   1. **만들기** > **컨텍스트 허브 세그먼트 만들기를 클릭합니다.** [ **새 ContextHub** 세그먼트] 대화 상자가 열립니다.

   1. **제목**&#x200B;을 **Higherthan50**&#x200B;으로 입력하고 **만들기**&#x200B;를 클릭합니다. 마찬가지로 **50 보다 작음**&#x200B;이라는 제목의 다른 세그먼트를 만듭니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 세그먼트 **Higherthan50**&#x200B;을 선택하고 작업 표시줄에서 **속성**을 클릭합니다.
      ![이미지](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **세그먼트 속성**&#x200B;에서 **개인화** 탭을 선택합니다. 아래 그림과 같이 **ContextHub 경로**&#x200B;을 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 및 **세그먼트 경로**&#x200B;을 `/conf/screens/settings/wcm/segments`로 설정하고 **저장**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 마찬가지로 **50** 세그먼트에 대해 **ContextHub 경로** 및 **세그먼트 경로**&#x200B;도 설정합니다.

## 4단계:브랜드 및 영역 설정 {#setting-brand-area}

브랜드 아래의 활동 및 영역에서 브랜드를 만들려면 아래 절차를 따르십시오.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 **개인화** > **활동**&#x200B;으로 이동합니다.

   1. **만들기** > **브랜드 만들기**&#x200B;를 클릭합니다.

   1. **페이지 만들기** 마법사에서 **브랜드**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을 **ScreensBrand**&#x200B;로 입력하고 **만들기**&#x200B;를 클릭합니다. 이제 브랜드가 아래와 같이 생성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      알려진 문제:
영역을 추가하려면 다음과 같은 URL에서 마스터를 제거합니다.
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **브랜드에서 영역 만들기**

   브랜드의 영역을 만들려면 아래 단계를 수행하십시오.

   1. **만들기**&#x200B;를 클릭한 다음 **영역 만들기**&#x200B;를 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub9.png)

   1. **페이지 만들기** 마법사에서 **영역**&#x200B;을 선택하고 **다음**&#x200B;을 클릭합니다.

   1. **제목**&#x200B;을 **ScreensValue**&#x200B;로 입력하고 **만들기**를 클릭합니다.
브랜드에 영역이 만들어집니다.

## 5단계:활동 {#step-setting-up-audience-segmentation}에서 세그먼트 만들기

데이터 저장소를 설정하고 활동(브랜드 및 영역)을 정의했으면 아래 단계에 따라 활동에 세그먼트를 만듭니다.

1. **활동에서 세그먼트 만들기**

   1. AEM 인스턴스에서 **개인화** > **활동** > **ScreensBrand** >**ScreensValue**&#x200B;로 이동합니다.

   1. **만들기** > **활동 만들기를 클릭합니다.** 활동  **구성 마법사가** 열립니다.

   1. **제목**&#x200B;을 **ValueCheck50** 및 **이름**&#x200B;을 **valuecheck50**&#x200B;으로 입력합니다. 드롭다운에서 **타깃팅 엔진**&#x200B;을 **ContextHub (AEM)**&#x200B;으로 선택하고 **다음**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub14.png)

   1. **활동 구성 마법사**&#x200B;에서 **경험 추가**&#x200B;를 클릭합니다.

   1. **대상**&#x200B;에서 **Higherthan50**&#x200B;을 선택하고 **경험 추가**&#x200B;를 클릭한 다음 **제목**&#x200B;을 50 ****&#x200B;이름&lt;a10/>을 입력합니다. 1/>은(는) **higherthan50**&#x200B;으로 지정됩니다. **** **확인**&#x200B;을 클릭합니다.

   1. **대상**&#x200B;에서 **50 미만**&#x200B;경험 추가&#x200B;**경험 추가**&#x200B;를 클릭하고 **제목**&#x200B;을 **50** **이름**&#x200B;을 입력합니다. **lower than50**) **확인**&#x200B;을 클릭합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub15.png)

   1. **다음**&#x200B;을 클릭한 다음 **저장**&#x200B;을 클릭합니다. **이제 ValueCheck50** 활동이 만들어지고 구성됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub16.png)

## 5단계:대상에서 세그먼트 편집{#editing-audience-segmentation}

1. **세그먼트 편집**

   1. AEM 인스턴스에서 **개인화** > **대상** > **screens**&#x200B;로 이동합니다.

   1. 세그먼트 **Higher50**&#x200B;을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   1. **비교:속성 - 편집기에 대한 값** 구성 요소입니다.

   1. 공구 모양 아이콘을 클릭하여 **속성과 값** 비교 대화 상자를 엽니다.

   1. **속성 이름**&#x200B;의 드롭다운에서 **googlessheet/value/1/0**&#x200B;을(를) 선택합니다.

      >[!NOTE]
작업표/ **값/1/0** 은 아래 그림에서 google 시트에 채워진 행 2와 열을 나타냅니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 드롭다운 메뉴에서 **연산자**&#x200B;를 **보다 큼**&#x200B;으로 선택합니다.

   1. **값**&#x200B;을 **70**&#x200B;으로 입력합니다.

      >[!NOTE]
      AEM에서는 세그먼트를 녹색으로 표시하여 Google Sheet에서 데이터의 유효성을 검사합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub18.png)
   마찬가지로 속성 값을 **Lower than50**&#x200B;으로 편집합니다.

   1. **비교:속성 - 편집기에 대한 값** 구성 요소입니다.

   1. 공구 모양 아이콘을 클릭하여 **속성과 값** 비교 대화 상자를 엽니다.

   1. **속성 이름**&#x200B;의 드롭다운에서 **googlessheet/value/1/0**&#x200B;을(를) 선택합니다.

   1. 드롭다운 메뉴에서 **연산자**&#x200B;를 **보다 작음**&#x200B;으로 선택합니다.

   1. **값**&#x200B;을 **50**&#x200B;으로 입력합니다.



## 채널 {#step-enabling-targeting-in-channels}에서 타깃팅 활성화

채널에서 타깃팅을 활성화하려면 아래 절차를 따르십시오.

1. AEM Screens 채널 중 하나로 이동합니다. 다음 단계는 AEM Screens 채널에서 만든 **DataDrivenChannel**&#x200B;을 사용하여 타깃팅을 활성화하는 방법을 보여줍니다.

1. 채널 **TargetChannel**&#x200B;을 선택하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/context-hub/context-hub19.png)

1. **개인화** 탭을 선택하여 ContextHub 구성을 설정합니다.

   1. **ContextHub 경로**&#x200B;을 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 및 **세그먼트 경로**&#x200B;을 `/conf/screens/settings/wcm/segments`로 설정하고 **저장**&#x200B;을 클릭합니다.

   1. **저장 후 닫기**&#x200B;를 클릭합니다.

      >[!NOTE]
      ContextHub 구성 및 세그먼트를 처음에 저장한 ContextHub 및 세그먼트 경로를 사용합니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub20.png)

   1. **TargetChannel** 채널을 탐색하여 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

      >[!NOTE]
      모든 내용을 올바르게 설정한 경우 아래 그림과 같이 편집기의 드롭다운에 **타게팅** 옵션이 표시됩니다.

      ![이미지](/help/user-guide/assets/context-hub/context-hub21.png)

## 자세한 내용:예제 사용 사례 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후에는 다른 사용 사례를 따라 데이터를 트리거한 자산이 다른 업계에서 중요한 역할을 수행하는 방법을 파악할 수 있습니다.

1. **[소매 인벤토리 타깃팅 활성화](retail-inventory-activation.md)**
1. **[여행 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**
