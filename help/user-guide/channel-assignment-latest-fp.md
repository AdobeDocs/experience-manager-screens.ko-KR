---
title: 채널 할당 - 최신 FP
description: 채널 할당 및 시간대 지정에 대해 알아봅니다.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 2%

---

# 채널 지정 {#channel-assignment}

>[!IMPORTANT]
>
>이 섹션에서는 AEM 6.5.5 Screens 기능 팩 이상에 대한 채널 할당 및 채널 일정을 중점적으로 다룹니다.

디스플레이를 설정한 경우 디스플레이에 채널을 할당하여 콘텐츠를 봅니다.

이 페이지에는 디스플레이에 채널 할당, 채널 속성 이해 및 DayParting이 표시됩니다.

>[!NOTE]
>
>디스플레이에 여러 채널을 할당할 수 있습니다.


## 채널 할당 {#assign-a-channel-new-release}

아래 섹션에 따라 AEM Screens 프로젝트를 만들고 채널을 디스플레이에 할당합니다.

### AEM Screens 프로젝트 및 채널 만들기 {#creating-project}

프로젝트 및 채널을 설정하려면 아래 단계를 따르십시오.

1. 제목이 **DemoScreens**&#x200B;인 AEM Screens 프로젝트를 만듭니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >AEM Screens 프로젝트를 만드는 방법에 대해 알아보려면 [프로젝트 만들기 및 관리](creating-a-screens-project.md)를 참조하십시오.

1. **채널** 폴더에서 **카페테리아**(으)로 제목이 지정된 시퀀스 채널을 만듭니다.

1. 채널을 클릭한 다음 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   예를 들어 이제 **카페테리아** 채널에 다음 이미지가 표시됩니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 제목이 **산호세**&#x200B;이고 디스플레이가 **로비**&#x200B;인 위치를 만드십시오.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 디스플레이에 채널 할당 {#assigning-channel-to-display}

프로젝트 설정이 완료되면 콘텐츠를 볼 수 있도록 채널을 디스플레이에 할당합니다.

1. 필요한 디스플레이로 이동합니다(예: **DemoScreens** > **위치** > **산호세** > **로비**).

1. 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   또는,

   작업 표시줄에서 **대시보드**&#x200B;를 클릭하고 **할당된 채널 및 일정** 패널에서 **+채널 할당**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. **채널 할당** 대화 상자가 열립니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. **설정** 옵션에서 경로별 **또는 이름별**&#x200B;채널&#x200B;**을 선택하고**&#x200B;채널 역할&#x200B;**,**&#x200B;우선 순위&#x200B;**,**&#x200B;지원되는 이벤트&#x200B;**및**&#x200B;중단 방법&#x200B;**을 입력할 수 있습니다.** 또한 이 대화상자에서 명소 도구 설명을 활성화할 수 있습니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >채널 할당 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

1. **일정** 옵션에서 **활성화 기간** 및 **반복 일정**&#x200B;을 클릭합니다.
   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >채널 할당 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

1. 환경 설정을 구성했으면 **저장**&#x200B;을 클릭합니다.

### Chrome Player에서 컨텐츠 보기 {#viewing-content-output}

이 예는 Chrome 플레이어의 출력을 보여 줍니다. 디스플레이에 채널을 할당하면 플레이어에 장치를 등록합니다.

AEM Screens 플레이어에서 장치를 등록하는 방법에 대해 알아보려면 [장치 등록](device-registration.md)을 참조하세요.

플레이어를 선택하면 다음 출력을 볼 수 있습니다.

![new1](assets/channel-assignment/channel-assign-output.gif)

## 타임라인 보기 {#timeline-view}

디스플레이에 채널을 할당하고 반복 일정을 설정하면 **할당된 채널 및 일정** 패널에서 타임라인을 볼 수 있습니다.

아래 단계에 따라 타임라인 보기로 이동합니다.

1. 필요한 디스플레이로 이동합니다(예: **DemoScreens** > **위치** > **산호세** > **로비**).

1. 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

   또는,

   **대시보드**&#x200B;를 클릭하고 **할당된 채널 및 일정** 패널에서 **타임라인**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 채널 지정 대화 상자의 채널 속성 이해 {#channel-properties}

