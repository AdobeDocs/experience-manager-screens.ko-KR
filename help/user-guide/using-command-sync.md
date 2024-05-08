---
title: 명령 동기화 사용
description: AEM Screens에서 명령 동기화를 사용하는 방법에 대해 자세히 알아보십시오.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 명령 동기화 {#command-sync}

다음 페이지에서는 명령 동기화를 사용하는 방법에 대해 설명합니다. 명령 동기화를 사용하면 여러 플레이어에서 동기화된 재생을 사용할 수 있습니다. 플레이어는 다른 콘텐츠를 재생할 수 있지만 각 에셋의 지속 시간은 동일해야 합니다.

>[!IMPORTANT]
>
>이 기능은 포함된 시퀀스, 동적 포함된 시퀀스, 응용 프로그램 채널 또는 전환을 지원하지 않습니다.

## 개요 {#overview}

디지털 사이니지 솔루션은 비디오 월 및 동기화된 재생을 지원하여 새해 카운트다운이나 여러 화면에서 재생하기 위해 얇게 썬 대형 비디오와 같은 시나리오를 지원해야 하며, 여기에서 명령 동기화가 실행됩니다.

명령 동기화를 사용하려면 한 플레이어가 *기본* 명령을 보내면 다른 모든 플레이어가 *클라이언트* 명령을 받으면 재생합니다.

다음 *기본* 는 항목 재생을 시작하려고 할 때 명령을 등록된 모든 클라이언트에 보냅니다. 이것의 페이로드는 재생될 항목의 인덱스 및/또는 재생될 요소의 외부 html일 수 있다.

## 명령 동기화 구현 {#using-command-sync}

다음 섹션에서는 AEM Screens 프로젝트에서 명령 동기화를 사용하는 방법에 대해 설명합니다.

>[!NOTE]
>
>동기화된 재생을 위해, 모든 하드웨어 장치들이 동일한 하드웨어 사양들 및 바람직하게는 동일한 운영 체제를 갖는 것이 요구된다. 서로 다른 하드웨어와 운영 체제 간의 동기화는 권장되지 않습니다.

### 프로젝트 설정 {#setting-up}

명령 동기화 기능을 사용하기 전에 프로젝트와 채널에 프로젝트의 콘텐츠가 설정되어 있는지 확인하십시오.

1. 다음 예제에서는 이라는 데모 프로젝트를 보여 줍니다. **명령 동기화 데모** 및 시퀀스 채널 **채널 로비**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >채널을 만들거나 채널에 콘텐츠를 추가하는 방법은 을 참조하십시오. [채널 만들기 및 관리](/help/user-guide/managing-channels.md)

   이 채널에는 아래 그림과 같이 다음 콘텐츠가 포함되어 있습니다.

   ![image1](assets/command-sync/command-sync2-1.png)

1. 위치 만들기 **로비** 제목이 인 디스플레이 **로비 디스플레이** 다음에서 **위치** 아래 그림과 같은 폴더입니다.
   ![image1](assets/command-sync/command-sync3-1.png)

1. 채널 할당, **채널 로비** (으)로 **로비 디스플레이**. 이제 디스플레이 대시보드에서 디스플레이에 할당된 채널을 볼 수 있습니다.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >디스플레이에 채널을 할당하는 방법에 대한 자세한 내용은 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md).

1. 다음으로 이동 **장치** 폴더를 삭제합니다.
1. 클릭 **장치 관리자** 작업 표시줄에서

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >장치를 등록하는 방법에 대해 알아보려면 다음을 참조하십시오. [장치 등록](/help/user-guide/device-registration.md)

1. 이 예에서는 데모 목적으로 chrome 장치와 Windows Player를 두 개의 개별 장치로 보여 줍니다. 두 장치 모두 동일한 디스플레이를 가리킵니다.
   ![image1](assets/command-sync6.png)

### 채널 설정 업데이트 중

1. 다음으로 이동 **채널 로비**.
1. 클릭 **편집** 작업 표시줄에서
1. 아래 그림과 같이 전체 채널을 클릭합니다.
   ![image1](assets/command-sync/command-sync7-1.png)

1. 렌치 아이콘을 클릭합니다.
   ![image1](assets/command-sync/command-sync8-1.png)

1. 다음에서 **페이지** 대화 상자에서 *동기화됨* 키워드 입력 **전략** 필드.
   ![image1](assets/command-sync/command-sync9-1.png)


### 기본 설정 {#setting-up-primary}

1. 에서 디스플레이 대시보드로 이동합니다. **명령 동기화 데모** > **위치**  > **로비** > **로비 디스플레이** 및 클릭 **대시보드** 작업 표시줄에서
에서 두 장치(chrome 및 Windows Player)를 확인합니다. **장치** 패널, 다음 참조:
   ![image1](assets/command-sync/command-sync10-1.png)

1. 다음에서 **장치** 패널을 통해 기본 장치로 설정할 장치를 클릭합니다. 다음 예에서는 Chrome 장치를 기본 장치로 설정하는 방법을 보여 줍니다. 클릭 **기본 장치로 설정**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. 에 IP 주소 입력 **기본 장치로 설정** 및 클릭 **저장**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>여러 장치를 기본 장치로 설정할 수 있습니다.

### 기본과 동기화 중 {#sync-up-primary}

1. Chrome 장치를 기본 장치로 설정한 후 다른 장치(이 경우 Windows Player)를 동기화하여 기본 장치와 동기화합니다.
에서 다른 장치(이 경우 Windows Player)를 클릭합니다. **장치** 패널 및 클릭 **기본 장치와 동기화**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. 목록에서 장치를 클릭하고 **저장**.

   >[참고:]
   > 다음 **기본 장치와 동기화** 대화 상자에 기본 디바이스 목록이 표시됩니다. 원하는 항목을 선택합니다.

1. 장치(Windows Player)가 기본 장치(Chrome Player)에 동기화되면 **장치** 패널.

   ![image1](assets/command-sync/command-sync14-1.png)

### 기본과 동기화 해제 {#desync-up-primary}

장치를 기본 장치에 동기화한 후 해당 장치에서 할당을 비동기화할 수 있습니다.

>[!NOTE]
>
>기본 장치의 동기화를 해제하면 해당 기본 장치와 연결된 모든 클라이언트 장치의 연결도 해제됩니다.

기본 장치에서 동기화를 제거하려면 아래 단계를 수행하십시오.

1. 다음 위치로 이동 **장치** 패널을 연 다음 장치를 클릭합니다.

1. 클릭 **장치 동기화 해제** 따라서 기본 장치에서 클라이언트를 비동기화할 수 있습니다.

   ![image1](assets/command-sync/command-sync15-1.png)

1. 클릭 **확인** 기본 장치에서 선택한 장치의 동기화를 해제합니다.

   >[참고:]
   > 기본 장치를 클릭하고 동기화 해제 옵션을 사용하면 기본 장치에 연결된 모든 장치가 한 단계에서 동기화되지 않습니다.
