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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens에서 ContextHub 구성 {#configuring-contexthub-in-aem-screens}

이 섹션에서는 데이터 저장소를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 것을 강조합니다.

## 주요 용어 {#key-terms}

AEM Screens 프로젝트에서 인벤토리 기반 채널을 만들고 관리하는 세부 사항을 살펴보려면 먼저 여러 시나리오와 관련된 중요한 주요 용어 중 일부를 알아야 합니다.

**브랜드** 수준 높은 프로젝트 설명을 참조합니다.

**영역** 디지털 광고 사이니지와 같은 AEM Screens 프로젝트 이름을 나타냅니다.

**활동** 재고 기반, 날씨 기반, 부서 가용성 기반 등과 같은 규칙 카테고리를 정의합니다.

**대상규칙을** 정의합니다.

**세그먼트** 해당 규칙에 대해 재생할 자산 버전을 나타냅니다. 예를 들어 기온이 화씨 50도 미만인 경우 화면에 뜨거운 커피 이미지가 표시되고, 그렇지 않으면 차가운 음료가 표시됩니다.

다음 다이어그램은 ContextHub 구성이 활동, 대상 및 채널과 어떻게 일치하는지 시각적으로 보여줍니다.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 전제 조건 {#preconditions}

AEM Screens 프로젝트에 대해 Context Hub 구성을 구성하기 위해 데이터 저장소를 설정하기 전에 Google Sheets(데모용)를 설정해야 합니다.

>[!CAUTION]
>
>Google Sheets는 값이 반입되고 교육용 목적으로만 사용되는 샘플 데이터베이스 시스템으로 다음 예제에서 사용됩니다. Adobe는 프로덕션 환경에서 Google Sheets 사용을 지지하지 않습니다.
>
>자세한 내용은 Google 설명서의 [API 키](https://developers.google.com/maps/documentation/javascript/get-api-key) 가져오기를 참조하십시오.

## 1단계:데이터 저장소 설정 {#step-setting-up-a-data-store}

아래 절차에 따라 ContextHub 구성 및 AEM Screens 채널에 대한 세그먼트 경로를 사용할 수 있는 데이터 저장소를 설정하십시오.

1. **ContextHub로 이동**

   AEM 인스턴스로 이동하고 왼쪽 사이드바에서 도구 아이콘을 클릭합니다. 아래 **그림과** 같이 사이트 **—&gt;** ContextHub를클릭합니다.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **새 ContextHub 저장소 구성 만들기**

   1. 전역 **&gt;** 기본값 **&gt;** ContextHub 구성으로 **이동합니다**.

   1. ** 만들기 &gt; 구성 컨테이너를 **클릭하고 제목을 ContextHubDemo** **로 입력합니다.

   1. **** ContextHubDemo ****&gt; ContentHub **** Store 구성...를 클릭하여 구성 **마법사를**&#x200B;엽니다.

   1. Google **Sheets** , Google **Sheets**, Google Sheets **Google Sheets** 형식으로 Google Store 이름을 ******** **입력합니다.Contexthub Generic-jsonp**

   1. **다음**&#x200B;을 클릭합니다
   1. 특정 json 구성**을 입력합니다.** 예를 들어 데모 목적으로 다음 json을 사용할 수 있습니다.
   1. **저장**&#x200B;을 클릭합니다.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >위의 샘플 코드에서 pollInterval **은** 값이 새로 고쳐지는 빈도(ms)를 정의합니다.
   >
   >
   >코드를 Google Sheets *를* 설정하는 동안 가져온 *&lt;Sheet ID&gt;*&#x200B;및&lt;API Key&gt;(으)로 바꿉니다.

   >[!CAUTION]
   Google Sheets 저장소 구성을 기존 폴더 외부에 만드는 경우(예: 자체 프로젝트 폴더) 타깃팅이 제대로 작동하지 않습니다.
   Google Sheets 저장소 구성을 전역 레거시 폴더 밖으로 구성하려는 경우 스토어 이름을 **세그멘테이션** 및 **스토어** 유형으로 **** aem.segmentation ****&#x200B;저장소 유형을설정해야합니다. 또한 위에서 정의한 대로 json을 정의하는 프로세스를 건너뛸 수 있습니다.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 개인화 **&gt; 활동으로** 이동합니다 ****

   1. 만들기 **&gt; 브랜드** **만들기를 클릭합니다**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. 이제 브랜드가 아래와 같이 생성됩니다.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   알려진 문제:
   영역을 추가하려면 URL에서
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **브랜드에서 영역 만들기**

   브랜드의 영역을 만들려면 아래 절차를 따르십시오.

   1. 만들기를 **클릭한** 다음 **영역 만들기**

   1. Select **Area** from the **Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**.
활동에서 영역이 만들어집니다.

## 2단계:고객 세분화 설정 {#step-setting-up-audience-segmentation}

데이터 저장소를 설정하고 브랜드를 정의했으면 아래 단계에 따라 대상 세그먼트를 설정하십시오.

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 개인화 &gt; **대상** &gt; **We** . **Retail로**&#x200B;이동합니다.

   1. 만들기 **&gt;** 컨텍스트 **허브 세그먼트 만들기를 클릭합니다.** 새 **ContextHub 세그먼트** 대화 상자가 열립니다.

   1. Enter the **Title** as **SheetA1 1** and click **Create**. 마찬가지로 SheetA2 2 **라는 다른 세그먼트를 만듭니다**.

1. **세그먼트 편집**

   1. 세그먼트 **시트 A1** (단계(5)에서 생성)을 선택하고 작업 **표시줄에서 편집을** 클릭합니다.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기에** 대한 값 구성 요소입니다.
   1. 렌치 아이콘을 클릭하여 속성과 값 **비교** 대화 상자를 엽니다.
   1. 속성 **이름의** 드롭다운에서 워크시트/값/1/0 **을**&#x200B;선택합니다.

   1. 드롭다운 **메뉴에서** **등호** 연산자를 선택합니다.

   1. 값을 **1** 로 **입력합니다**.
   >[!NOTE]
   AEM 파섹

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   마찬가지로 속성 값을 시트 A1 **2로**&#x200B;편집합니다.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기에** 대한 값 구성 요소입니다.
   1. 렌치 아이콘을 클릭하여 속성과 값 **비교** 대화 상자를 엽니다.
   1. 속성 **이름의** 드롭다운에서 워크시트/값/1/0 **을**&#x200B;선택합니다.

   1. 드롭다운 **메뉴에서** **등호** 연산자를 선택합니다.

   1. 값을 **2** 로 **입력합니다**.
   >[!NOTE]
   이전 단계에 적용된 규칙은 다음 사용 사례를 구현하기 위해 세그먼트를 설정하는 방법의 한 예입니다.

## 3단계:채널에서 타깃팅 활성화 {#step-enabling-targeting-in-channels}

채널에서 타깃팅을 활성화하려면 아래 절차를 따르십시오.

1. AEM Screens 채널* 중 하나로 이동합니다. **다음 단계는 AEM Screens 채널에서 **만든 DataDrivenRetail** 을 사용하여 타깃팅을 활성화하는 방법을 보여줍니다.

1. 채널 DataDrivenRetail **을** 선택하고 작업 **표시줄에서** 속성을 클릭합니다.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 개인화 **탭을 선택하여** ContextHub 구성을 설정합니다.

   1. ContextHub 경로를 **** libs **** 설정 **&gt;** 설정 **&gt; clouddefault** &gt; DefaultConfigurationsBehance ContextBehaviorClickHub SelectSelect로 **** **** ****&#x200B;선택합니다.

   1. 세그먼트 경로를 ************ conf로 **선택합니다.** 소매 **설정 &gt;** wcm &gt; wcm **** ****&#x200B;세그먼트 &gt; 세그먼트세그먼트선택 을 클릭합니다.

   1. 저장 **및 닫기를 클릭합니다**.
   >[!NOTE]
   ContextHub 및 세그먼트 경로를 사용합니다. 여기서 처음에 컨텍스트 허브 구성 및 세그먼트를 저장했습니다.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. DataDrivenAssets 채널에서 **DataDrivenRetail** 을 **찾아** 선택하고 **작업** 표시줄에서 **[편집]을 클릭합니다** .

   >[!NOTE]
   모든 것을 올바르게 설정한 경우 아래 그림과 **같이** 편집기의 드롭다운에 타깃팅 옵션이 표시됩니다.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   채널에 대해 ContextHub 구성을 구성한 후에는 아래의 모든 사용 사례를 따르려면 다른 세 시퀀스 채널에 대해 1부터 4까지의 이전 단계를 따르십시오.

## 자세한 내용:사용 사례 예 {#learn-more-example-use-cases}

AEM Screens 프로젝트에 대해 ContextHub를 구성한 후에는 다른 사용 사례를 통해 데이터를 트리거한 자산이 다양한 업계에서 중요한 역할을 수행하는 방법을 파악할 수 있습니다.

1. **[소매 인벤토리 대상 활성화](retail-inventory-activation.md)**
1. **[출장 센터 온도 활성화](local-temperature-activation.md)**
1. **[숙박 예약 활성화](hospitality-reservation-activation.md)**