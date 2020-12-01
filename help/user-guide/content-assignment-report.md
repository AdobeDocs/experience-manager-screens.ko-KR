---
title: 컨텐츠 할당 보고서
description: 이 페이지에서는 컨텐츠 할당 보고서의 다운로드 및 사용에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---


# 컨텐츠 할당 보고서 {#content-assignment-report}

컨텐츠 할당 보고서 기능을 사용하면 AEM Screens 관리자 또는 작성자가 스프레드시트 형식으로 *컨텐츠 할당 보고서*&#x200B;를 내보낼 수 있습니다.

## 컨텐츠 할당 보고서 사용 {#using-content-assignment-report}

AEM Screens 작성자 또는 관리자는 컨텐츠 할당 보고서를 통해 AEM Screens 프로젝트에서 생성된 모든 채널의 이미지, 비디오와 같은 모든 자산을 포함하는 보고서를 다운로드할 수 있습니다. 또한, 지정된 모든 디스플레이에 지정된 전체 채널의 정보를 포함하고 지정된 디스플레이에 지정된 모든 장치를 전달합니다.

컨텐츠 할당 보고서에서는 선택한 AEM Screens 프로젝트의 모든 채널, 자산, 표시 및 장치를 미리 볼 수 있을 뿐만 아니라 프로젝트의 수준 높은 구조를 제공합니다.

### 컨텐츠 할당 보고서 사용 {#downloading-content-assignment-report-fp}

#### 프로젝트 {#setting-up-project} 설정

AEM Screens 프로젝트에서 컨텐츠 할당 보고서를 다운로드하려면 아래 절차에 따르십시오.

1. **DemoScreens**&#x200B;라는 이름의 AEM Screens을 만듭니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/car-1.png)

1. **DemoScreens**&#x200B;에 **ChannelOne** 및 **ChannelTwo**&#x200B;와 같은 두 개의 시퀀스 채널을 만듭니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/car-2.png)

1. **ChannelOne**&#x200B;을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 이 채널에 자산(이미지/비디오)을 몇 개 추가합니다. 마찬가지로 **ChannelTwo**&#x200B;에 자산을 추가합니다.

1. **DemoScreens** —> **위치**&#x200B;에서 위치 폴더로 이동하고 **SanJose**, **Dublin** 및 **SanFrancisco**&#x200B;라는 이름의 세 개의 다른 위치를 만듭니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/car-3.png)

1. 각 위치로 이동하여 **SanJose** 위치, **Dublin** 위치 및 **SanJoseMain**&#x200B;과 같은 각 위치에 대한 디스플레이를 만듭니다. **SanFrancisco** 위치 아래.********

1. 각 디스플레이에 장치를 할당합니다.

   >[!NOTE]
   >디스플레이에 채널을 할당하는 방법에 대한 자세한 내용은 [채널 지정](/help/user-guide/channel-assignment.md)을 참조하십시오.

#### 콘텐트 할당 보고서 다운로드 {#downloading-content-assignment-report}

AEM Screens 프로젝트를 설정하고 이전 단계에 표시된 각 위치에 표시를 지정했으면 컨텐츠 지정 보고서를 다운로드할 준비가 됩니다.

>[!NOTE]
>컨텐츠 할당 보고서 기능은 프로젝트 수준에서만 액세스할 수 있습니다.

아래의 지침에 따라 콘텐트 할당 보고서를 다운로드하십시오.

1. AEM Screens 프로젝트로 이동하고 프로젝트 **DemoScreens**&#x200B;를 선택합니다.

1. 작업 표시줄에서 **컨텐트 지정 보고서**&#x200B;를 클릭합니다. Excel 시트를 로컬 컴퓨터에 다운로드해야 합니다.

   ![이미지](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >다운로드한 스프레드시트는 AEM Screens 프로젝트와 관련된 이러한 4개의 엔티티를 추가로 조사하는 데 사용할 수 있는 **채널**, **자산**, **디스플레이** 및 **장치**&#x200B;과 같은 4개의 열로 구성됩니다.





