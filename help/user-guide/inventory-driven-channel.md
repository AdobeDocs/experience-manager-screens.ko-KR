---
title: 인벤토리 기반 채널
seo-title: 인벤토리 기반 채널
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 인벤토리 기반 채널{#inventory-driven-channel}

## 인벤토리 기반 채널 시작하기 {#getting-started-with-inventory-driven-channels}

이 섹션에서는 Google Sheets를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 것을 강조하는 사용 사례 예를 설명합니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주요 배우 {#primary-actors}

컨텐츠 작성자

### 용어 {#terminolgies}

아래 약관을 따라 프로젝트를 이해하고 설정하는 데 중요한 역할을 수행합니다.

**활동** 활동은 카테고리를 나타냅니다.

**영역** 프로젝트 기본

**대상** 데이터의 위치

**브랜드** 브랜드

**세그먼트** 세그먼트는 타깃팅하려는 자산의 컨테이너를 나타냅니다.

### 기본 흐름:프로젝트 설정 {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**사전 요구 사항:**
>
>프로젝트에서 데이터 기반 자산 변경 설정 및 사용에 대한 세부 사항을 자세히 살펴보려면 먼저 시퀀스 채널이 있는 AEM Screens 프로젝트를 만들어야 합니다. 데모 목적으로 DataDrivenAsset **이라는** 프로젝트가 제작되고 시퀀스의 제목이 DataDrivenRestaurant **,** DataDrivenTextOverlay **, DataDriven WeatherWeather 및 DataDriven Retail********** 아래 그림에 표시된 대로 프로젝트에 DataDriven Retail이 추가됩니다.
>
>4개의 서로 다른 채널을 만드는 것은 데모용으로만 사용되며 서로 다른 채널에서 4개의 서로 다른 사용 사례를 보여줍니다. 하나의 사용 사례만 요구 사항으로 팔로우하려면 하나의 시퀀스 채널만 만들어 주십시오.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

아래 섹션을 따라 AEM Screens 프로젝트에서 Google Sheets를 사용하여 데이터 기반 자산 변경 사항을 만들고 관리하는 샘플 프로젝트를 만드십시오.

## 1단계:데이터베이스 설정 {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets는 값이 반입되고 교육용으로만 사용되는 다음 예제 데이터베이스 시스템에서 사용됩니다. Adobe는 프로덕션 환경에서 Google Sheets 사용을 지지하지 않습니다.
>
>자세한 내용은 Google 설명서의 [API 키](https://developers.google.com/maps/documentation/javascript/get-api-key) 가져오기를 참조하십시오.

1. Google 문서에 로그인합니다.

   >[!NOTE]
   >
   >새 Google 시트를 만들기 전에 Google Drive에 계정이 있어야 합니다.

1. 새 빈 스프레드시트를 시작합니다. Google 시트에 컨텐츠를 추가하고 저장합니다. 데모를 위해 Google Sheet의 이름은 ContextHubDemo **로 지정됩니다**.
1. Google **Sheet** 오른쪽 상단 모서리에서 공유를 클릭하여 다른 사람과 **공유** 대화 상자를 엽니다. 고급 **옵션을** 클릭하고 **아래 그림과 같이 설정을 켜기 -**&#x200B;링크가있는 모든 사람으로 변경합니다.

   이 단계에서는 google 시트의 값에 액세스할 수 있습니다.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. 이전 **단계에서 저장을** 클릭하면 Google 시트에 대한 링크가 표시됩니다. 나중에 참조할 수 있도록 클릭 수를 저장하고 완료를 **클릭합니다**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets는 다음 예에서 교육용 용도로 사용됩니다. Adobe는 프로덕션 환경에서 Google Sheets 사용을 지지하지 않습니다.

## 2단계:Google Sheets REST API 활성화 {#step-enabling-the-google-sheets-rest-apis}

Google Sheet를 설정했으면 Google Sheet REST API를 활성화하여 값에 액세스해야 합니다.

Google Sheets용 REST API를 활성화하는 방법에 대한 자세한 내용은 Google API 설명서를 참조하십시오.

1. Google API [콘솔로 이동합니다](https://console.developers.google.com/apis/credentials). Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. 프로젝트 이름을 **자산** 변경으로 **입력하고** 만들기를 **클릭합니다**.
1. 프로젝트를 만들었으면 API 키를 설정해야 합니다. 자격 **증명** 만들기를 클릭하고 **API 키 **를 선택하여 프로젝트에 대한 API 키를 생성합니다. 향후 참조를 위해 API 키를 저장합니다.

   >[!NOTE]
   >
   >이 데모 프로젝트는 무료 Google API 키를 사용합니다. 자세한 내용은 Google 웹 사이트의 가격 및 제한 사항 API 키 **가져오기를** 참조하십시오.

### Google 시트 설정 확인 {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;your sheet id&gt;/values/Sheet1?key=&lt;your API key&gt;

예:

** Google Sheets** 링크가 *다음과 같은 경우:*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, then

**시트 ID는** 다음과 같습니다. `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**API 키** : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

위의 구문에 두 값 추가:

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

이제 시트에서 데이터를 볼 수 있습니다.

## 2단계:Google Sheets의 컨텐츠를 가져오도록 AEM 구성 {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

다음 섹션에서는 Google Sheets에서 콘텐츠를 가져오기 위해 AEM(Adobe Experience Manager)을 구성하는 방법에 대해 설명합니다.

1. AEM 인스턴스로 이동하고 왼쪽 사이드바에서 도구 아이콘을 클릭합니다. 아래 **그림과** 같이 사이트 **—&gt;** ContextHub를클릭합니다.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **새 ContextHub 저장소 구성 만들기**

   1. 전역 **&gt;** 기본값 **&gt;** ContextHub 구성으로 **이동합니다**.

   1. ** 만들기 &gt; 구성 컨테이너를 **클릭하고 제목을 ContextHubDemo**로** 입력합니다.

   1. **** ContextHubDemo ****&gt; ContentHub **** Store 구성...구성 **마법사를 열려면**
   1. Google **Sheets** , Google **Sheets**, Google Sheets **Google Sheets** 형식으로 Google Store 이름을 ******** **입력합니다.Contexthub Generic-jsonp**
   1. **다음**&#x200B;을 클릭합니다
   1. 특정 json 구성을 입력합니다. 예를 들어 데모 목적으로 다음 json을 사용할 수 있습니다.
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
   >코드를 *&lt;Sheet ID&gt;* 및 *&lt;API Key&gt;*( **1단계에서 가져온)로바꿉니다.데이터베이스 설정을 참조하십시오.**

   >[!CAUTION]
   Google Sheets 저장소 구성을 기존 폴더 외부에 만드는 경우(예: 자체 프로젝트 폴더) 타깃팅이 제대로 작동하지 않습니다.
   Google Sheets 저장소 구성을 전역 레거시 폴더 밖으로 구성하려는 경우 스토어 이름을 **세그멘테이션** 및 **스토어** 유형으로 **** aem.segmentation ****&#x200B;저장소 유형을설정해야합니다. 또한 위에서 정의한 대로 json을 정의하는 프로세스를 건너뛸 수 있습니다.

1. **활동에서 브랜드 만들기**

   1. AEM 인스턴스에서 개인화 **&gt; 활동으로** 이동합니다 ****

   1. 클릭** 만들기** &gt; **브랜드 만들기**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. 이제 브랜드가 아래와 같이 생성됩니다.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
알려진 문제:
영역을 추가하려면 URL에서
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. 브랜드에서 영역 만들기**

   1. 만들기 **&gt; 영역** **만들기를 클릭합니다**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. 활동에서 영역이 만들어집니다.

1. **대상에서 세그먼트 만들기**

   1. AEM 인스턴스에서 개인화 &gt; **대상** &gt; **We** . **Retail로**&#x200B;이동합니다.
   1. 만들기 **&gt;** 컨텍스트 **허브 세그먼트 만들기를 클릭합니다**. 새 ContextHub 세그먼트 대화 상자가 열립니다.
   1. Enter the **Title** as **SheetA1 1** and click **Create**. 마찬가지로 SheetA2 2 **라는 다른 세그먼트를 만듭니다**.

1. **세그먼트 편집**

   1. 세그먼트 **시트 A1** (단계(5)에서 생성)을 선택하고 작업 **표시줄에서 편집을** 클릭합니다.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기에** 대한 값 구성 요소입니다.
   1. 렌치 아이콘을 클릭하여 속성과 값 **비교** 대화 상자를 엽니다.
   1. 속성 **이름의** 드롭다운에서 워크시트/값/1/0 **을**&#x200B;선택합니다.

   1. 드롭다운 **메뉴에서** **Equal **로 연산자를 선택합니다.

   1. 값을 **1** 로 **입력합니다**.
   >[!NOTE]
   AEM 파섹

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   마찬가지로 속성 값을 시트 A1 **2로**&#x200B;편집합니다.

   1. 비교를 드래그하여 **놓습니다.속성 - 편집기에** 대한 값 구성 요소입니다.
   1. 렌치 아이콘을 클릭하여 속성과 값 **비교** 대화 상자를 엽니다.
   1. 속성 **이름의** 드롭다운에서 워크시트/값/1/0 **을**&#x200B;선택합니다.

   1. 드롭다운 **메뉴에서** **Equal **로 연산자를 선택합니다.

   1. 값을 **2** 로 **입력합니다**.
   >[!NOTE]
   이전 단계에 적용된 규칙은 다음 사용 사례를 구현하기 위해 세그먼트를 설정하는 방법의 한 예입니다.

## 3단계:AEM Screens 채널에서 Context Hub 구성 설정 {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

아래 절차에 따라 AEM Screens 채널에 대한 ContextHub 구성 및 세그먼트 경로를 설정합니다.

1. 사전 요구 사항으로 만든 AEM Screens 채널(**DataDrivenRetail**) 중 하나로 이동합니다.
1. 채널(DataDrivenRetail)**을**&#x200B;선택하고 작업 **표시줄에서** 속성을 클릭합니다.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 개인화 **탭을 선택하여** ContextHub 구성을 설정합니다.

   1. ContextHub 경로를 **** libs **** 설정 **&gt;** 설정 **&gt; clouddefault** &gt; DefaultConfigurationsBehance ContextBehaviorClickHub SelectSelect로 **** **** ****&#x200B;선택합니다.

   1. 세그먼트 경로를 ******강사로** 선택합니다. &gt; **We 소매 **&gt; **설정을** **** **** ****&#x200B;선택합니다.

   1. 저장 **및 닫기를 클릭합니다**.
   >[!NOTE]
   ContextHub 및 세그먼트 경로를 사용합니다. 여기서 처음에 컨텍스트 허브 구성 및 세그먼트를 저장했습니다.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   위의 대화 상자에서 **타깃팅 구성** 아래에 있는 **브랜드를 선택하지 않으면** 타깃팅 프로세스를 시작할 때 브랜드 및 활동을 선택해야 합니다.

1. DataDrivenAssets **&gt; **Channels** ** **에서 DataDrivenRetail을** 찾아 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   >[!NOTE]
   모든 것을 올바르게 설정한 경우 아래 그림과 **같이** 편집기의 드롭다운에 타깃팅 옵션이 표시됩니다.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   채널에 대해 ContextHub 구성을 구성한 후에는 아래의 모든 사용 사례를 따르려면 다른 세 시퀀스 채널에 대해 1부터 4까지의 이전 단계를 따르십시오.

## 사용 사례 1:소매 인벤토리 활성화 {#use-case-retail-inventory-activation}

다음 사용 사례에서는 Google Sheet의 값을 기준으로 세 개의 다른 이미지를 보여 줍니다.

### 설명 {#description}

이 사용 사례에서는 세 개의 서로 다른 컬러 트레이닝셔츠에 대한 소매 재고 재고 재고가 표시됩니다. Google Sheets에 기록되어 있는 Stock에서 사용 가능한 스웨터 수에 따라 화면에 가장 많은 수의 이미지(빨간색, 녹색 또는 파란색 스웨터)가 표시됩니다.

이 사용 사례의 경우 사용 가능한 스웨터 수의 최고 값에 따라 화면에 빨간색, 녹색 또는 파란색 스웨터가 표시됩니다.

### 절차 {#procedure}

소매 인벤토리 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google Sheet로 이동합니다.
   1. 세 개의 서로 다른 스웨터에 해당하는 값과 함께 세 개의 열(빨강, 녹색 및 파랑)을 추가합니다.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **요구 사항에 따라 대상 구성**

   1. 대상의 세그먼트로 이동합니다(2단계(5단계)의 ***섹션:Google 시트의 컨텐츠를 가져오도록 AEM 구성***).
   1. 세 개의 새 세그먼트 For_ **Red**, **For_Green**&#x200B;및 **For_Blue를**&#x200B;추가합니다.

   1. For_ **Red를** 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   1. 비교를 드래그하여 **놓습니다.속성 -** 편집기에 대한 속성 및 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 첫 **번째 속성 이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 큼 **로 연산자를 선택합니다.

   1. 데이터 **유형을** **번호로 선택**

   1. 두 **번째 속성 이름의 드롭다운에서 워크시트/값/1/1** **을 선택합니다.**

   1. 드래그 앤 드롭 **또 다른 비교:속성 - 속성 **을 편집기에 입력하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 첫 **번째 속성 이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 큼 **로 연산자를 선택합니다.

   1. 데이터 **유형을** **번호로 선택**

   1. 두 **번째 속성 이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 **For_Blue** 세그먼트에 추가합니다.

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   마찬가지로 아래 그림과 같이 비교 속성 규칙을 편집하고 ** For_Green **segment에 추가합니다.

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   For_Green 및 **For_Green** 세그먼트의 경우 ****&#x200B;현재 Google Sheet의 값에 따라 첫 번째 비교만 유효하므로 데이터를 편집기에서 로드할 수 없습니다.

1. **DataDrivenRetail **채널(시퀀스 채널)을 탐색하여 선택하고 작업 **표시줄에서** 편집을 클릭합니다.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   위에 표시된 **이미지와 같이** 프로젝트에 **대해 ContextHub 구성을** 설정하는 **동안 타깃팅 구성 아래에 브랜드를** 추가하지 않는 경우 **다음 단계에서 타깃팅 프로세스를 시작하는 동안 BrandVertising 및 Hub 활동을** **** 선택해야 합니다.

1. **기본 이미지 추가**

   1. 채널에 기본 이미지를 추가하고 타깃팅을 **클릭합니다**.
   1. 드롭다운 **메뉴에서** 브랜드와 **활동을** 선택하고 타깃팅 **시작을**&#x200B;클릭합니다.

   1. **타깃팅 시작**&#x200B;을 클릭합니다.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   타게팅을 시작하기 전에 아래 그림과 같이 사이드 레일에서 경험 타게팅 추가&#x200B;******(For_Green**, For_Red 및 **For_Blue**)를 클릭하여 세그먼트를 추가해야 합니다 **** .

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 아래 표시된 대로 세 가지 다른 영역에 이미지를 추가합니다.

   ![retail_targeting](assets/retail_targeting.gif)

1. **미리 보기 확인**

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 세 개의 서로 다른 열 모두에 대한 값을 변경하면 재고 중 가장 높은 값에 따라 표시 이미지가 업데이트됩니다.
   ![retail_result](assets/retail_result.gif)

## 사용 사례 2:여행 센터 날씨 활성화 {#use-case-travel-center-weather-activation}

다음 사용 사례는 Google Sheet의 값을 기반으로 두 개의 다른 이미지를 보여 줍니다.

### 설명 {#description-1}

이 사용 사례의 경우 Google Sheets의 값이 50보다 작으면 따뜻한 음료가 포함된 이미지가 표시되고 값이 50보다 크거나 같으면 차가운 음료가 포함된 이미지가 표시됩니다. 다른 값 또는 값이 없는 경우 플레이어에 기본 이미지가 표시됩니다.

### 절차 {#procedure-1}

AEM Screens 프로젝트에 대한 여행 센터 날씨 활성화 사용 사례를 구현하려면 아래 절차를 따르십시오.

1. **Google 시트 채우기**

   1. ContextHubDemo Google Sheet로 이동합니다.
   1. 온도 값이 **있는 Heading1** 열을 추가합니다.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다(2단계(5단계)의 ***섹션:Google 시트의 컨텐츠를 가져오도록 AEM 구성***).
   1. 시트 A1 **을** 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**

   1. 드롭다운 **메뉴에서** **보다 크거나 같음 **연산자를 선택합니다.

   1. 값을 **50으로** 입력합니다 ****

   1. 마찬가지로* Sheets A1 2 **를 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/0** **을 선택합니다.**

   1. 드롭다운 **메뉴에서** **less-than **으로 연산자를 선택합니다.

   1. 값을 **50으로** 입력합니다 ****

1. 채널()을 탐색하고 선택하고 작업 **표시줄에서 편집을** 클릭합니다. 다음 예제에서는 **순차적 채널인 DataDrivenWeather**&#x200B;를 사용하여 기능을 표시합니다.

   >[!NOTE]
   채널에 이미 기본 이미지가 있어야 하며 대상은 단계(3)에 설명된 대로 미리 구성되어야 합니다.

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   위에 표시된 **이미지와 같이** 프로젝트에 **대해 ContextHub 구성을** 설정하는 **동안 타깃팅 구성 아래에 브랜드를** 추가하지 않는 경우 **다음 단계에서 타깃팅 프로세스를 시작하는 동안 BrandVertising 및 Hub 활동을** **** 선택해야 합니다.

1. 편집기에서 ******브랜드를** 선택하고 **드롭다운** 메뉴에서 **활동과**&#x200B;타깃팅 시작을클릭합니다.

   >[!NOTE]
   프로젝트에 **대해 ContextHub 구성을** 설정하는 **** 동안 타깃팅 구성 아래에 **브랜드를** 추가한 경우, 이 단계에서 **브랜드 및 활동** **** 단계를 선택할 필요가 없습니다.

   ![new_activity3](assets/new_activity3.gif)

1. 미리 보기 확인

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 값을 50세 미만으로 변경하면 여름 음료 이미지를 볼 수 있습니다. Google Sheet의 값이 50 이상인 경우, 핫 드링크의 이미지를 볼 수 있어야 합니다.
   ![result3](assets/result3.gif)

## 사용 사례 3:숙박 예약 활성화 {#use-case-hospitality-reservation-activation}

다음 사용 사례에서는 Google 시트에 적용된 값과 공식을 기준으로 두 개의 다른 이미지를 보여 줍니다.

### 설명 {#description-2}

이 사용 사례의 경우, Google Sheet는 두 개의 레스토랑 Restaurant Restaurant1 **과 Restaurant2** 중 예약 비율이 **채워집니다**. 수식은 Restaurant1 및 Restaurant2의 값을 기반으로 적용되며 공식을 기준으로 값 1 또는 2가 AdTarget 열에 **할당됩니다** .

Restaurant1 **Restaurant2****가**&#x200B;있는 경우 **AdTaget** 값이 1이면 **AdTarget** 이 1이면할당된 값 2가 됩니다. 값 1은 *스테이크 음식* 옵션을 생성하고 값 2는 *디스플레이 화면에 태국 음식* 옵션을 표시합니다.

### 절차 방법 {#procedural-approach}

아래 절차에 따라 AEM Screens 프로젝트에 대한 숙박 예약 활성화 사용 사례를 구현하십시오.

1. Google Sheet를 채우고 공식을 추가합니다.

   예를 들어 아래 그림과 같이 세 번째 열 AdTarget **에**&#x200B;공식을 적용합니다.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **요구 사항에 따라 대상에서 세그먼트 구성**

   1. 대상의 세그먼트로 이동합니다(2단계(5단계)의 ***섹션:Google 시트의 컨텐츠를 가져오도록 AEM 구성***).
   1. 시트 A1 **을** 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 드롭다운 **메뉴에서** **equal **로 연산자를 선택합니다.

   1. 값을 **1** **로 입력합니다.**

   1. 마찬가지로* Sheets A1 2 **를 선택하고 편집을 **클릭합니다**.

   1. 비교 속성을 선택하고 구성 아이콘을 클릭하여 속성을 편집합니다.
   1. 속성 **이름의 드롭다운에서 워크시트/값/1/2** **를 선택합니다.**

   1. 연산자를 **2** 로 선택합니다 ****

1. 채널()을 탐색하고 선택하고 작업 **표시줄에서 편집을** 클릭합니다. 다음 예제에서는 **DataDrivenRestaurant**&#x200B;순차적 채널을 사용하여 기능을 표시합니다.

   >[!NOTE]
   채널에 이미 기본 이미지가 있어야 하며 대상은 단계(3)에 설명된 대로 미리 구성해야 합니다.

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   채널 속성 —&gt; 개인화 **탭을 사용하여** **ContextHub** 구성을 **** 설정해야 **** 합니다.

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   위에 표시된 **이미지와 같이** 프로젝트에 **대해 ContextHub 구성을** 설정하는 **동안 타깃팅 구성 아래에 브랜드를** 추가하지 않는 경우 **다음 단계에서 타깃팅 프로세스를 시작하는 동안 BrandVertising 및 Hub 활동을** **** 선택해야 합니다.

1. 편집기에서 ******브랜드를** 선택하고 **드롭다운** 메뉴에서 **활동과**&#x200B;타깃팅 시작을클릭합니다.
1. 미리 보기 확인

   1. 미리 보기를 **클릭합니다.** 또한 Google Sheet를 열고 값을 업데이트합니다.
   1. Restaurant1 &gt; Restaurant2에서 값을 변경하면 스테이크의 이미지를 볼 수 있고 Restaurant1 &lt; Restaurant12에서는 타이 요리 사진을 디스플레이 화면에서 볼 수 있습니다.
   ![result5](assets/result5.gif)

## 사용 사례 4:디지털 메뉴 보드 텍스트 오버레이 {#use-case-digital-menu-board-text-overlay}

다음은 디지털 메뉴 보드 사용 사례를 보여줍니다. 일반적으로 레스토랑과 패스트푸드점에 많이 사용됩니다.

### 설명 {#description-3}

다음 사용 사례에서는 순차적 채널에서 텍스트 오버레이의 사용과 Google 시트의 가격 업데이트가 텍스트 오버레이 구성 요소 업데이트에서 업데이트를 트리거하는 방법에 대해 설명합니다.

### 절차 방법 {#procedural-approach-1}

아래 절차에 따라 AEM Screens 프로젝트에 대한 텍스트 오버레이 사용 사례와 함께 디지털 메뉴 보드를 구현하십시오.

1. **Google 시트 채우기**

   1. Google Sheets로 이동합니다.
   1. 아래 그림과 같이 사용 사례에 대한 가격 값이 있는 열을 추가합니다.
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **시퀀스 채널에 이미지 추가**

   1. 채널(DataDrivenAssets —&gt;**채널** —&gt; **DataDrivenTextOverlay** ) **을 찾아 선택합니다**.

   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.
   1. 편집기에서 사과 파이 이미지를 드래그하여 놓습니다.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **이미지에 텍스트 오버레이 추가**

   1. 편집기에서 이미지를 선택하고 구성을 클릭합니다.
   1. 텍스트 오버레이 **탭으로** 이동하여 이미지에 텍스트 오버레이를 추가합니다. Google Sheets에서 값을 가져오려면 값이 중괄호 안에 있어야 합니다. 예를 들어 가격은 google Sheet에서 가져오고 텍스트 오버레이를 정의하는 동안 **{price}** 로 언급됩니다.

   1. 아래 **그림과 같이 ContextHub** 탭으로 이동하여 google 시트에서 가져올 값을 구성합니다.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **미리 보기 확인**

   <!-- Edit text in steps below. wonky-->

   1. 미리 보기를 **클릭합니다**.  또한 Google Sheet를 열고 값을 업데이트합니다.
   1. 가격 아래의 **값을** 변경하면 아래 그림과 같이 텍스트 오버레이에 사용된 값이 그에 따라 업데이트됩니다.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
