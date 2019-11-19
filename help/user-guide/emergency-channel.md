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
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 비상 채널 {#emergency-channel}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 전제 조건이 있을 경우 컨텐츠 작성자가 시퀀스 채널에서 전환할 수 있는 응급 채널 만들기 및 관리를 강조하는 사용 사례 예제를 설명합니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주요 배우 {#primary-actors}

컨텐츠 작성자

## 기본 흐름:프로젝트 설정 {#basic-flow-setting-up-the-project}

아래 절차에 따라 긴급 채널을 설정하십시오.

1. 아래와 같이 EmergencyChannel **으로**&#x200B;명명된 AEM Screens 프로젝트를 만듭니다.

   >[!NOTE]
   >
   >AEM Screens에서 프로젝트를 만들고 관리하는 방법에 대한 자세한 내용은 프로젝트 만들기를 참조하십시오.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **시퀀스 채널 만들기**

   1. 채널 폴더를 **선택하고** 만들기를 클릭하여 **마법사를** 열어 채널을 만듭니다.

   1. 마법사에서 **시퀀스 채널 **을 선택하고 MainAdChannel이라는 이름의 채널을 **만듭니다**.
   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **시퀀스 채널에 컨텐츠 추가**

   1. 채널(MainAdChannel **)을**&#x200B;선택합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다. 몇 개의 자산을 채널에 드래그하여 놓습니다.
   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **비상 채널 만들기**

   1. 채널 **폴더를** 선택합니다.
   1. 만들기를 **클릭하여** 마법사를 열고 채널을 만듭니다.
   1. 마법사에서 **시퀀스 채널 **을 선택하고 EmergencyChannel이라는 이름의 채널을 **만듭니다**.
   >[!NOTE]
   >
   >일반적으로 비상 채널은 기존 프로덕션 프로젝트에 추가됩니다.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **응급 채널에 컨텐츠 추가**

   1. 채널(**긴급 채널)을 선택합니다**.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다. 비상 시 실행할 자산을 채널에 드래그하여 놓습니다.
   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **위치 생성**

   1. 위치 **폴더로 이동합니다** .
   1. 작업 **표시줄에서** 만들기를 클릭하고 마법사에서 스토어 **라는** 위치를 만듭니다.
   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **위치에 디스플레이 만들기**

   위치(스토어)**로**&#x200B;이동하고 작업 **표시줄에서** 만들기를 클릭합니다. 마법사의 지시에 따라 StoreFront **와 StoreBack** 이라는 **두** 개의 **디스플레이를**&#x200B;만듭니다.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **예약 생성**

   1. 예약 **폴더로** 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사에 따라 StoreSchedule이라는 제목을 붙인 일정을 **만듭니다**.
   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 일정에 디스플레이를 지정하고 우선순위를 설정합니다.

   1. schedule**(StoreSchedule)**를 선택하고 작업 **표시줄에서** Dashboard를 클릭합니다.

   1. ** **지정된 채널** **패널에서+ 채널 지정을 클릭합니다.

   1. 채널 지정 **대화** 상자에서 다음을 수행합니다.

      1. MainAdChannel 경로 **선택**
      1. 우선 순위를 **2로** 설정
      1. Set the Supported Events as **Initial Load** and **Idle Screen**.
      1. **저장**&#x200B;을 클릭합니다
      마찬가지로, EmergencyChannel을 할당하고 Priority를 **설정하려면 동일한** 단계를 다시 수행해야 **합니다**.
   >[!NOTE]
   >
   >우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. ** **지정된 채널** **패널에서+ 채널 지정을 클릭합니다.

1. 채널 지정 **대화** 상자에서 다음을 수행합니다.

   1. EmergencyChannel 경로 **선택**
   1. 우선 순위를 **1로** 설정

   1. 지원되는 이벤트를 초기 로드, **유휴**&#x200B;화면 **및**&#x200B;사용자 인터랙션으로 **설정**

   1. **저장**&#x200B;을 클릭합니다
   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   StoreSchedule 대시보드에서 지정된 채널을 볼 **수** 있습니다.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **각 디스플레이에 스케줄 지정**

   1. EmergencyChannel —&gt; **위치** —&gt; ** **Store **—&gt;StoreFront와 같은 각** 디스플레이로&#x200B;**이동합니다**.

   1. Click **Dashboard** from the action to open the display dashboard.
   1. **클릭**&#x200B;중...지정된 **채널 및 예약** 패널에서 을 클릭하고 **+예약 할당을 클릭합니다**.

   1. 예약 경로를 선택합니다(예: EmergencyChannel —&gt; **Schedules** —&gt; **Store** Schedule **)**.

   1. **저장**&#x200B;을 클릭합니다.
   StoreSchedule 대시보드에서 디스플레이에 지정된 일정을 볼 **수** 있습니다.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **장치 등록**

   장치 등록 프로세스를 완료하고 등록하면 AEM Screens 플레이어에서 다음 출력을 볼 수 있습니다.

   ![new30](assets/new30.gif)

## 응급 채널로 전환 {#switching-to-emergency-channel}

긴급한 경우 다음 단계를 수행합니다.

1. EmergencyChannel **—&gt; Schedules** **—&gt; StoreSchedule** 로 **이동하고** Dashboard작업 표시줄에서 **** Dashboard를 선택합니다.

   ![screen_shot_2019-02-25at10112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. StoreSchedule **대시보드에서 EmergencyChannel** 을 **선택하고** Edit Assignment **를 클릭합니다**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 긴급 채널의 **우선 순위를** 채널 **할당** 대화 상자에서 **3**********&#x200B;으로 업데이트하고 SaveSaveClick을 클릭합니다.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 채널의 우선 순위가 업데이트되는 즉시 모든 AEM Screens 플레이어에 **다음과 같이 EmergencyChannel** 콘텐츠가 표시됩니다.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 결론 {#conclusion}

EmergencyChannel **은** 컨텐츠 작성자가 Priority 값을 1로 재설정할 때까지 컨텐츠를 계속 표시합니다.

컨텐츠 작성자가 비상사태가 해결되었다는 지침을 받으면 MainAdChannel의 우선 순위를 업데이트하여 **정상적인** 재생이 다시 시작됩니다.
