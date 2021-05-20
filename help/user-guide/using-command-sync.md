---
title: 명령 동기화 사용
seo-title: 명령 동기화 사용
description: 명령 동기화를 사용하는 방법에 대해 알아보려면 이 페이지를 따르십시오.
seo-description: 명령 동기화를 사용하는 방법에 대해 알아보려면 이 페이지를 따르십시오.
feature: 스크린 작성
role: Administrator, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 2%

---

# 명령 동기화 {#command-sync}

다음 페이지에서는 명령 동기화를 사용하는 방법에 대해 설명합니다. 명령 동기화를 사용하면 서로 다른 플레이어에서 동기화된 재생이 가능합니다. 플레이어에서는 다른 콘텐츠를 재생할 수 있지만 각 자산의 지속 시간은 같아야 합니다.

>[!IMPORTANT]
>
>이 기능은 포함된 시퀀스, 동적 포함된 시퀀스, 응용 프로그램 채널 또는 전환을 지원하지 않습니다.

## 개요 {#overview}

디지털 사이니지 솔루션은 신년 카운트다운이나 여러 화면에서 재생되도록 분할된 대형 비디오와 같은 시나리오를 지원하기 위해 비디오 벽과 동기화된 재생을 지원해야 하며, 이때 Command Sync가 실행됩니다.

명령 동기화를 사용하기 위해 한 플레이어가 *master* 역할을 하고 명령을 전송하며 다른 모든 플레이어가 *clients* 역할을 수행하고 명령을 받을 때 재생합니다.

*master*&#x200B;는 항목의 재생을 시작하려고 할 때 등록된 모든 클라이언트에 명령을 보냅니다. 이 페이로드의 페이로드는 재생할 항목의 색인 및/또는 재생할 요소의 외부 html일 수 있습니다.

## 명령 동기화 구현 {#using-command-sync}

다음 섹션에서는 AEM Screens 프로젝트에서 명령 동기화를 사용할 수 있는 방법에 대해 설명합니다.

>[!NOTE]
>
>동기화된 재생의 경우, 모든 하드웨어 장치에 동일한 하드웨어 사양이 있고, 바람직하게는 동일한 운영 체제가 있어야 합니다. 다른 하드웨어와 운영 체제 간의 동기화는 권장되지 않습니다.

### 프로젝트 {#setting-up} 설정

명령 동기화 기능을 사용하기 전에 프로젝트에 대해 설정된 컨텐츠 및 프로젝트가 있는지 확인하십시오.

1. 다음 예에서는 **CommandSyncDemo** 및 시퀀스 채널 **ChannelLobby**&#x200B;을 보여주는 데모 프로젝트를 소개합니다.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >채널을 만들거나 채널에 컨텐츠를 추가하는 방법에 대해 알려면 [채널 만들기 및 관리](/help/user-guide/managing-channels.md) 를 참조하십시오

   채널에는 아래 그림과 같이 다음 컨텐츠가 포함되어 있습니다.

   ![image1](assets/command-sync/command-sync2-1.png)

1. **Lobby** 위치를 만들고 **Locations** 폴더에서 **LobbyDisplay**라는 표시도 아래 그림과 같이 작성하십시오.
   ![image1](assets/command-sync/command-sync3-1.png)

1. **ChannelLobby** 채널을 **LobbyDisplay**에 할당합니다. 이제 디스플레이 대시보드에서 디스플레이에 지정된 채널을 볼 수 있습니다.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >디스플레이에 채널을 지정하는 방법에 대한 자세한 내용은 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)를 참조하십시오.

1. **장치** 폴더로 이동하고 작업 표시줄에서 **장치 관리자**&#x200B;를 클릭하여 장치를 등록합니다.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >장치를 등록하는 방법에 대한 자세한 내용은 [장치 등록](/help/user-guide/device-registration.md) 을 참조하십시오

1. 데모 목적으로 이 예에서는 chrome 장치와 windows 플레이어를 두 개의 개별 장치로 보여줍니다. 두 장치 모두 동일한 디스플레이를 가리킵니다.
   ![image1](assets/command-sync6.png)

### 채널 설정 업데이트

1. **ChannelLobby**&#x200B;로 이동하고 작업 표시줄에서 **편집**&#x200B;을 클릭하여 채널 설정을 업데이트합니다.

1. 아래 그림과 같이 전체 채널을 선택합니다.
   ![image1](assets/command-sync/command-sync7-1.png)

1. 공구아이콘을 클릭하여 **페이지** 대화 상자를 엽니다.
   ![image1](assets/command-sync/command-sync8-1.png)

1. **전략** 필드에 *동기화된* 키워드를 입력합니다.

   ![image1](assets/command-sync/command-sync9-1.png)


### 마스터 {#setting-up-master} 설정

1. **CommandSyncDemo** —> **위치** —> **로비** —> **LobbyDisplay**&#x200B;에서 디스플레이 대시보드로 이동하여 작업 표시줄에서 **대시보드**를 클릭합니다.
아래 그림과 같이 **DEVICES** 패널에 두 개의 장치(chrome 및 windows 플레이어)가 표시됩니다.
   ![image1](assets/command-sync/command-sync10-1.png)

1. **장치** 패널에서 마스터로 설정할 장치를 선택합니다. 다음 예에서는 Chrome 장치를 마스터로 설정하는 방법을 보여줍니다. **마스터 장치로 설정**&#x200B;을 클릭합니다.

   ![image1](assets/command-sync/command-sync11-1.png)

1. **마스터 장치로 설정**&#x200B;에 IP 주소를 입력하고 **저장**&#x200B;을 클릭합니다.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>여러 장치를 마스터로 설정할 수 있습니다.

### 기본 {#sync-up-master}과 동기화 중

1. Chrome 장치를 마스터로 설정한 후에는 다른 장치(이 경우 Windows 플레이어)를 동기화하여 마스터와 동기화할 수 있습니다.
**장치** 패널에서 다른 장치(이 경우 Windows 플레이어)를 선택하고 아래 그림과 같이 **마스터 장치에 동기화**&#x200B;를 클릭합니다.

   ![image1](assets/command-sync/command-sync13-1.png)

1. 목록에서 장치를 선택하고 **저장**&#x200B;을 클릭합니다.

   >[메모:]
   > **마스터 장치에 동기화** 대화 상자에 마스터 장치 목록이 표시됩니다. 원하는 환경 설정 중 하나를 선택할 수 있습니다.

1. 장치(Windows 플레이어)가 마스터(Chrome 플레이어)에 동기화되면 **장치** 패널에 동기화된 장치가 표시됩니다.

   ![image1](assets/command-sync/command-sync14-1.png)

### 기본 {#desync-up-master}과 동기화 취소

장치나 장치를 마스터에 동기화한 후에는 해당 장치에서 할당을 동기화 해제할 수 있습니다.

>[!NOTE]
>
>마스터 장치를 동기화를 해제하면 해당 마스터 장치와 연결된 모든 클라이언트 장치의 연결이 해제됩니다.

마스터 장치에서 동기화를 제거하려면 아래 단계를 수행하십시오.

1. **장치** 패널로 이동하여 장치를 선택합니다.

1. **Desync 장치**&#x200B;를 클릭하여 마스터 장치에서 클라이언트를 다시 동기화합니다.

   ![image1](assets/command-sync/command-sync15-1.png)

1. **Confirm**&#x200B;을 클릭하여 마스터에서 선택한 장치를 역동기화합니다.

   >[메모:]
   > 마스터 장치를 선택하고 동기화 해제 옵션을 사용하면 마스터에 연결된 모든 장치가 한 단계에서 동기화되지 않습니다.
