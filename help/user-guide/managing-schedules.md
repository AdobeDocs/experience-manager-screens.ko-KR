---
title: 스케줄 생성 및 관리
description: 컨텐츠를 표시할 각 표시에 대해 개별적으로 할당을 반복하지 않아도 되도록 채널을 재사용 가능한 그룹으로 구성할 수 있는 일정에 대해 알아봅니다.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# 스케줄 생성 및 관리 {#creating-and-managing-schedules}

**일정** AEM Screens에서는 컨텐츠를 표시할 각 표시에 대해 개별적으로 할당을 반복하지 않아도 되도록 채널을 재사용 가능한 그룹으로 구성할 수 있습니다.

과 결합된 경우 일정 ***시간대 지정***&#x200B;을(를) 사용하면 하루 중 특정 시간에 여러 채널이 실행되는 글로벌 일정을 설정하고 모든 디스플레이에 대해 설정된 일정을 한 번에 다시 사용할 수 있습니다.

>[!NOTE]
>
>이 AEM Screens 기능은 AEM 6.3 Sites 기능 팩 1을 설치한 경우에만 사용할 수 있습니다. 이 기능 팩에 액세스하려면 Adobe 지원에 문의하고 액세스를 요청해야 합니다. 필요한 권한이 있으면 패키지 공유에서 다운로드할 수 있습니다.

## 일정 만들기 {#creating-a-schedule}

사용 사례에 대한 모든 활동을 관리할 수 있는 Screens 프로젝트에 대한 일정을 만들 수 있습니다.

채널의 일정을 만들려면 아래 단계를 수행하십시오.

1. Adobe Experience Manager 링크(왼쪽 상단)를 선택한 다음 화면 을 선택합니다. 또는 다음 위치로 직접 이동할 수 있습니다. `http://localhost:4502/screens.html/content/screens`.
1. Screens 프로젝트로 이동한 다음 **일정**.
1. 클릭 **만들기** 작업 표시줄에서
1. 선택 **예약** 다음에서 **만들기** 마법사 및 클릭 **다음**.

1. 다음을 입력합니다. **이름** 및 **제목** 및 클릭 **만들기**.

프로젝트에서 지정된 이름과 제목의 예약 폴더를 볼 수 있습니다.


## 대시보드 보기 {#viewing-dashboard}

프로젝트에서 일정 폴더를 생성한 후 일정 대시보드에서 세부 정보를 볼 수 있습니다.

예약 대시보드를 보려면 아래 단계를 따르십시오. 다음 예제는 의 대시보드를 보여줍니다. `We.Retail` 프로젝트:

1. 다음 위치로 이동 **일정** Screens 폴더(예: `We.Retail`) 프로젝트.

   ![chlimage_1](assets/chlimage_1.png)

1. 선택 **대시보드** 작업 표시줄에서

   다음과 같은 세 개의 서로 다른 패널을 볼 수 있습니다 **일정 정보**, **할당된 채널**, 및 **할당된 디스플레이**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **일정 정보 패널** [일정 정보] 패널의 오른쪽 상단 모서리에서 [속성]을 클릭하여 일정 속성을 보거나 변경합니다.

   **할당된 채널 패널** [할당된 채널] 패널의 오른쪽 상단 모서리에서 +채널 할당 을 클릭하여 [채널 할당] 대화 상자를 엽니다.

   **할당된 디스플레이 패널** 지정된 디스플레이(ASSIGNED DISPLAYS) 패널에서 디스플레이를 선택하여 디스플레이 대시보드를 엽니다.
