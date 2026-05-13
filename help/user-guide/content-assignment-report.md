---
title: 컨텐츠 할당 보고서
description: AEM Screens과 관련된 컨텐츠 할당 보고서의 다운로드 및 사용에 대해 알아봅니다.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
TQID: https://experienceleague.adobe.com/Pwq3ebRrbCufXFMk7R-FJj90xq4b7gLOcLvslch2L5o
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 358
ht-degree: 3%

---

# 컨텐츠 할당 보고서 {#content-assignment-report}

콘텐츠 할당 보고서 기능을 사용하면 AEM Screens 관리자 또는 작성자가 *콘텐츠 할당 보고서*&#x200B;를 스프레드시트 형식으로 내보낼 수 있습니다.

## 컨텐츠 할당 보고서 사용 {#using-content-assignment-report}

컨텐츠 할당 보고서를 사용하면 AEM Screens 작성자 또는 관리자가 AEM Screens 프로젝트에서 만든 모든 채널의 이미지, 비디오와 같은 모든 자산이 포함된 보고서를 다운로드할 수 있습니다. 또한, 모든 지정된 디스플레이에 할당된 전체 채널 및 이제부터 지정된 디스플레이에 할당된 모든 장치의 정보를 포함합니다.

콘텐츠 할당 보고서 를 사용하면 선택한 AEM Screens 프로젝트의 모든 채널, Assets, 디스플레이 및 장치를 미리 볼 수 있을 뿐만 아니라 프로젝트의 높은 수준 구조를 제공합니다.


### 사전 요구 사항 {#pre-reqs}

콘텐츠 할당 보고서를 다운로드하기 전에 채널, 위치 및 장치가 있는 AEM Screens 프로젝트를 설정했는지 확인하십시오.
자세한 내용은 다음 리소스를 참조하십시오.

1. [프로젝트 생성 및 관리](/help/user-guide/creating-a-screens-project.md)
1. [채널 만들기 및 관리](/help/user-guide/managing-channels.md)
1. [위치 생성 및 관리](/help/user-guide/managing-locations.md)
1. [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)
1. [장치 만들기](/help/user-guide/managing-devices.md)
1. [채널 할당](/help/user-guide/channel-assignment-latest-fp.md)


## 콘텐츠 할당 보고서 다운로드 {#downloading-content-assignment-report-fp}

AEM Screens 프로젝트를 설정하고 이전 단계에 표시된 대로 각 위치에 디스플레이를 할당하면 콘텐츠 할당 보고서를 다운로드합니다.

>[!NOTE]
>콘텐츠 할당 보고서 기능은 프로젝트 수준에서만 액세스할 수 있습니다.

콘텐츠 할당 보고서를 다운로드하려면 아래 지침을 따르십시오.

1. AEM Screens 프로젝트로 이동하여 프로젝트 **DemoScreens**&#x200B;을(를) 클릭합니다.

1. 작업 표시줄에서 **콘텐츠 할당 보고서**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/can-download.png)

1. 다운로드한 스프레드시트는 **위치** 및 **콘텐츠**&#x200B;와 같은 두 개의 탭으로 구성됩니다. 위치 탭에는 AEM Screens 프로젝트와 관련된 네 개의 엔터티를 조사하는 데 사용할 수 있는 **위치**, **표시**, **채널** 및 **장치**&#x200B;와 같은 네 개의 열이 표시됩니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >스프레드시트에 표시되는 데이터는 알파벳순으로 읽기 쉬운 형식으로 정렬됩니다.

1. **채널** 열에서 채널을 선택하면 **콘텐츠** 탭이 열립니다. 결과적으로 해당 채널로 직접 이동하여 해당 특정 채널과 연관된 에셋(이미지 및 비디오)에 대한 정보를 제공합니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
