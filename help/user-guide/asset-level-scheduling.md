---
title: 자산 수준 예약
seo-title: 자산 수준 예약
description: 플레이어의 로컬 표준 시간대에서 예약된 시간대에 대해 채널에서 특정 자산을 활성화하는 방법을 알아보려면 이 페이지를 따르십시오.
seo-description: 플레이어의 로컬 표준 시간대에서 예약된 시간대에 대해 채널에서 특정 자산을 활성화하는 방법을 알아보려면 이 페이지를 따르십시오.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: da25cdc7-c814-493e-8d8e-b6191fee2831
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 자산 수준 예약 {#asset-level-scheduling}


이 섹션에서는 채널에 사용된 자산에 대한 자산 수준 예약에 대해 설명합니다.

이 섹션에서는 다음과 같은 주제를 다룹니다.

* OverviewW
* 자산 레벨 스케줄링 사용
* 자산에서 되풀이 처리
* 다중 자산 예약


>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.3 Feature Pack 3 또는 AEM 6.4 Screens 기능 팩 1을 설치한 경우에만 사용할 수 있습니다.
>
>이 Feature Pack에 액세스하려면 Adobe 지원 센터에 연락하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.

## 개요 {#overview}

***자산 수준***&#x200B;예약을 사용하면 플레이어의 로컬 시간대에서 예약된 시간대에 대해 채널에서 특정 자산을 활성화할 수 있습니다. 이미지, 비디오, 전환, 페이지 및 포함된 채널(동적 또는 정적)에 사용할 수 있습니다.

*예를 들어*, 월요일과 수요일에 해피아워(2PM ~ 5PM) 동안에만 특별 프로모션을 표시하고자 합니다.

이 기능을 사용하면 시작 및 종료 날짜와 시간을 지정할 수 있을 뿐만 아니라 되풀이 패턴도 지정할 수 있습니다.

## 자산 레벨 스케줄링 사용 {#using-asset-level-scheduling}

자산 수준 예약은 자산의 속성에 액세스하는 **동안 활성화** 탭을 구성하여 수행합니다.

아래 절차에 따라 자산 수준 예약을 수행합니다.

1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 채널에서 컨텐츠를 추가하거나 편집합니다.

   ![screen_shot_2018-04-23at111422am](assets/screen_shot_2018-04-23at111422am.png)

   >[!NOTE]
   >
   >자세한 내용
   >
   >* 프로젝트 만들기를 참조하십시오 [](creating-a-screens-project.md).
   >* 채널에 컨텐츠를 만들고 추가합니다. 채널 관리를 [참조하십시오](managing-channels.md).


1. 편집을 **클릭하여** 채널 편집기를 열고 예약을 적용할 자산을 선택합니다.

   ![screen_shot_2018-04-24at90434pm](assets/screen_shot_2018-04-24at90434pm.png)

1. 자산을 선택하고 왼쪽 상단의 구성 **아이콘을 클릭하여** 이미지의 속성을 엽니다.

   Click the **Activation** tab.

   ![screen_shot_2018-04-23at112348am](assets/screen_shot_2018-04-23at112348am.png)

1. 활성 시작 날짜 및 활성 날짜 **필드에서** 날짜 선택부터 **필드까지** 날짜를 지정할 수있습니다.

   활성 시작 **및** 활성 **** 날짜 및 시간을 선택하면 자산이 각각 해당 시작 날짜/시간과 종료 날짜/시간 간에만 표시되고 반복됩니다.

   ![screen_shot_2018-04-23at113545am](assets/screen_shot_2018-04-23at113545am.png)

## 자산에서 되풀이 처리 {#handling-recurrence-in-assets}

요구 사항에 따라 일별, 주별 또는 월별 기준으로 특정 간격으로 반복되도록 자산을 예약할 수 있습니다.

금요일 오후 1시부터 오후 10시까지만 이미지를 표시한다고 가정합니다. 활성화 탭을 사용하여 자산의 반복 간격을 설정할 수 있습니다.

### 자산에 대한 반복 이벤트 추가 {#adding-a-recurring-event-for-your-asset}

1. 자산을 선택하고 구성 **아이콘을 클릭하여** 속성 대화 상자를 엽니다.
1. 시작 날짜/시간 및 종료/날짜 시간을 입력한 후 cron 표현식 또는 자연어 텍스트 버전을 사용하여 되풀이 일정을 지정할 수 있습니다.

   웹에서 무료 cron 표현식 생성기를 검색한 다음 cron 표현식을 복사하여 Schedule **에** 붙여 넣으면 특정 시간 간격 동안 자산이 표시됩니다.

   *또는* cron 표현식을 사용하는 대신, 금요일에 6시 *이후나 18시 이전과 같은 자연어 텍스트 버전을 사용하여 작업을 수행할* 수도 있습니다. 자산을 표시할 **예약에** 텍스트를 입력합니다.

## 다중 자산 예약 {#multi-asset-scheduling}

>[!CAUTION]
>
>다중 **자산** 예약 기능은 AEM 6.3 기능 팩 5 또는 AEM 6.4 기능 팩 3을 설치한 경우에만 사용할 수 있습니다.

***다중 자산 예약을*** 사용하면 여러 자산을 선택하고 선택한 모든 자산에 재생 일정을 적용할 수 있습니다.

### 전제 조건 {#prerequisites}

자산에 대해 다중 자산 수준 예약을 사용하려면 시퀀스 채널이 있는 AEM Screens 프로젝트를 만드십시오. 예를 들어 다음 사용 사례에서는 기능 구현을 보여줍니다.

* MultiAssetDemo라는 이름의 AEM Screens 프로젝트 **만들기**
* 아래 그림과 같이 MultiAssetChannel **이라는** 이름의 채널을 만들고 채널에 컨텐츠를 추가합니다.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

아래 절차에 따라 여러 자산을 선택하고 AEM Screens 프로젝트에서 해당 표시를 예약하십시오.

1. Select **MultiAssetChannel** and click **Edit** from the action bar to open the editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. 편집기에서 여러 자산을 선택하고 활성화 편집( **왼쪽 상단 아이콘** )을 클릭합니다.

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. 활성 시작 날짜 및 **활성** 날짜 및 시간을 구성 요소 **활성화** 대화 **상자에서** 선택합니다. 예약 선택이 완료되면 확인 표시 아이콘을 클릭합니다.

   ![screen_shot_2018-12-17at2037pm](assets/screen_shot_2018-12-17at20337pm.png)

1. 다중 자산 일정이 적용되는 자산을 확인하려면 새로 고침을 클릭합니다.

   >[!NOTE]
   >
   >일정 아이콘은 다중 자산 예약이 있는 자산의 오른쪽 상단에 표시됩니다.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

