---
title: 긴급 채널
description: 전제 조건이 있는 경우 콘텐츠 작성자가 시퀀스 채널에서 전환할 수 있는 긴급 채널을 만들고 관리하는 방법에 대해 알아봅니다.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# 긴급 채널 {#emergency-channel}

## 사용 사례 설명 {#use-case-description}

이 섹션에서는 사용 사례 예제를 설명합니다. 전제 조건이 있는 경우 콘텐츠 작성자가 시퀀스 채널에서 전환할 수 있는 긴급 채널을 만들고 관리하는 것을 강조합니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해했는지 확인하십시오.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[일정 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 기본 작업자 {#primary-actors}

콘텐츠 작성자

## 기본 플로우: 프로젝트 설정 {#basic-flow-setting-up-the-project}

긴급 채널을 설정하려면 아래 단계를 따르십시오.

1. 아래와 같이 이름이 **EmergencyChannel**&#x200B;인 AEM Screens 프로젝트를 만듭니다.

   >[!NOTE]
   >AEM Screens에서 프로젝트를 만들고 관리하는 방법에 대한 자세한 내용은 프로젝트 만들기 를 참조하십시오.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **시퀀스 채널 만들기**

   1. **채널** 폴더를 클릭하고 **만들기**&#x200B;를 클릭합니다.

   1. 마법사에서 **시퀀스 채널**&#x200B;을(를) 클릭하고 제목이 **MainAdChannel**&#x200B;인 채널을 만듭니다.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **시퀀스 채널에 콘텐츠 추가**

   1. 채널(**MainAdChannel**)을 클릭합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.
   1. 몇 개의 에셋을 채널에 드래그 앤 드롭합니다.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **긴급 채널 만들기**

   1. **채널** 폴더를 클릭합니다.
   1. **만들기**&#x200B;를 클릭합니다.
   1. 마법사에서 **시퀀스 채널**&#x200B;을(를) 클릭하고 **EmergencyChannel**(으)로 제목이 지정된 채널을 만듭니다.

   >[!NOTE]
   >
   >일반적으로 긴급 채널은 기존 프로덕션 프로젝트에 추가됩니다.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **긴급 채널에 콘텐츠 추가**

   1. 채널(**긴급 채널)**&#x200B;을 클릭합니다.
   1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.
   1. 비상 시 실행할 에셋을 채널에 드래그 앤 드롭합니다.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **위치 만들기**

   1. **위치** 폴더로 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭하고 마법사에서 **스토어**&#x200B;라는 위치를 만듭니다.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **위치에 디스플레이 만들기**

   위치(**스토어**)로 이동한 다음 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다. 마법사에 따라 **StoreFront** 및 **StoreRear**(으)로 제목이 지정된 두 개의 **디스플레이**&#x200B;을(를) 만듭니다.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **일정 만들기**

   1. **일정** 폴더로 이동합니다.
   1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
   1. 마법사에 따라 **StoreSchedule**(으)로 제목이 지정된 일정을 만듭니다.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 일정에 디스플레이 할당 및 우선 순위 설정

   1. 일정 **(StoreSchedule)**&#x200B;을(를) 클릭하고 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.

   1. **할당된 채널** 패널에서 **+ 채널 할당**&#x200B;을 클릭합니다.

   1. **채널 할당** 대화 상자에서 다음 작업을 수행합니다.

      1. **MainAdChannel** 경로를 클릭합니다.
      1. **우선 순위**&#x200B;을(를) 2로 설정
      1. 지원되는 이벤트를 **초기 로드** 및 **유휴 화면**(으)로 설정합니다.
      1. **저장** 클릭

      마찬가지로 같은 단계를 다시 수행하여 **EmergencyChannel**&#x200B;을 할당하고 **우선 순위**&#x200B;를 설정하십시오.

   >[!NOTE]
   >
   >여러 할당이 재생 기준과 일치하는 경우 우선 순위를 사용하여 할당을 정렬합니다. 값이 가장 높은 것이 항상 낮은 값보다 우선합니다.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. **할당된 채널** 패널에서 **+ 채널 할당**&#x200B;을 클릭합니다.

1. **채널 할당** 대화 상자에서 다음 작업을 수행합니다.

   1. **EmergencyChannel** 경로를 클릭합니다.
   1. **우선 순위**&#x200B;을(를) 1로 설정

   1. 지원되는 이벤트를 **초기 로드**, **유휴 화면** 및 **사용자 상호 작용**(으)로 설정

   1. **저장** 클릭

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   **StoreSchedule** 대시보드에서 할당된 채널을 볼 수 있습니다.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **각 디스플레이에 일정 할당**

   1. **EmergencyChannel** > **위치** > **스토어** >**스토어**&#x200B;와 같이 각 디스플레이로 이동합니다.

   1. 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.
   1. **할당된 채널 및 일정** 패널에서 **..**&#x200B;을(를) 클릭하고 **+일정 할당**&#x200B;을(를) 추가로 클릭합니다.

   1. 예약에 대한 경로를 클릭합니다(예: **EmergencyChannel** > **Schedules** >**StoreSchedule**).

   1. **저장**&#x200B;을 클릭합니다.

   **StoreSchedule** 대시보드에서 디스플레이에 할당된 일정을 볼 수 있습니다.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **장치 등록**

   장치 등록 프로세스를 완료합니다. 등록하면 AEM Screens 플레이어에서 다음 출력을 볼 수 있습니다.

   ![new30](assets/new30.gif)

## 긴급 채널로 전환 {#switching-to-emergency-channel}

긴급한 상황이 발생하면 다음 단계를 수행하십시오.

1. **EmergencyChannel** > **일정** > **StoreSchedule**&#x200B;로 이동하고 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. **StoreSchedule** 대시보드에서 **EmergencyChannel**&#x200B;을 클릭하고 **할당 편집**&#x200B;을 클릭합니다.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. **채널 할당** 대화 상자에서 **EmergencyChannel**&#x200B;의 **우선 순위**&#x200B;를 **3**(으)로 업데이트하고 **저장**&#x200B;을(를) 클릭합니다.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 채널의 우선 순위가 업데이트되면 모든 AEM Screens 플레이어에 **EmergencyChannel** 콘텐츠가 표시됩니다.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 결론 {#conclusion}

**EmergencyChannel**&#x200B;은(는) 콘텐츠 작성자가 우선 순위 값을 1로 재설정할 때까지 해당 콘텐츠를 계속 표시합니다.

콘텐츠 작성자는 긴급 상황이 해결되었다는 지침을 받으면 **MainAdChannel**&#x200B;의 우선 순위를 업데이트해야 합니다. 이렇게 하면 일반 재생이 다시 시작됩니다.
