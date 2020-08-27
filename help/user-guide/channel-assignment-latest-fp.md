---
title: 채널 지정 - 최신 FP
seo-title: 채널 지정 - 최신 FP
description: 채널 지정 및 한시적 분할에 대해 알려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: f5d80f3765993277c552b64685d12244658915bb
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 23%

---


# 채널 지정 {#channel-assignment}

>[!IMPORTANT]
>이 섹션에서는 AEM 6.5.5 스크린 기능 팩 이상의 채널 지정 및 일정 관리를 집중적으로 설명합니다.

디스플레이를 설정한 후에는 컨텐츠를 보려면 디스플레이에 채널을 지정해야 합니다.

이 페이지에서는 디스플레이에 채널 지정, 채널 속성 이해 및 DayParting을 보여줍니다.

>[!NOTE]
>디스플레이에 여러 채널을 지정할 수 있습니다.


## Assigning a Channel {#assign-a-channel-new-release}

아래 섹션에 따라 AEM Screens 프로젝트를 만들고 디스플레이에 채널을 지정합니다.

### AEM Screens 프로젝트 및 채널 만들기 {#creating-project}

아래 절차에 따라 프로젝트 및 채널을 설정합니다.

1. DemoScreens라는 이름의 AEM Screens **프로젝트를 만듭니다**.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >AEM Screens 프로젝트 [를 만드는](creating-a-screens-project.md) 방법을 알려면 프로젝트 만들기 및 관리를 참조하십시오.

1. 채널 폴더에 **카페테리아라는** 이름의 시퀀스 채널을 **만듭니다** .

