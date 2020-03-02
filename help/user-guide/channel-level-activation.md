---
title: 채널 수준 활성화 - 단일 이벤트 재생
seo-title: 채널 수준 활성화 - 단일 이벤트 재생
description: 단일 이벤트 재생을 사용하여 채널 수준의 활성화를 이해하려면 이 안내서를 따르십시오.
seo-description: 단일 이벤트 재생을 사용하여 채널 수준의 활성화를 이해하려면 이 안내서를 따르십시오.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: 1dbbe62875cdc1a0c1c7d5fe45221d7ebd12207f

---


# 채널 수준 활성화 {#channel-level-activation-single-event-playback}

채널 수준 활성화를 사용하면 다음 주제를 다룹니다.

* 개요
* 채널 수준 활성화를 단일 이벤트 재생으로 사용

## 개요 {#overview}

***채널 수준 활성화를*** 사용하면 특정 설정 일정 후에 채널을 전환할 수 있습니다. 단일 이벤트 채널은 설정된 일정 후에 기본 채널을 대체하며 기본 채널이 해당 컨텐츠를 다시 재생할 때까지 특정 시간 동안 재생됩니다.

다음 예에서는 다음 주요 용어에 초점을 맞춰 솔루션을 제공합니다.

* 전역 시퀀스의 ***기본 시퀀스 채널***
* 설정된 시간에 한 번만 실행되는 ***단일 이벤트 채널***
* 기본 시퀀스 채널에서 발생하는 단일 재생 이벤트에 대한 ***설정 일정 및 우선 순위***

## 채널 수준 활성화 사용 {#using-channel-level-activation}

다음 섹션에서는 AEM Screens 프로젝트에 대한 채널 내에서 단일 이벤트 재생을 만드는 방법에 대해 설명합니다.

### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 다음 사전 요구 사항을 준비하여 채널 수준 활성화 구현을 시작하십시오.

* AEM Screens 프로젝트 만들기(이 예에서는 채널 **수준 활성화)**

* 채널 폴더 아래에 **MainAdChannel** 채널을 **만듭니다**

* 채널 폴더 아래에 다른 채널을 **TargetedSinglePlay** 로 **만듭니다**

* 두 채널에 관련 자산 추가

다음 이미지는 MainAdChannel **과** TargetedSinglePlay **채널이** 있는 채널 **수준 활성화** 프로젝트를 **ChannelsFolder에** 표시합니다.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>프로젝트를 만드는 방법과 시퀀스 채널을 만드는 방법에 대한 자세한 내용은 아래 리소스를 참조하십시오.
>
>* [프로젝트 만들기 및 관리](creating-a-screens-project.md)
   >
   >
* [채널 관리](managing-channels.md)
>



### 구현 {#implementation}

AEM Screens 프로젝트에서 채널 수준 활성화 구현에는 다음 세 가지 주요 작업이 포함됩니다.

1. **채널, 위치 및 표시를 포함한 프로젝트 분류 설정**
1. **표시할 채널 지정**
1. **예약 및 우선순위 설정**

다음 단계에 따라 기능을 구현합니다.

1. **위치 만들기**

   AEM Screens **프로젝트에서** 위치 폴더로 이동하여 위치를 영역으로 **만듭니다**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >위치를 만드는 방법에 대한 자세한 내용은 위치 **[만들기 및 관리를 참조하십시오](managing-locations.md)**.

1. **위치 아래에 표시 만들기**

   1. 채널 수준 **활성화 > 위치** > **영역으로** **이동합니다**.
   1. 영역을 **선택하고** 작업 표시줄에서 **+ 만들기를** 클릭합니다.
   1. 마법사에서 **표시를** 선택하고 영역 표시라는 이름의 디스플레이를 **만듭니다.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **표시할 채널 지정**

   MainAdChannel **의 경우:**

   1. 채널 레벨 활성화 > **위치** > **위치** **** > 영역 **> 영역** 표시 및 **** 클릭 채널작업 표시줄에서 채널 지정으로 이동합니다.
   1. **채널 지정** 대화 상자가 열립니다.
   1. Select **Reference Channel**.. by path.
   1. 채널 경로를 채널 수준 **활성화** —> **채널** —> ***기본*** 광고 ***채널로***&#x200B;선택합니다.
   1. 채널 **역할은** 기본 채널로 **채워집니다**.
   1. 우선 순위를 **1** 로 **선택합니다**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. **저장**&#x200B;을 클릭합니다.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >또한 채널 레벨 활성화 —> 위치 **—>** 위치 ******—> 표시** 영역 **클릭** 및 대시보드 **클릭 작업 표시줄에서 채널 지정을** 사용하여 디스플레이 대시보드에서 채널을 지정할 수 있습니다. 지정된 채널 및 예약 **패널에서** + 채널 **지정을** 클릭합니다.

   마찬가지로, 표시할 채널 **TargetedSinglePlay** *를 할당합니다.

   1. 채널 레벨 **활성화 위치** —> **위치** —> 영역 ******> 영역** 표시 **** 및 클릭 채널 지정작업 표시줄에서 채널을 지정합니다.
   1. **채널 지정** 대화 상자가 열립니다.
   1. Select **Reference Channel**.. by path.
   1. 채널 경로 **채널 수준 활성화** * —> **채널**—> ***타깃팅된*** SinglePlay ***를***&#x200B;선택합니다.
   1. 채널 **역할은** 타깃팅된 **singleplay로 채워집니다**.
   1. 우선 순위를 **2** 로 **설정합니다**.
   1. 아래 그림에서와 같이 지원되는 **이벤트를** 초기 **로드**, **유휴 화면** 및 **타이머***로선택합니다.
   1. 2018년 11월 27일 오후 11시 59분부터 **2018년 11월 28일 오전 12시 05분으로** 활성 **** 날짜를 선택합니다.
   1. **저장**&#x200B;을 클릭합니다.
   >[!CAUTION]
   MainAdSegment 채널보다 높은 **TargetedSinglePlay** 채널에 대한 우선 순위를 설정해야 **합니다** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   같은 날을 선택하려면 다음 날을 선택하고 수동으로 날짜를 같은 날로 편집해야 하지만 나중을 위해 편집합니다. 이로 인해 사용자가 지난 날짜를 선택할 수 없습니다. 아래 예를 참조하십시오.

   ![new1](assets/new1.gif)

## 결과 보기 {#viewing-the-results}

채널 설정 및 전체 표시가 완료되면 AEM Screens 플레이어를 실행하여 컨텐츠를 보십시오.

플레이어는 MainAdChannel의 컨텐츠를 **오후** 11:59(일정에 설정된 대로) **정확히** 오후 12:05 **까지** 해당 컨텐츠를 표시한 다음 MainAdChannel이해당 컨텐츠 재생을 다시 시작합니다.

>[!NOTE]
AEM Screen Player에 대한 자세한 내용은 다음 리소스를 참조하십시오.
* [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/)
* [AEM Screens 플레이어 작업](working-with-screens-player.md)

