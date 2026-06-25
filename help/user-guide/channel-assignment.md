---
title: 채널 할당
description: 채널 할당 및 시간대 지정에 대해 알아봅니다.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
TQID: https://experienceleague.adobe.com/3KiJEdVpZNlcvEo9PBzkyYJqIsQfBgXQY7-HlZZVxVE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: d4878390-3838-4e80-8cb3-33bc1a01ea16
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 1285
ht-degree: 2%

---

# 채널 할당 {#channel-assignment}

>[!IMPORTANT]
>이 섹션에서는 AEM 6.5.5 Screens 버전 이전의 기능 팩에 대한 채널 할당 및 채널 예약을 강조 표시합니다.

디스플레이를 설정한 경우 디스플레이에 채널을 할당하여 콘텐츠를 봅니다.

이 페이지에는 디스플레이에 대한 채널 할당이 표시됩니다.

이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

>[!NOTE]
>디스플레이에 여러 채널을 할당할 수 있습니다.

## 채널 할당 {#assign-a-channel}

채널을 디스플레이에 할당하려면 아래 단계를 따르십시오.

1. 필요한 디스플레이로 이동합니다(예: **DemoProject** > **위치** > **산호세** > **스토어 디스플레이**).

   ![이미지](assets/screen_shot_2018-08-23at25359pm.png)

1. 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

   또는,

   **대시보드**&#x200B;를 클릭하고 **할당된 채널** 패널에서 **+채널 할당**&#x200B;을 클릭하여 **채널 할당** 대화 상자를 열 수 있습니다.

   ![이미지](/help/user-guide/assets/channel-assign1.png)

   아래 섹션의 **채널 할당** 대화 상자에서 속성을 구성할 수 있습니다. 채널 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

## 채널 지정의 채널 속성 이해 {#channel-properties}

### 참조 채널 {#ref-channel}

참조 채널을 사용하면 채널 이름이나 채널 경로로 원하는 채널에 대한 참조를 제공할 수 있습니다.

* **경로별** - 채널의 절대 경로를 사용하여 명시적 참조를 제공합니다.

* **이름별** - 컨텍스트별로 실제 채널로 확인되는 채널의 이름을 입력합니다. 이 기능을 사용하면 위치별 콘텐츠를 동적으로 해결할 수 있도록 채널의 로컬 버전을 만들 수 있습니다. 예를 들어, 이름이 *오늘의 거래*&#x200B;인 채널이 있습니다. 여기서 실제 컨텐츠는 두 도시마다 다르지만 모든 디스플레이에는 여전히 올바른 채널 역할이 있습니다.

### 채널 역할 {#role-channel}

채널 역할은 디스플레이의 컨텍스트를 정의합니다. 역할은 다양한 작업을 대상으로 하며 역할을 수행하는 실제 채널과는 독립적입니다.

### 우선 순위 {#priority-channel}

여러 할당이 재생 기준과 일치하는 경우 우선 순위를 사용하여 할당을 정렬합니다. 값이 가장 높은 것이 항상 낮은 값보다 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있는 경우. A는 우선 순위가 1이고 B는 우선 순위가 2이므로 A보다 우선 순위가 높은 채널 B가 표시됩니다.

>[!NOTE]
>채널의 우선 순위는 위에서 설명한 대로 **채널 할당** 대화 상자에서 숫자(최소 1)로 설정됩니다. 또한 할당된 채널은 내림차순 우선 순위를 기준으로 정렬됩니다.

### 지원되는 이벤트 {#supported-events-channel}

* **초기 로드** - 플레이어가 시작될 때 채널을 로드합니다. 일정이 있는 여러 채널에 할당할 수 있습니다.
* **유휴 화면** - 화면이 유휴 상태일 때 로드됩니다. 일정이 있는 여러 채널에 할당할 수 있습니다.
* **타이머** - 일정을 제공할 때 설정해야 합니다.
* **사용자 상호 작용** - 플레이어가 유휴 채널에서 화면 상의 사용자 상호 작용(터치)이 있는 경우 지정된 채널로 전환하고 화면을 터치하면 로드됩니다.

### 중단 방법 {#interruption-method-channel}

>[!IMPORTANT]
>
> 이 옵션은 <!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 기능 팩 4에서만 사용할 수 있습니다.

콘텐츠 작성자는 채널이 중단되는 시기를 지정합니다. 필요한 경우 중요하지 않은 콘텐츠를 차단할 수 있지만, 예약으로 인해 재생을 차단하기 전에 중요한 콘텐츠를 재생할 수도 있습니다.

**채널 할당** 대화 상자에서 중단 방법을 설정하는 데 사용할 수 있는 다음 옵션 중 하나를 클릭합니다.

* **즉시** - 일정이 활성화되거나 업데이트가 수신될 때마다 재생을 중단하고 새 콘텐츠를 즉시 새로 고치거나 재생할 수 있습니다.
* **현재 항목의 끝** - 새 일정이 활성화되거나 업데이트가 수신되면 선택적으로 시퀀스의 현재 항목이 재생을 마칠 때까지 대기할 수 있습니다. 그 후에만 새 콘텐츠를 새로 고치거나 재생할 수 있습니다.

  >[!NOTE]
  >이 옵션은 기본적으로 선택되어 있습니다.