1. 채널을 선택하고 작업 표시줄에서 **편집을** 클릭하여 채널에 컨텐츠를 추가합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   예를 들어, **카페테리아** 채널은 이제 다음 이미지를 표시합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. SanJose라는 이름의 위치 **를 만들고** Lobby로 **표시합니다**.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 디스플레이에 채널 지정 {#assigning-channel-to-display}

프로젝트 설정이 완료되면, 컨텐츠를 보려면 디스플레이에 채널을 지정해야 합니다.

1. 필요한 디스플레이(예: **DemoScreens** —> **위치** —> **SanJose** —> **LobbyCover**&#x200B;로이동합니다.

1. Tap/click **Assign Channel** from the action bar.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   또는,

   작업 표시줄에서 **대시보드** 를 탭/클릭하고 지정된 채널 및 일정 **패널에서** 채널 **지정을** 클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. [ **설정** ] 옵션 **에서 이름별로 경로** 또는 경로 **별로 채널을 선택하고, 역할**, 채널, **채널PriorityPriority**, 지원되는Events,지원되는Events, 및Safety ************&#x200B;와 SafetyAInterftion Methods를 입력합니다. 또한 이 대화 상자에서 명소 도구 설명을 활성화할 수 있습니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >채널 지정 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

1. 예약 **옵션** 에서 **참조 시간대**, **활성화 창** 및 되풀이 **일정**을선택합니다.
   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >채널 지정 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

1. 환경 **설정을** 구성했으면 저장을 클릭합니다.

### Chrome Player에서 콘텐트 보기 {#viewing-content-output}

이 예에서는 Chrome Player에서 출력을 보여 줍니다. 디스플레이에 채널을 지정했으면 플레이어를 플레이어에 등록해야 합니다.

AEM Screens 플레이어에서 [장치를 등록하는](device-registration.md) 방법은 장치 등록을 참조하십시오.

플레이어를 선택한 경우 다음 출력을 볼 수 있습니다.

![new1](assets/channel-assignment/channel-assign-output.gif)

## Timeline View {#timeline-view}

디스플레이에 채널을 지정하고 되풀이 일정을 설정했으면 지정된 채널 및 일정 **패널에서 타임라인을** 볼 수 있습니다.

아래 절차에 따라 타임라인 보기로 이동합니다.

1. 필요한 디스플레이(예: **DemoScreens** —> **위치** —> **SanJose** —> **LobbyCover**&#x200B;로이동합니다.

1. Tap/click **Assign Channel** from the action bar.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   또는,

   대시보드 **를 탭/클릭하고** 지정된 채널 **및 일정** 패널에서 **** 타임라인을클릭합니다.

1. 보류 중인 이미지(수정됨)

## 채널 지정 대화 상자에서 채널 속성 이해 {#channel-properties}

다음 속성은 채널 지정 대화 상자의 **설정** 옵션 **에서** 설정됩니다.

![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 채널 선택 {#select-channel}

채널을 선택하면 채널 이름 또는 채널 경로별로 원하는 채널에 대한 참조를 제공할 수 있습니다.

* **경로 기준**: 채널의 절대 경로를 사용하여 명시적 참조를 제공합니다.

* **이름별**:컨텍스트별로 실제 채널로 확인할 채널의 이름을 입력합니다. 이 기능을 사용하면 위치별 컨텐츠를 동적으로 확인할 수 있도록 채널의 로컬 버전을 만들 수 있습니다. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

### 채널 역할 {#role-channel}

채널 역할은 디스플레이 컨텍스트를 정의합니다. 이 역할은 다양한 작업에 의해 타깃팅되며 역할을 수행하는 실제 채널과 독립적입니다.

### 우선 순위 {#priority-channel}

우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있고 A의 우선 순위는 1이고 B의 우선 순위는 2라면, 채널 B의 우선 순위가 A보다 높으므로 채널 B가 표시됩니다.

>[!NOTE]
>채널의 우선 순위는 위에 언급된 대로 **채널 지정** 대화 상자에서 숫자(최소값은 1)로 설정됩니다. 또한, 지정된 채널은 내림차순의 우선 순위를 기준으로 정렬됩니다.

### 지원되는 이벤트 {#supported-events-channel}

* **초기 로드**: 플레이어가 시작될 때 채널을 로드합니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
* **유휴 화면**: 화면이 유휴 상태일 때 로드됩니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
* **타이머**: 일정이 제공되면 설정해야 합니다.
* **사용자 상호 작용**: 유휴 채널에서 화면(터치)에 사용자 상호 작용이 있으면 플레이어가 지정된 채널로 전화되고 화면을 터치하면 로드됩니다.

### 중단 방법 {#interruption-method-channel}

>[!IMPORTANT]
>
> 이 옵션은 AEM 6.4 기능 팩 8 또는 AEM 6.5 기능 팩 4에서만 사용할 수 있습니다.

컨텐츠 작성자는 채널이 중단되는 시점을 지정할 수 있으므로 중요하지 않은 컨텐츠를 차단하도록 선택할 수 있지만 일정 때문에 재생을 중단하기 전에 중요한 컨텐츠가 완전히 재생되도록 할 수 있습니다.

채널 지정 대화 상자에서 중단 방법을 설정하는 데 사용할 수 있는 다음 옵션 중 하나를 **선택합니다** .

* **즉시**:일정이 활성화되거나 업데이트가 수신될 때마다 재생을 중단하고 즉시 새 컨텐츠를 새로 고치거나 재생할 수 있습니다
* **현재 항목**&#x200B;끝:새 일정이 활성화되거나 업데이트가 수신되면 시퀀스의 현재 항목이 재생을 완료할 때까지 기다릴 수 있는 옵션을 사용할 수 있습니다. 단, 새 컨텐츠를 새로 고치거나 재생한 후에만 가능합니다
   >[!NOTE]
   >이 옵션은 기본적으로 선택되어 있습니다.
* **시퀀스**&#x200B;끝:새 일정이 활성화되거나 업데이트가 수신되면 전체 시퀀스가 해당 끝에 도달할 때까지 기다리는 옵션을 사용할 수 있으며 원하는 시퀀스 바로 전에 첫 번째 요소로 다시 루프하면 새 컨텐츠를 새로 고치거나 재생할 수 있습니다

   >[!NOTE]
   >두 번째 또는 세 번째 옵션을 사용하면 플레이어가 새로 고치기 전에 항목이나 시퀀스의 끝(지정된 시간 후)을 기다리기 때문에 할당에 정의된 예약 시간이 약간 지연될 수 있습니다. 지연 시간은 항목의 재생 기간에 따라 다릅니다.


다음 속성은 채널 지정 대화 상자의 **예약** 옵션 **에서** 설정됩니다.

### 참조 시간대 {#reference-timezone}

참조 시간대를 사용하면 컨텐츠 표시 시간대를 선택할 수 있습니다.

### 활성화 창 {#activation-window}

활성화 창을 사용하면 컨텐츠를 표시할 **시작 날짜** 및 **종료 날짜를** 선택할 수 있습니다.

### 재현 예약 {#recurrence-schedule}

되풀이 일정을 사용하면 컨텐츠에 대한 반복 일정을 설정할 수 있습니다. 채널에 반복 일정을 추가하려면 **+ 일정** 추가를 클릭합니다.

![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)


>[!NOTE]
>여러 개의 반복되는 일정을 채널에 추가할 수 있습니다.
>Recurrence Schedules introduces *DayParting*, that allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

다음 옵션을 설정할 수 있습니다.

* **이름**:되풀이 일정의 제목입니다.
* **반복**:일정이 **일별**, **주별**, **월별****또는**&#x200B;연간을실행할지 여부를 선택합니다.
* **시작**:일정의 시작 시간입니다.
* **끝**:일정의 종료 시간입니다. 다음을 통해 설정할 수 있습니다.
* **시간**:일정은 지정된 시간에 종료됩니다.
* **지속 시간**:특정 시간(시간 또는 분)에 대해 일정이 실행됩니다.

### DayParting {#dayparting}

방송 시간 분할은 하루를 시간 슬롯으로 분할하고 원하는 시간에 재생되는 컨텐츠를 지정하는 것을 말합니다. AEM Screens을 사용하면 요구 사항에 따라 하루, 주 또는 월 내에 채널 일정을 지정할 수 있습니다.

다음 예에서는 채널의 DayParting에 대해 세 가지 다른 시나리오로 설명합니다.

#### 여러 개의 시간 슬롯으로 분할된 하루의 컨텐츠 재생 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

이 예에서는 음식점이 어떻게 DayParting을 사용하여 매일 아침, 점심 및 저녁 메뉴를 선보이는지 보여줍니다.

여기서는 각 날을 다른 시간 슬롯으로 나누어 채널 컨텐츠가 지정된 시간에 따라 재생되도록 합니다. 이 사용 사례에 따라 컨텐트를 재생하려면 채널에 대해 되풀이 일정의 다음 속성을 설정합니다.

| **이름** | **반복** | **시작** | **끝** |
|---|---|---|---|
| 아침 식사 | 일별 | 오전 6:00 | 오전 11:00 |
| 점심 | 일별 | 오전 11:02 | 오후 3:00 |
| 저녁 식사 | 일별 | 오후 3:01 | 오후 8:00 |

#### 특정 요일에 컨텐츠 재생 {#playing-content-on-a-particular-day-of-the-week}

이 예에서는 라이브 이벤트가 주말마다 오후 8:00부터 오후 10:00까지 발생하는 카지노에 구현된 DayParting을 보여주며 스페셜 메뉴는 오후 10:00부터 오전 1:00까지 저녁 메뉴에 사용할 수 있습니다.

| **이름** | **반복** | **시작** | **끝** |
|---|---|---|---|
| 주말 | 매주 | 오후 8:00 | 오후 10:00 |
| 특수 | 일별 | 오후 10:00 | 오전 1:00 |

>[!NOTE]
>
>추가로, 각 채널에 대해 ***우선 순위***&#x200B;를 정의할 수 있습니다. 예를 들어, 동일한 날짜 및 시간 또는 동일한 달에 대해 두 개의 채널이 설정되면 우선 순위가 높은 채널이 먼저 재생됩니다. 우선 순위의 최소값은 0으로 설정할 수 있습니다.

