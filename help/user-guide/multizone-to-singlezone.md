---
title: MultiZone에서 SingleZone 전환 사용 사례
description: MultiZone에서 SingleZone 전환 사용 사례에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone에서 SingleZone 전환 사용 사례
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 0cae7c19759fe3418a13ab2d7cc68f1b220f397d

---


# 다중 영역을 단일 영역으로 전환 {#multizone-to-singlezone-use-case}


## 사용 사례 설명 {#use-case-description}

이 섹션에서는 단일 영역 레이아웃 채널과 대체되는 다중 영역 레이아웃 채널을 설정하는 방법을 강조하는 사용 사례 예제를 설명합니다. 각 채널에는 이미지/비디오 에셋이 순서대로 지정됩니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주요 배우 {#primary-actors}

컨텐츠 작성자

## 프로젝트 설정 {#setting-up-the-project}

아래 절차에 따라 프로젝트를 설정하십시오.

1. 아래와 같이 ChannelTransition으로 명명된 AEM **Screens**&#x200B;프로젝트를 만듭니다.



1. **분할 화면 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.
   1. 마법사에서 **[왼쪽-L 막대 분할** 화면 채널]을 선택하고 MultiZoneLayout이라는 채널을 **만듭니다**.



   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. 자산을 각 영역으로 드래그하여 놓습니다. 다음 예제는 아래에 표시된 대로 채널에 비디오, 이미지 및 텍스트 배너를 보여줍니다.


1. **4개의 이미지가 포함된 2X2 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **2X2 분할 화면** 채널 템플릿을 선택하고 TwobyTwoChannel이라는 이름의 채널을 **만듭니다**.


   1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 편집기를 열고 아래 표시된 대로 4개의 이미지(4개의 다른 영역)를 해당 채널에 드래그하여 놓습니다.


1. **2개의 이미지로 1X2 분할 화면 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **1X2 분할 화면** 채널 템플릿을 선택하고 OnedbyTwoChannel이라는 이름의 채널을 **만듭니다**.


   1. 채널을 선택하고 작업 **표시줄에서** 편집을 클릭하여 편집기를 열고 아래에 표시된 것처럼 두 개의 이미지(두 개의 다른 영역)를 해당 채널에 드래그하여 놓습니다.


1. **하나의 전체 화면 비디오가 포함된 채널 만들기**

   1. 채널 폴더를 **선택하고** 작업 **표시줄에서 만들기를** 클릭하여 마법사를 열어 채널을 만듭니다.

   1. 마법사에서 **시퀀스** 채널 템플릿을 선택하고 FullScreensVideo라는 이름의 채널을 **만듭니다**.


   1. 채널을 선택하고 작업 **표시줄에서 편집을** 클릭하여 편집기를 열고 비디오 구성 요소를 해당 채널에 드래그하여 놓은 다음 아래와 같이 원하는 비디오를 추가합니다.