* **시퀀스가 끝날 때** - 새 일정이 활성화되거나 업데이트가 수신되면 전체 시퀀스가 끝날 때까지 대기할 수도 있습니다. 그런 다음 원하는 시퀀스 바로 전에 첫 번째 요소로 다시 루프백하거나 새로 고침하거나 새 콘텐츠를 재생할 수 있습니다.

  >[!NOTE]
  >두 번째 또는 세 번째 옵션을 사용하면 할당에 정의된 스케줄링 시간이 약간 지연될 수 있습니다. 그 이유는 플레이어가 새로 고치기 전에 항목 또는 시퀀스가 끝날 때까지(지정된 시간 후) 대기하기 때문입니다. 지연은 항목의 재생 기간에 따라 다릅니다.

### 일정 {#schedule-channel}

예약을 사용하면 채널이 표시되는 시기를 텍스트로 표시할 수 있습니다. 또한 채널을 표시할 시작 날짜(**부터**&#x200B;활성) 및 종료 날짜(**활성**&#x200B;까지)를 정의할 수 있습니다.

**명소 도구 설명 표시**

명소 도구 설명 표시 는 채널이 실행되는 동안 명소 도구 설명(&quot;*시작할 위치에 터치*&quot;)을 표시해야 하는지 여부를 정의합니다.

### 시간대 지정 {#dayparting}

일정은 **DayParting**&#x200B;과(와) 결합하면 하루 중 특정 시간에 여러 채널이 실행되는 글로벌 일정을 설정하고 모든 디스플레이에 대해 설정된 일정을 한 번에 재사용할 수 있습니다.

DayParting은 하루를 시간 슬롯으로 분할하고 원하는 시간에 재생할 콘텐츠를 지정하는 것을 말합니다. AEM Screens을 사용하면 요구 사항에 따라 일, 주 또는 월 단위로 채널을 DayParting 기준으로 예약할 수 있습니다.

다음 예제에서는 서로 다른 세 가지 시나리오에서 채널의 날짜 분할을 설명합니다.

#### 여러 개의 시간 슬롯으로 분할된 하루 동안 콘텐츠 재생 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

이 예는 Restaurant이 DayParting을 사용하여 아침, 점심 및 저녁 메뉴를 선보이는 방법을 보여줍니다.

여기서는 채널 콘텐츠가 지정된 시간에 따라 재생되도록 각 요일을 세 개의 서로 다른 시간 슬롯으로 나눕니다.

| **채널** | **역할** | **우선 순위** | **일정** |
|---|---|---|---|
| Menu_A | 아침 식사 |  | 6:00 후 및 11:00 전 |
| Menu_B | 점심 |  | 11:00 후 및 15:00 전 |
| Menu_C | 저녁식사 |  | 15:00 후 및 20:00 전 |

#### 특정 요일에 콘텐츠 재생 {#playing-content-on-a-particular-day-of-the-week}

이 예는 매일 주말 오후 8:00부터 오후 10:00까지 라이브 이벤트가 발생하고 오후 10:00부터 오전 1:00까지 디너 메뉴에 대한 스페셜을 사용할 수 있는 카지노에서 달성한 dayParting을 보여줍니다.

<table>
 <tbody>
  <tr>
   <td><strong>채널</strong></td>
   <td><strong>역할</strong></td>
   <td><strong>우선 순위</strong></td>
   <td><strong>일정</strong></td>
  </tr>
  <tr>
   <td>라이브 콘서트</td>
   <td>주말</td>
   <td> </td>
   <td>2017년 10월 21일 - 2017년 10월 22일 <br /> 20:00 이후 22:00</td>
  </tr>
  <tr>
   <td>스페셜스 디너</td>
   <td>주말</td>
   <td> </td>
   <td>2017년 10월 21일 - 2017년 10월 22일 <br /> 22시 이후 1시 이전</td>
  </tr>
 </tbody>
</table>

#### 특정 달/개월 동안 컨텐츠 재생 {#playing-content-for-a-particular-month-months}

이 예제는 6월부터 8월까지 여름 컬렉션 및 9월부터 10월 말까지 가을 컬렉션을 표시하는 스토어의 DayParting을 보여 줍니다.

여기에서는 한 달에 따라 DayParting을 만들어 채널 콘텐츠가 한 해의 지정된 달에 따라 재생되도록 합니다.

| **채널** | **역할** | **우선 순위** | **일정** |
|---|---|---|---|
| SummerCollection | Summer |  | 2017년 6월 1일 - 2017년 8월 31일 |
| FallCollection | 가을 |  | 2017년 9월 1일 - 2017년 10월 30일 |

>[!NOTE]
>
>또한 각 채널에 대해 ***우선 순위***&#x200B;를 정의할 수 있습니다. 예를 들어, 두 개의 채널이 같은 날 및 시간 또는 같은 달에 대해 설정된 경우 우선 순위가 높은 채널이 먼저 재생됩니다. 우선 순위의 최소값은 0으로 설정할 수 있습니다.

#### 우선 순위가 같은 채널의 콘텐츠 재생 {#playing-content-for-channels-with-same-priority}

이 예는 12월 한 달에 동일한 일정으로 겨울 컬렉션을 표시하는 스토어의 DayParting을 보여줍니다. 그러나 채널 B의 우선순위가 2로 설정되어 있으므로 해당 주 동안 채널 B가 채널 A가 아닌 콘텐츠를 재생합니다.

| **채널** | **역할** | **우선 순위** | **일정** |
|---|---|---|---|
| A | 겨울 | 1 | 2017년 12월 1일 - 2017년 12월 31일 |
| B | 크리스마스 | 2 | 2017년 12월 24일 - 2017년 12월 31일 |


>[!NOTE]
>
> DayParting에 대한 자세한 내용은 아래 섹션을 참조하십시오.
>
>* [Assets에서 반복 처리](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [채널에서 Assets에 대한 반복 처리](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
