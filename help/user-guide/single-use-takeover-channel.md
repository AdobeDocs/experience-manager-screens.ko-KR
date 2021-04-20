---
title: 단일 사용 인계채널
seo-title: 단일 사용 인계채널
description: 단일 사용 TakeOver 채널을 만들려면 이 사용 사례를 따르십시오.
seo-description: 단일 사용 TakeOver 채널을 만들려면 이 사용 사례를 따르십시오.
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---


# 단일 사용 테이크 오버 채널 {#single-use-takeover-channel}

다음 페이지에서는 특정 시간에 한 번만 재생되는 단일 TakeOver 채널을 만드는 방법에 대한 프로젝트 설정에 중점을 둔 사용 사례를 보여줍니다.


## 사용 사례 설명 {#use-case-description}

이 사용 사례는 표시 또는 디스플레이 그룹에 대해 일반적으로 재생되는 채널에서 *이*을(를) 차지하는 채널을 만드는 방법을 설명합니다. 인계는 한 번만 그리고 특정 시간에 발생합니다.
예를 들어 금요일 오전 9시부터 오전 10시까지 재생되는 단일 TakeOver 채널이 있습니다. 이 시간 동안에는 다른 채널이 재생되지 않습니다. 이 시간 전후에 단일 사용 인계 채널이 재생되지 않습니다. 다음 예에서는 12월 31일 오전 12시 10분부터 오전 12시까지 2분 동안 내용을 재생할 수 있는 단일 인계 채널 만들기를 보여줍니다.

### 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해해야 합니다.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[예약 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 주 배우 {#primary-actors}

컨텐츠 작성자

## 프로젝트 {#setting-up-the-project} 설정

프로젝트를 설정하려면 아래 절차를 따르십시오.

**채널 및 표시 설정**

1. 아래와 같이 **SingleUseTakeOver**&#x200B;라는 이름의 AEM Screens 프로젝트를 만듭니다.

   ![자산](assets/single-takeover1.png)

1. **채널** 폴더에 **MainAdChannel**&#x200B;을 만듭니다.

   ![자산](assets/single-takeover2.png)

1. **MainAdChannel**&#x200B;을 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 일부 자산(이미지, 비디오, 포함된 시퀀스)을 채널에 드래그하여 놓습니다.

   ![자산](assets/single-takeover2.png)


   >[!NOTE]
   >이 예제의 **MainAdChannel**&#x200B;에서는 컨텐츠를 지속적으로 재생하는 시퀀스 채널을 보여 줍니다.

   ![자산](assets/single-takeover3.png)

1. **MainAdChannel**&#x200B;의 컨텐츠를 인계받고 특정 일 및 시간에 대해서만 재생되는 **TakeOver** 채널을 만듭니다.

1. **TakeOver**&#x200B;를 선택하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 일부 자산을 채널에 드래그하여 놓습니다. 다음 예에서는 이 채널에 추가된 단일 영역 이미지를 보여 줍니다.

   ![자산](assets/single-takeover4.png)

1. 채널의 위치와 디스플레이를 설정합니다. 예를 들어 이 프로젝트에 대해 **Lobby** 위치 및 **MainLobbyDisplay**&#x200B;가 설정되어 있습니다.

   ![자산](assets/single-takeover5.png)

**디스플레이에 채널 지정**

1. **위치** 폴더에서 **MainLobbyDisplay** 표시를 선택합니다. 작업 표시줄에서 **채널 지정**&#x200B;을 클릭합니다.

   ![자산](assets/single-takeover6.png)

   >[!NOTE]
   >디스플레이에 채널을 지정하는 방법에 대해 알아보려면 **[채널 지정](channel-assignment.md)**&#x200B;을 참조하십시오.

1. **채널 지정** 대화 상자에서 **채널 경로**, **우선 순위** 및 **지원되는 이벤트**)를 채우고 **저장**&#x200B;을 클릭합니다. 이제 디스플레이에 **MainAdChannel**&#x200B;을(를) 할당했습니다.

   ![자산](assets/single-takeover7.png)

1. **위치** 폴더에서 **TakeOver** 표시를 선택합니다. 작업 표시줄에서 **채널 지정**&#x200B;을 클릭하여 단일 사용 인계 채널을 지정합니다.

1. **TakeOver** 채널을 예약된 시간에 디스플레이에 지정하고 **채널 지정** 대화 상자에서 다음 필드를 채우려면 **저장**&#x200B;을 클릭합니다.

   * **채널 경로**:TakeOver 채널의 경로를 선택합니다.
   * **우선 순위**:이 채널의 우선 순위를 MainAdChannel보다 크게  **설정합니다**. 예를 들어 이 예에서 설정된 우선 순위는 8입니다.

      >[!NOTE]
      >우선 순위는 일반적으로 재생되는 채널의 우선 순위 값보다 높은 값일 수 있습니다.
   * **지원되는 이벤트**:유휴 화면  **및** 타이머를  **선택합니다**.
   * **일정**:이 채널이 디스플레이를 실행할 일정에 대한 텍스트를 입력합니다. 예를 들어, 여기 있는 텍스트를 사용하면 12월 31일 오전 12시 12분 전에 2분 동안 내용을 재생할 수 있습니다.
이 예제에 언급된 **일정**&#x200B;의 텍스트는 23:58 이후 12월 31일에 *이고, 또한 00.01* 전 1일에 있습니다.

      ![자산](assets/single-takeover8.png)

      **SingleUseTakeOver** —> **위치** —> **로비** —> **MainLobbyDisplay**&#x200B;에서 디스플레이를 클릭하고 작업 표시줄에서 **대시보드**&#x200B;를 클릭하여 지정된 채널을 표시합니다. 우선 순위.

      >[!NOTE]
      >인계 채널의 우선 순위를 가장 높은 것으로 설정해야 합니다.

      ![자산](assets/single-takeover9.png)

>[!NOTE]
>
>재생되면 단일 사용 인계받기 채널을 삭제하는 것이 가장 좋습니다.