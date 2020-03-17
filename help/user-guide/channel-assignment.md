---
title: 채널 지정
seo-title: 채널 지정
description: 채널 지정 및 방송 시간 분할에 대해 알려면 이 페이지를 따르십시오.
seo-description: 채널 지정 및 방송 시간 분할에 대해 알려면 이 페이지를 따르십시오.
uuid: fe429485-dcc9-4507-864c-b04393cedeee
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 212adcd1-835b-453d-9d3e-775366abf181
docset: aem65
translation-type: tm+mt
source-git-commit: f8d4b612d9c10d3f9f43ff4792ca48a1bf9407d0

---


# 채널 지정 {#channel-assignment}

이 섹션에서는 다음과 같은 주제를 다룹니다.

* **채널 지정**
* **채널 지정 대화 상자의 속성 이해**
* **방송 시간 분할**

디스플레이를 정의한 후에는 디스플레이에 채널을 지정해야 합니다.

이 페이지에서는 디스플레이에 채널을 할당하는 과정을 보여줍니다.

**전제 조건**:

* [스크린 구성 및 배치](configuring-screens-introduction.md)
* [스크린 프로젝트 만들기 및 관리](creating-a-screens-project.md)
* [채널 만들기 및 관리](managing-channels.md)
* [위치 만들기 및 관리](managing-locations.md)
* [디스플레이 만들기 및 관리](managing-displays.md)

## 채널 지정 {#assign-a-channel}

아래 절차에 따라 디스플레이에 채널을 지정하십시오.

1. 필요한 디스플레이(예: DemoProject **—> 위치** **—> SanJose** —> **StoreDisplay** ) ****&#x200B;로 이동합니다.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. 작업 표시줄에서 **채널 지정 **을 탭/클릭합니다.

   또는,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   **채널 지정** 대화 상자에서 다음 속성을 구성할 수 있습니다.

   **채널 역할**:

   채널 역할은 디스플레이 컨텍스트를 정의합니다. 역할은 다양한 동작에 의해 타깃팅되며 역할을 수행하는 실제 채널과 독립적입니다.

   **참조 채널**:

   참조 채널을 사용하면 채널 이름 또는 채널 경로별로 원하는 채널에 대한 참조를 제공할 수 있습니다.

   * **경로 기준**: 채널의 절대 경로를 사용하여 명시적 참조를 제공합니다.
   * **이름별**:컨텍스트별로 실제 채널로 확인할 채널의 이름을 입력합니다. 이 기능을 사용하면 위치별 컨텐츠를 동적으로 확인할 수 있도록 채널의 로컬 버전을 만들 수 있습니다. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.
   **우선 순위:**

   우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있고 A의 우선 순위는 1이고 B의 우선 순위는 2라면, 채널 B의 우선 순위가 A보다 높으므로 채널 B가 표시됩니다.

   채널의 우선 순위는 위에 언급된 대로 **채널 지정** 대화 상자에서 숫자(최소값은 1)로 설정됩니다. 또한, 지정된 채널은 내림차순의 우선 순위를 기준으로 정렬됩니다.

   **지원되는 이벤트**:

   * **초기 로드**: 플레이어가 시작될 때 채널을 로드합니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
   * **유휴 화면**: 화면이 유휴 상태일 때 로드됩니다. 일정과 결합하여 여러 채널에 지정할 수 있습니다.
   * **타이머**: 일정이 제공되면 설정해야 합니다.
   * **사용자 상호 작용**: 유휴 채널에서 화면(터치)에 사용자 상호 작용이 있으면 플레이어가 지정된 채널로 전화되고 화면을 터치하면 로드됩니다.
   **예약**:

   일정을 사용하면 채널이 표시될 때 텍스트로 된 설명을 제공할 수 있습니다. It also let&#39;s you define a start date (**active from**) and an end date (**active until**) for the channel to be shown. 일정 표현식 구문은 later.js의 텍스트 및 cron 구문을 기반으로 합니다.

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text)
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron)
   **명소 도구 설명 표시**:

   [명소 도구 설명 표시]는 채널이 실행될 때 명소 도구 설명(&quot;*시작하려면 아무 데나 터치하세요*&quot;)을 표시해야 할지 여부를 정의합니다.

1. **저장**&#x200B;을 클릭하여 생성된 채널을 디스플레이에 지정합니다.

### 방송 시간 분할 {#dayparting}

Schedules when combined with **Dayparting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

방송 시간 분할은 하루를 시간 슬롯으로 분할하고 원하는 시간에 재생되는 컨텐츠를 지정하는 것을 말합니다. AEM Screens에서는 요구 사항에 따라 하루, 1주일 또는 1개월 내의 방송 시간 분할 관점에서 채널 일정을 예약할 수 있습니다.

다음 예에서는 채널의 방송 시간 분할을 세 개의 서로 다른 시나리오로 설명합니다.

#### 여러 개의 시간 슬롯으로 분할된 하루의 컨텐츠 재생 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

이 예에서는 음식점이 어떻게 방송 시간 분할을 사용하여 아침, 점심, 저녁 식사 메뉴를 선보이지를 보여줍니다.

여기서는 매일 세 개의 다른 시간 슬롯으로 나누어 채널 컨텐츠가 지정된 시간에 따라 재생되도록 합니다.

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
   <td>2017년 10월 21일 - 2017년 10월 22 <br /> 일 20:00 전 22:00</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>주말</td>
   <td> </td>
   <td>2017년 10월 21일 - 2017년 10월 22일 <br /> 후 1:00 이전</td>
  </tr>
 </tbody>
</table>

#### 특정 달 동안의 컨텐츠 재생 {#playing-content-for-a-particular-month-months}

이 예에서는 6월부터 8월까지의 달 동안 여름 컬렉션을 표시하고 9월부터 10월 말까지 가을 컬렉션을 표시하는 점포의 방송 시간 분할을 보여줍니다.

여기서는 채널 컨텐츠가 지정된 달이 되면 재생되도록 달에 대한 방송 시간 분할을 작성하게 됩니다.

| **채널** | **역할** | **우선 순위** | **예약** |
|---|---|---|---|
| SummerCollection | 여름 |  | 2017년 6월 01일 - 2017년 8월 31일 |
| FallCollection | 가을 |  | 2017년 9월 1일 - 2017년 10월 30일 |

>[!NOTE]
>
>추가로, 각 채널에 대해 ***우선 순위***&#x200B;를 정의할 수 있습니다. 예를 들어, 동일한 날짜 및 시간 또는 동일한 달에 대해 두 개의 채널이 설정되면 우선 순위가 높은 채널이 먼저 재생됩니다. 우선 순위의 최소값은 0으로 설정할 수 있습니다.

#### 우선 순위가 같은 채널의 컨텐츠 재생 {#playing-content-for-channels-with-same-priority}

이 예에서는 12월에 일정이 동일한 겨울 컬렉션을 표시하는 점포에 대한 방송 시간 분할을 보여줍니다. 그러나 해당 주 동안 채널 B의 우선 순위가 2로 설정되었으므로 채널 A가 아니라 채널 B가 컨텐츠를 재생합니다.

| **채널** | **역할** | **우선 순위** | **예약** |
|---|---|---|---|
| A | 겨울 | 1 | 2017년 12월 1일 - 2017년 12월 31일 |
| B | 크리스마스 | 2 | 2017년 12월 24일 - 2017년 12월 31일 |

