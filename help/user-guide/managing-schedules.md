---
title: 일정 생성 및 관리
seo-title: 예약 관리
description: 컨텐츠를 표시할 각 디스플레이에 대해 개별적으로 지정을 반복하지 않아도 되도록 채널을 재사용 가능 그룹으로 구성할 수 있도록 해주는 예약에 대해 알려면 이 페이지를 따르십시오.
seo-description: 컨텐츠를 표시할 각 디스플레이에 대해 개별적으로 지정을 반복하지 않아도 되도록 채널을 재사용 가능 그룹으로 구성할 수 있도록 해주는 예약에 대해 알려면 이 페이지를 따르십시오.
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
feature: 스크린 작성
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 49%

---

# 일정 생성 및 관리 {#creating-and-managing-schedules}

**AEM Screens의 예약** 을 사용하면 컨텐츠를 표시할 각 디스플레이에 대해 개별적으로 지정을 반복할 필요가 없도록 채널을 재사용 가능 그룹으로 구성할 수 있습니다.

***DayParting***&#x200B;과 결합할 때 일정을 사용하면 하루 중 특정 시간에 실행 중인 여러 채널을 사용하여 글로벌 일정을 설정하고, 이 설정을 모든 디스플레이에 한 번에 다시 사용할 수 있습니다.

>[!NOTE]
>
>이 AEM Screens 기능은 AEM 6.3 Sites Feature Pack 1을 설치한 경우에만 사용할 수 있습니다. 이 Feature Pack에 액세스하려면 Adobe 지원 센터에 연락하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.

## 예약 생성 {#creating-a-schedule}

사용 사례의 모든 활동을 관리할 스크린 프로젝트를 위한 예약을 생성할 수 있습니다.

아래 절차에 따라 채널에 사용할 예약을 생성하십시오.

1. Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음 스크린을 선택합니다. 또는 다음 위치로 바로 이동할 수 있습니다. `http://localhost:4502/screens.html/content/screens`
1. 스크린 프로젝트로 이동하고 **예약**&#x200B;을 클릭합니다.
1. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.
1. **만들기** 마법사에서 **예약**&#x200B;을 선택하고 **다음**&#x200B;을 클릭합니다.

1. **이름**&#x200B;과 **제목**&#x200B;을 입력하고 **만들기**&#x200B;를 클릭합니다.

프로젝트에 지정된 이름과 제목을 사용하는 예약 폴더가 표시됩니다.


## 대시보드 보기 {#viewing-dashboard}

프로젝트에서 예약 폴더를 만들면 예약 대시보드에서 세부 사항을 볼 수 있습니다.

아래 절차에 따라 예약 대시보드를 확인하십시오. 다음 예에서는 We.Retail 프로젝트의 대시보드를 보여줍니다.

1. 스크린 프로젝트(예: We.Retail)의 **예약** 폴더로 이동합니다.

   ![chlimage_1](assets/chlimage_1.png)

1. 작업 표시줄에서 **대시보드**&#x200B;를 클릭하여 예약의 대시보드를 엽니다.

   **예약 정보**, **지정된 채널** 및 **지정된 디스플레이**&#x200B;와 같은 세 개의 서로 다른 패널이 표시됩니다.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **예약 정보** 패널일정 정보 패널의 오른쪽 위 모서리에서 속성을 클릭하여 예약의 속성을 보거나 변경합니다.

   **지정된 채널** 패널지정된 채널 패널의 오른쪽 위 모서리에서 +채널 지정 을 클릭하여 채널 지정 대화 상자를 엽니다.

   **지정된 디스플레이** 패널지정된 디스플레이 패널에서 디스플레이를 선택하여 디스플레이 대시보드를 엽니다.
