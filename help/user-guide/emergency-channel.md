---
title: 비상 채널
seo-title: 비상 채널
description: 이 사용 사례 예제를 통해 컨텐츠 작성자가 전제 조건이 있는 경우 시퀀스 채널에서 전환할 수 있는 응급 채널을 만들고 관리하는 방법을 살펴보십시오.
seo-description: 이 사용 사례 예제를 통해 컨텐츠 작성자가 전제 조건이 있는 경우 시퀀스 채널에서 전환할 수 있는 응급 채널을 만들고 관리하는 방법을 살펴보십시오.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 16%

---


# 비상 채널 {#emergency-channel}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 컨텐츠 작성자가 전제 조건이 있는 경우 시퀀스 채널에서 전환할 수 있는 응급 채널 생성 및 관리를 강조하는 사용 사례 예제를 설명합니다.

### 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주 배우 {#primary-actors}

컨텐츠 작성자

## 기본 흐름:프로젝트 {#basic-flow-setting-up-the-project} 설정

아래 절차에 따라 응급 채널을 설정하십시오.

1. 아래와 같이 **EmergencyChannel**&#x200B;이라는 AEM Screens 프로젝트를 만듭니다.

   >[!NOTE]
   >AEM Screens에서 프로젝트를 만들고 관리하는 방법에 대한 자세한 내용은 프로젝트 만들기를 참조하십시오.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **시퀀스 채널 만들기**

   1. **채널** 폴더를 선택하고 **만들기**&#x200B;를 클릭하여 마법사를 열고 채널을 만듭니다.

   1. 마법사에서 **시퀀스 채널**&#x200B;을 선택하고 **MainAdChannel**&#x200B;이라는 이름의 채널을 만듭니다.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **시퀀스 채널에 컨텐츠 추가**

   1. 채널(**MainAdChannel**)을 선택합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다. 몇 개의 자산을 채널에 드래그하여 놓습니다.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **응급 채널 만들기**

   1. **채널** 폴더를 선택합니다.
   1. 채널을 만들 마법사를 열려면 **만들기**&#x200B;를 클릭합니다.
   1. 마법사에서 **시퀀스 채널**&#x200B;을 선택하고 **EmergencyChannel**&#x200B;이라는 이름의 채널을 만듭니다.

   >[!NOTE]
   >
   >일반적으로 비상 채널은 기존 프로덕션 프로젝트에 추가됩니다.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **응급 채널에 컨텐츠 추가**

   1. 채널(**비상 채널)**&#x200B;을 선택합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다. 비상시 실행할 자산을 채널에 드래그하여 놓습니다.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **위치 생성**

   1. **위치** 폴더로 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭하고 마법사에서 **스토어**&#x200B;라는 이름의 위치를 만듭니다.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **위치에 디스플레이 만들기**

   위치(**스토어**)로 이동하고 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사의 지시에 따라 **StoreFront** 및 **StoreRear**&#x200B;라는 이름의 두 **Display**&#x200B;를 만듭니다.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **예약 생성**

   1. **일정** 폴더로 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사를 따라 **StoreSchedule**&#x200B;이라는 이름의 일정을 만듭니다.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 일정에 디스플레이 할당 및 우선 순위 설정

   1. 일정 **(StoreSchedule)**&#x200B;을 선택하고 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.

   1. **지정된 채널** 패널에서 **+ 채널 지정**&#x200B;을 클릭합니다.

   1. **채널 지정** 대화 상자에서 다음을 수행합니다.

      1. **MainAdChannel** 경로를 선택합니다.
      1. **우선 순위**&#x200B;를 2로 설정합니다.
      1. 지원되는 이벤트를 **초기 로드** 및 **유휴 화면**&#x200B;으로 설정합니다.
      1. **저장**&#x200B;을 클릭합니다

      마찬가지로, 동일한 단계를 다시 수행하여 **EmergencyChannel**&#x200B;을 할당하고 해당 **Priority**&#x200B;를 설정해야 합니다.
   >[!NOTE]
   >
   >우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. **지정된 채널** 패널에서 **+ 채널 지정**&#x200B;을 클릭합니다.

1. **채널 지정** 대화 상자에서 다음을 수행합니다.

   1. **EmergencyChannel** 경로를 선택합니다.
   1. **Priority**&#x200B;을(를) 1로 설정합니다.

   1. 지원되는 이벤트를 **초기 로드**, **유휴 화면** 및 **사용자 상호 작용**&#x200B;으로 설정합니다.

   1. **저장**&#x200B;을 클릭합니다

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   **StoreSchedule** 대시보드에서 지정된 채널을 볼 수 있습니다.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **각 디스플레이에 스케줄 지정**

   1. **EmergencyChannel** —> **위치** —> **스토어** —>**StoreFront**&#x200B;와 같은 각 디스플레이로 이동합니다.

   1. 동작에서 **대시보드**&#x200B;를 클릭하여 표시 대시보드를 엽니다.
   1. **...을 클릭합니다.**&#x200B;지정된 채널 및 일정&#x200B;**패널에서**&#x200B;을 클릭하고 **+일정 지정**&#x200B;을 클릭합니다.

   1. 일정 경로를 선택합니다(예: **EmergencyChannel** —> **Schedues** —>**StoreSchedule**).

   1. **저장**&#x200B;을 클릭합니다.

   **StoreSchedule** 대시보드에서 디스플레이에 지정된 일정을 볼 수 있습니다.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **장치 등록**

   장치 등록 프로세스를 완료하고 등록하면 AEM Screens 플레이어에서 다음 출력을 볼 수 있습니다.

   ![new30](assets/new30.gif)

## 응급 채널 {#switching-to-emergency-channel}으로 전환

비상시에는 다음 단계를 수행합니다.

1. **EmergencyChannel** —> **Schedules** —> **StoreSchedule**&#x200B;로 이동하고 작업 표시줄에서 **Dashboard**&#x200B;을 선택합니다.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. **StoreSchedule** 대시보드에서 **EmergencyChannel**&#x200B;을 선택하고 **할당 편집**&#x200B;을 클릭합니다.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. **채널 지정** 대화 상자에서 **EmergencyChannel**&#x200B;의 **Priority**&#x200B;을 **3**&#x200B;로 업데이트하고 **저장**&#x200B;을 클릭합니다.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 채널의 우선 순위가 업데이트되는 즉시 모든 AEM Screens 플레이어는 아래와 같이 **EmergencyChannel** 콘텐츠를 표시합니다.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 결론 {#conclusion}

**EmergencyChannel**&#x200B;은 컨텐츠 작성자가 우선순위 값을 1로 재설정할 때까지 해당 컨텐츠를 계속 표시합니다.

컨텐츠 작성자가 비상사태가 해결되었다는 지침을 받으면 일반 재생이 다시 시작되게 하는 **MainAdChannel**&#x200B;의 우선 순위를 업데이트해야 합니다.