다음 속성은 **채널 할당** 대화 상자의 **설정** 옵션에서 설정됩니다.

![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 채널 선택 {#select-channel}

채널을 선택하면 채널 이름이나 채널 경로로 원하는 채널에 대한 참조를 제공할 수 있습니다.

* **경로별** - 채널의 절대 경로를 사용하여 명시적 참조를 제공합니다.
* **이름별** - 컨텍스트별로 실제 채널로 확인되는 채널의 이름을 입력합니다. 이 기능을 사용하면 위치별 콘텐츠를 동적으로 해결할 수 있도록 채널의 로컬 버전을 만들 수 있습니다. 예를 들어, 이름이 *오늘의 거래*&#x200B;인 채널이 있습니다. 여기서 실제 컨텐츠는 두 도시마다 다르지만 모든 디스플레이에는 여전히 올바른 채널 역할이 있습니다.

### 채널 역할 {#role-channel}

채널 역할은 디스플레이의 컨텍스트를 정의합니다. 다양한 작업이 역할을 타겟팅합니다. 역할을 수행하는 실제 채널과는 독립적입니다.

### 우선 순위 {#priority-channel}

여러 할당이 재생 기준과 일치하는 경우 우선 순위를 사용하여 할당을 정렬합니다. 값이 가장 높은 것이 항상 낮은 값보다 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있는 경우. A는 우선 순위가 1이고 B는 우선 순위가 2이므로 A보다 우선 순위가 높은 채널 B가 표시됩니다.

>[!NOTE]
>
>채널의 우선 순위는 위에서 설명한 대로 **채널 할당** 대화 상자에서 숫자(최소 1)로 설정됩니다. 또한 할당된 채널은 내림차순 우선 순위를 기준으로 정렬됩니다.

### 지원되는 이벤트 {#supported-events-channel}

* **초기 로드** - 플레이어가 시작될 때 채널을 로드합니다. 일정이 있는 여러 채널에 할당할 수 있습니다.
* **유휴 화면** - 화면이 유휴 상태일 때 로드됩니다. 일정이 있는 여러 채널에 할당할 수 있습니다.
* **타이머** - 일정을 제공할 때 설정해야 합니다.
* **사용자 상호 작용** - 플레이어가 유휴 채널에서 화면 상의 사용자 상호 작용(터치)이 있는 경우 지정된 채널로 전환하고 화면을 터치하면 로드됩니다.

### 중단 방법 {#interruption-method-channel}

>[!IMPORTANT]
> 이 옵션은 <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 기능 팩 4에서만 사용할 수 있습니다.

콘텐츠 작성자는 채널이 중단되는 시기를 지정할 수 있습니다. 이렇게 하면 중요하지 않은 콘텐츠를 차단할 수 있습니다. 그러나 일정 조정으로 인해 중요한 콘텐츠가 짧게 줄어들기 전에 완전히 재생되도록 하는 옵션도 제공됩니다.

**채널 할당** 대화 상자에서 중단 방법을 설정하는 데 사용할 수 있는 다음 옵션 중 하나를 선택하십시오.

* **즉시** - 일정이 활성화되거나 업데이트가 수신될 때마다 재생을 중단하고 새 콘텐츠를 즉시 새로 고치거나 재생할 수 있습니다.
* **현재 항목의 끝** - 새 일정이 활성화되거나 업데이트가 수신되면 선택적으로 시퀀스의 현재 항목이 재생을 완료할 때까지 대기할 수 있습니다. 그런 다음 그 이후에만 새 콘텐츠를 새로 고치거나 재생할 수 있습니다.

  >[!NOTE]
  >이 옵션은 기본적으로 선택되어 있습니다.

* **시퀀스가 끝날 때** - 새 일정이 활성화되거나 업데이트가 수신되면 전체 시퀀스가 끝날 때까지 대기할 수도 있습니다. 그런 다음 원하는 시퀀스 바로 전에 첫 번째 요소로 다시 루프백하거나 새로 고침하거나 새 콘텐츠를 재생할 수 있습니다.

  >[!NOTE]
  >두 번째 또는 세 번째 옵션을 사용하면 할당에 정의된 스케줄링 시간이 약간 지연될 수 있습니다. 그 이유는 플레이어가 새로 고치기 전에 항목 또는 시퀀스가 끝날 때까지(지정된 시간 후) 대기하기 때문입니다. 지연은 항목의 재생 기간에 따라 다릅니다.

다음 속성은 **채널 할당** 대화 상자의 **일정** 옵션에서 설정됩니다.

![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 활성화 창 {#activation-window}

활성화 창에서는 콘텐츠를 표시할 **시작 날짜** 및 **종료 날짜**&#x200B;를 선택할 수 있습니다.

### 재현 예약 {#recurrence-schedule}

반복 일정을 사용하면 콘텐츠에 대한 반복 일정을 설정할 수 있습니다. **+ 일정 추가**&#x200B;를 클릭하여 채널에 되풀이 일정을 추가합니다.

>[!NOTE]
>채널에 여러 개의 반복 일정을 추가할 수 있습니다.
>자동연장 일정에서 *DayParting*&#x200B;을(를) 도입했습니다. 하루 중 특정 시간에 여러 채널이 실행되는 글로벌 일정을 설정하고 모든 디스플레이에 대해 설정된 일정을 한 번에 재사용합니다.

다음 옵션을 설정할 수 있습니다.

* **이름** - 되풀이 일정의 제목입니다.
* **반복** - 일정이 **일별**, **주별**, **월별** 또는 **연간**&#x200B;로 실행되는지 여부를 선택합니다.
* **시작** - 일정 시작 시간입니다.
* **종료** - 일정 종료 시간. 시간 또는 기간에 따라 설정할 수 있습니다.
   * **시간** - 지정한 시간에 일정이 종료됩니다.
   * **기간** - 일정은 시간 또는 분 단위의 특정 기간 동안 실행됩니다.

### 시간대 지정 {#dayparting}

일 분할은 하루를 시간 슬롯으로 분할하고 원하는 시간에 재생할 콘텐츠를 지정하는 것을 의미합니다. AEM Screens을 사용하면 요구 사항에 따라 일, 주 또는 월 단위로 DayParting 조건으로 채널을 예약할 수 있습니다.

다음 예제에서는 세 가지 시나리오에서 채널의 DayParting을 설명합니다.

#### 여러 개의 시간 슬롯으로 분할된 하루 동안 콘텐츠 재생 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

이 예는 레스토랑이 DayParting을 사용하여 매일 아침, 점심 및 저녁 메뉴를 선보이는 방법을 보여줍니다.

여기서, 매일은 상이한 시간 슬롯들로 분할되어, 채널 콘텐츠는 그 날의 지정된 시간에 따라 재생된다. 이 사용 사례에 따라 콘텐츠를 재생하려면 채널에 대한 반복 예약의 다음 속성을 설정하십시오.

| **이름** | **반복** | **시작** | **종료** |
|---|---|---|---|
| 아침 식사 | 일별 | 오전 6시 | 오전 11시 |
| 점심 | 일별 | 오전 11시 | 오후 3시 |
| 저녁식사 | 일별 | 오후 3시 | 오후 8시 |

#### 특정 요일에 콘텐츠 재생 {#playing-content-on-a-particular-day-of-the-week}

이 예에서는 매주 주말 오후 8시부터 오후 10시까지 라이브 이벤트가 발생하고 오후 10시 이후부터 오전 1시까지 디너 메뉴에 대한 스페셜이 제공되는 카지노에서 구현된 DayParting을 보여 줍니다.

| **이름** | **반복** | **시작** | **종료** |
|---|---|---|---|
| 주말 | 주별: 토요일 및 일요일 | 오후 8시 | 오후 10시 |
| 특별 광고 | 매일: 월요일부터 금요일까지 | 오후 10시 | 오전 1시 |

>[!NOTE]
>
>또한 각 채널에 대해 ***우선 순위***&#x200B;를 정의할 수 있습니다. 예를 들어, 두 개의 채널이 같은 날 및 시간 또는 같은 달에 대해 설정된 경우 우선 순위가 높은 채널이 먼저 재생됩니다. 우선 순위의 최소값은 0으로 설정할 수 있습니다.
