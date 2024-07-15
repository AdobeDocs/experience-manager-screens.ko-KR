---
title: 단일 사용 전환 채널
description: 단일 사용 인계 채널을 만들려면 이 사용 사례를 따르십시오.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 단일 사용 전환 채널 {#single-use-takeover-channel}

다음 페이지에서는 특정 시간 동안 한 번 재생되는 단일 전환 채널을 만드는 방법에 대한 프로젝트 설정을 강조하는 사용 사례를 보여 줍니다.

## 사용 사례 설명 {#use-case-description}

이 사용 사례에서는 디스플레이 또는 디스플레이 그룹에 대해 일반 재생 채널에서 *을(를)*&#x200B;을(를) 대신하는 채널을 만드는 방법을 설명합니다. 인수는 오직 한 번 그리고 특정한 시간 동안만 발생한다.

예를 들어 금요일 오전 9시부터 오전 10시까지 재생되는 단일 TakeOver 채널이 있습니다. 이 시간 동안에는 다른 채널이 재생되지 않습니다. 이 시간 전후에는 단일 사용 인계 채널이 재생되지 않습니다. 다음 예제에서는 컨텐츠가 12월 31일 오전 12시 전부터 오전 12시 1분까지 2분 동안 재생되도록 하는 단일 인계 채널을 만드는 방법을 보여줍니다.

### 전제 조건 {#preconditions}

이 사용 사례를 시작하기 전에 다음 방법을 이해했는지 확인하십시오.

* **[채널 만들기 및 관리](managing-channels.md)**
* **[위치 만들기 및 관리](managing-locations.md)**
* **[일정 만들기 및 관리](managing-schedules.md)**
* **[장치 등록](device-registration.md)**

### 기본 작업자 {#primary-actors}

콘텐츠 작성자

## 프로젝트 설정 {#setting-up-the-project}

프로젝트를 설정하려면 아래 단계를 따르십시오.

**채널 및 디스플레이 설정**

1. 아래와 같이 **SingleUseTakeOver**(으)로 제목이 지정된 AEM Screens 프로젝트를 만듭니다.

   ![자산](assets/single-takeover1.png)

1. **채널** 폴더에 **MainAdChannel**&#x200B;을(를) 만듭니다.

   ![자산](assets/single-takeover2.png)

1. 작업 표시줄에서 **MainAdChannel**&#x200B;을 클릭하고 **편집**&#x200B;을 클릭합니다. 일부 에셋(이미지, 비디오, 포함된 시퀀스)을 채널로 드래그하여 놓습니다.

   ![자산](assets/single-takeover2.png)


   >[!NOTE]
   >이 예제의 **MainAdChannel**&#x200B;은 콘텐츠를 계속 재생하는 시퀀스 채널을 보여 줍니다.

   ![자산](assets/single-takeover3.png)

1. **MainAdChannel**&#x200B;에서 콘텐츠를 인수하고 특정 요일 및 시간에만 재생되는 **TakeOver** 채널을 만드십시오.

1. **TakeOver**&#x200B;를 클릭하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 일부 에셋을 채널로 드래그하여 놓습니다. 다음 예에서는 이 채널에 추가된 단일 영역 이미지를 보여 줍니다.

   ![자산](assets/single-takeover4.png)

1. 채널의 위치 및 디스플레이를 설정합니다. 예를 들어 이 프로젝트에 대해 다음 **Lobby** 위치와 **MainLobbyDisplay** 디스플레이를 설정했습니다.

   ![자산](assets/single-takeover5.png)

**디스플레이에 채널 할당**

1. **위치** 폴더에서 **MainLobbyDisplay** 디스플레이를 클릭합니다. 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

   ![자산](assets/single-takeover6.png)

   >[!NOTE]
   >디스플레이에 채널을 할당하는 방법을 알아보려면 **[채널 할당](channel-assignment.md)**&#x200B;을 참조하세요.

1. **채널 할당** 대화 상자에서 필드(**채널 경로**, **우선 순위**, **지원되는 이벤트**)를 채우고 **저장**&#x200B;을 클릭합니다. 이제 디스플레이에 **MainAdChannel**&#x200B;을(를) 할당했습니다.

   ![자산](assets/single-takeover7.png)

1. **위치** 폴더에서 **TakeOver** 표시를 클릭합니다. 일회용 인계 채널을 할당할 수 있도록 작업 표시줄에서 **채널 할당**&#x200B;을 클릭합니다.

1. 예약된 시간에 디스플레이에 **TakeOver** 채널을 할당하고 **채널 할당** 대화 상자에서 다음 필드를 채운 다음 **저장**&#x200B;을 클릭합니다.

   * **채널 경로**: TakeOver 채널의 경로를 클릭합니다.
   * **우선 순위**: 이 채널의 우선 순위를 **MainAdChannel**&#x200B;보다 크게 설정합니다. 예를 들어 이 예제에서 설정한 우선 순위는 8입니다.

     >[!NOTE]
     >우선 순위는 정상 재생 채널의 우선 순위 값보다 높은 임의의 값일 수 있다.
   * **지원되는 이벤트**: **유휴 화면** 및 **타이머**&#x200B;를 클릭합니다.
   * **일정**: 이 채널을 표시할 일정에 대한 텍스트를 입력하십시오. 예를 들어, 여기에 텍스트를 입력하면 컨텐츠가 12월 31일 오전 12시 전 2분에서 오전 12시 1분까지 재생될 수 있습니다.
이 예제에 언급된 **일정**&#x200B;의 텍스트는 23:58 이후 12월 31일에 *이고 00.01 이전 1월 1일에도*&#x200B;입니다.

     ![자산](assets/single-takeover8.png)

     **SingleUseTakeOver** > **위치** > **로비** > **MainLobbyDisplay**&#x200B;에서 표시로 이동합니다. 작업 표시줄에서 **대시보드**&#x200B;를 클릭하면 아래와 같이 우선 순위가 지정된 채널을 볼 수 있습니다.

     >[!NOTE]
     >인수채널의 우선 순위를 가장 높게 설정하는 것이 의무적이다.

     ![자산](assets/single-takeover9.png)

>[!NOTE]
>
>한 번 재생되면 Single Use TakeOver 채널을 삭제하는 것이 좋습니다.
