---
title: 채널 지정
seo-title: 채널 지정
description: 채널 지정 및 한시적 분할에 대해 알려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 37%

---


# 채널 지정 {#channel-assignment}

디스플레이를 정의하고 나면 디스플레이에 채널을 지정해야 합니다.

이 페이지에서는 디스플레이에 채널을 지정하는 것을 보여줍니다.

>[!NOTE]
>디스플레이에 여러 채널을 지정할 수 있습니다.

## Assigning a Channel {#assign-a-channel}

아래 절차에 따라 디스플레이에 채널을 지정하십시오.

>[!I역정]
>채널 지정에 대한 다음 대화 상자는 Adobe Experience 6.5.5 Screens Feature Pack 릴리스 이상과 다릅니다. 자세한 내용은 [채널 지정을](/help/user-guide/channel-assignment.md#assign-a-channel-new-release) 참조하십시오.

1. 필요한 디스플레이(예: **DemoProject** —> **위치** —> **SanJose** —> Store **Display)로**&#x200B;이동합니다.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Tap/click **Assign Channel** in the action bar

   또는,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![이미지](/help/user-guide/assets/channel-assign1.png)

   아래 섹션에서 **채널 지정** 대화 상자에서 속성을 구성할 수 있습니다. 채널 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

## AEM 6.5.5 스크린 기능 팩 릴리스용 채널 할당 {#assign-a-channel-new-release}

아래 절차에 따라 디스플레이에 채널을 지정하십시오.

1. 필요한 디스플레이(예: **DemoProject** —> **위치** —> **SanJose** —> Store **Display)로**&#x200B;이동합니다.


1. Tap/click **Assign Channel** from the action bar

   또는,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS &amp; SCHEDULES** panel to open the **Channel Assignment** dialog box.

1. 설정 옵션에서 경로 또는 이름별로 채널을 선택하고 채널 역할, 우선 순위, 지원 이벤트를 입력합니다.

   >[!NOTE]
   >채널 속성에 대한 자세한 내용은 [채널](#channel-properties) 속성 섹션을 참조하십시오.

1. 예약 **옵션** 에서 **참조 시간대**, **활성화 창** 및 되풀이 **일정**&#x200B;을선택합니다.

1. 환경 **설정을** 구성했으면 저장을 클릭합니다.

### 채널 할당의 채널 속성 이해 {#channel-properties}

#### 참조 채널 {#ref-channel}

참조 채널을 사용하면 채널 이름 또는 채널 경로별로 원하는 채널에 대한 참조를 제공할 수 있습니다.

* **경로 기준**: 채널의 절대 경로를 사용하여 명시적 참조를 제공합니다.

* **이름별**:컨텍스트별로 실제 채널로 확인할 채널의 이름을 입력합니다. 이 기능을 사용하면 위치별 컨텐츠를 동적으로 확인할 수 있도록 채널의 로컬 버전을 만들 수 있습니다. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

#### 채널 역할 {#role-channel}

채널 역할은 디스플레이 컨텍스트를 정의합니다. 이 역할은 다양한 작업에 의해 타깃팅되며 역할을 수행하는 실제 채널과 독립적입니다.

#### 우선 순위 {#priority-channel}

우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있고 A의 우선 순위는 1이고 B의 우선 순위는 2라면, 채널 B의 우선 순위가 A보다 높으므로 채널 B가 표시됩니다.

>[!NOTE]
>채널의 우선 순위는 위에 언급된 대로 **채널 지정** 대화 상자에서 숫자(최소값은 1)로 설정됩니다. 또한, 지정된 채널은 내림차순의 우선 순위를 기준으로 정렬됩니다.

#### 지원되는 이벤트 {#supported-events-channel}

* **초기 로드**: 플레이어가 시작될 때 채널을 로드합니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
* **유휴 화면**: 화면이 유휴 상태일 때 로드됩니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
* **타이머**: 일정이 제공되면 설정해야 합니다.
* **사용자 상호 작용**: 유휴 채널에서 화면(터치)에 사용자 상호 작용이 있으면 플레이어가 지정된 채널로 전화되고 화면을 터치하면 로드됩니다.

#### 중단 방법 {#interruption-method-channel}

>[중요 사항]
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

#### 예약 {#schedule-channel}

일정을 사용하면 채널이 표시될 때 텍스트로 된 설명을 제공할 수 있습니다. It also let&#39;s you define a start date (**active from**) and an end date (**active until**) for the channel to be shown.

**명소 도구 설명 표시**:

[명소 도구 설명 표시]는 채널이 실행될 때 명소 도구 설명(&quot;*시작하려면 아무 데나 터치하세요*&quot;)을 표시해야 할지 여부를 정의합니다.

### 한시적 입찰 {#dayparting}

Schedules when combined with **Day-parting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

방송 시간 분할은 하루를 시간 슬롯으로 분할하고 원하는 시간에 재생되는 컨텐츠를 지정하는 것을 말합니다. AEM Screens을 사용하면 요구 사항에 따라 하루, 주 또는 월 내에 한시적으로 채널을 예약할 수 있습니다.

다음 예에서는 채널에서의 일별 분할을 세 가지 다른 시나리오로 설명합니다.

#### 여러 개의 시간 슬롯으로 분할된 하루의 컨텐츠 재생 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

이 예에서는 음식점이 어떻게 한시적 입찰을 사용하여 아침, 점심 및 저녁 메뉴를 선보이는지 보여줍니다.

여기서는 각 날을 세 개의 서로 다른 시간 슬롯으로 나누어 채널 컨텐츠가 지정된 시간에 따라 재생되도록 합니다.

| **채널** | **역할** | **우선 순위** | **예약** |
|---|---|---|---|
| Menu_A | 아침 식사 |  | 6:00 후 및 11:00 전 |
| Menu_B | 점심 |  | 11:00 후 및 15:00 전 |
| Menu_C | 저녁 식사 |  | 15:00 후 및 20:00 전 |

#### 특정 요일에 컨텐츠 재생 {#playing-content-on-a-particular-day-of-the-week}

이 예에서는 라이브 이벤트가 주말마다 오후 8시에서 오후 10시까지 진행되고 스페셜 메뉴가 오후 10시부터 오전 1시까지 저녁 메뉴에 포함되는 카지노에서 달성한 방송 시간 분할을 보여줍니다.

<table>
 <tbody>
  <tr>
   <td><strong>채널</strong></td>
   <td><strong>역할</strong></td>
   <td><strong>우선 순위</strong></td>
   <td><strong>예약</strong></td>
  </tr>
  <tr>
   <td>라이브 콘서트</td>
   <td>주말</td>
   <td> </td>
   <td>2017년 10월 21일 - 20:00 <br /> 이후 2017년 10월 22일 22:00 이전</td>
  </tr>
  <tr>
   <td>스페셜 디너</td>
   <td>주말</td>
   <td> </td>
   <td>2017년 10월 21일 - 2017년 10월 22일 <br /> 후 22:00분 전 1:00</td>
  </tr>
 </tbody>
</table>

#### 특정 달 동안의 컨텐츠 재생 {#playing-content-for-a-particular-month-months}

이 예에서는 6월부터 8월까지 여름 컬렉션을 표시하고 9월부터 10월 말까지 가을 컬렉션을 표시하는 점포의 한시적 입찰을 보여줍니다.

여기서는 지정된 연도의 달에 따라 채널 컨텐츠가 재생되도록 달에 따라 한시적 입찰을 만듭니다.

| **채널** | **역할** | **우선 순위** | **예약** |
|---|---|---|---|
| SummerCollection | 여름 |  | 2017년 6월 1일 - 2017년 8월 31일 |
| FallCollection | 가을 |  | 2017년 9월 1일 - 2017년 10월 30일 |

>[!NOTE]
>
>추가로, 각 채널에 대해 ***우선 순위***&#x200B;를 정의할 수 있습니다. 예를 들어, 동일한 날짜 및 시간 또는 동일한 달에 대해 두 개의 채널이 설정되면 우선 순위가 높은 채널이 먼저 재생됩니다. 우선 순위의 최소값은 0으로 설정할 수 있습니다.

#### 우선 순위가 같은 채널의 컨텐츠 재생 {#playing-content-for-channels-with-same-priority}

이 예에서는 12월의 동일한 일정과 함께 겨울 컬렉션을 표시하는 스토어에 대한 방송 시간 분할을 보여줍니다. 그러나 해당 주 동안 채널 B의 우선 순위가 2로 설정되었으므로 채널 A가 아니라 채널 B가 컨텐츠를 재생합니다.

| **채널** | **역할** | **우선 순위** | **예약** |
|---|---|---|---|
| A | 겨울 | 1 | 2017년 12월 1일 - 2017년 12월 31일 |
| B | 크리스마스 | 2 | 2017년 12월 24일 - 2017년 12월 31일 |


>[!IMPORTANT]
>
> 한시적 입찰에 대한 자세한 내용은 아래 섹션을 참조하십시오.
>
>* [자산의 되풀이 처리](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [채널에서 자산에 대한 되풀이 처리](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


