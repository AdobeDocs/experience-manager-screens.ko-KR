---
title: 채널 지정 - 최신 FP
seo-title: 채널 지정 - 최신 FP
description: 채널 지정 및 한시적 분할에 대해 알려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 28%

---


# 채널 지정 {#channel-assignment}

>[!IMPORTANT]
>이 섹션에서는 AEM 6.5.5 스크린 기능 팩 이상의 채널 지정 및 일정 관리를 집중적으로 설명합니다.

디스플레이를 설정한 후에는 컨텐츠를 보려면 디스플레이에 채널을 지정해야 합니다.

이 페이지에서는 디스플레이에 채널을 지정하는 것을 보여줍니다.

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

   대시보드 **를 탭/클릭하고** 지정된 채널 및 일정 **패널에서****채널** 지정을클릭합니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. [ **설정** ] 옵션에서 경로 또는 이름별로 채널을 선택하고 채널 역할, 우선 순위, 지원되는 이벤트 및 중단 방법을 입력할 수 있습니다. 또한 이 대화 상자에서 명소 도구 설명 옵션을 활성화할 수 있습니다.

   ![이미지](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >채널 속성에 대한 자세한 내용은 [채널 속성](#channel-properties) 섹션을 참조하십시오.

1. 예약 **옵션** 에서 **참조 시간대**, **활성화 창** 및 되풀이 **일정**&#x200B;을선택합니다.

1. 환경 **설정을** 구성했으면 저장을 클릭합니다.

### Chrome Player에서 콘텐트 보기 {#viewing-content-output}

### 채널 할당의 채널 속성 이해 {#channel-properties}

### 참조 채널 {#ref-channel}

참조 채널을 사용하면 채널 이름 또는 채널 경로별로 원하는 채널에 대한 참조를 제공할 수 있습니다.

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