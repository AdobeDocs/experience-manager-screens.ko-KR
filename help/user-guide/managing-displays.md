---
title: 디스플레이 생성 및 관리
seo-title: 디스플레이 관리
description: 새 디스플레이 및 장치 구성을 생성하는 방법에 대해 알려면 이 페이지를 따르십시오. 추가로 디스플레이 대시보드에 대해서도 학습합니다.
seo-description: 새 디스플레이 및 장치 구성을 생성하는 방법에 대해 알려면 이 페이지를 따르십시오. 추가로 디스플레이 대시보드에 대해서도 학습합니다.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 디스플레이 생성 및 관리 {#creating-and-managing-displays}

디스플레이는 일반적으로 서로 인접하여 배치된 화면들의 가상 그룹입니다. 일반적으로 디스플레이는 설치와 관련하여 영구적이며 컨텐츠 작성자가 물리적으로 대응하는 부분이 아닌 논리적 디스플레이로서 작업에 사용하고 항상 참조하는 개체입니다.

위치를 생성한 후에는 해당 위치에 대한 새로운 디스플레이를 생성해야 합니다.

이 페이지에서는 스크린용 디스플레이의 만들기 및 관리에 대해 보여줍니다.

**전제 조건**:

* [스크린 구성 및 배치](configuring-screens-introduction.md)
* [스크린 프로젝트 만들기 및 관리](creating-a-screens-project.md)
* [채널 만들기 및 관리](managing-channels.md)
* [위치 만들기 및 관리](managing-locations.md)

## 새 디스플레이 생성 {#creating-a-new-display}

>[!NOTE]
>
>디스플레이를 생성하려면 먼저 위치를 생성해야 합니다. To see how to create a location, see [Create and Manage Locations](managing-locations.md) for more information.

사용자의 위치에 새 디스플레이를 생성하려면 아래 절차를 따르십시오.

1. Navigate to the appropriate location, for example `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Select your location folder and tap/click **Create** next to the plus icon in the action bar. 마법사가 열립니다.
1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter **Name** and **Title** for your display location.

1. Under the **Display** tab, choose the details of the Layout. Choose the desired **Resolution** (example as, as **Full HD**). 또한 가로 및 세로 장치의 수를 선택할 수 있습니다.

1. **만들기**&#x200B;를 클릭합니다.

The display (*StoreDisplay*) is created and added to the location (*SanJose*).

![display](assets/display.gif)

디스플레이가 적절히 생성되면 다음 단계에서는 해당 특정 디스플레이에 대한 장치 구성을 생성합니다. 아래 섹션에 따라 새 장치 구성을 생성하십시오.

>[!NOTE]
>
>**다음 단계**:
>
>위치에 대한 디스플레이가 생성되면 컨텐츠를 활용할 수 있도록 채널을 디스플레이에 지정해야 합니다.
>
>See [Assign Channels](channel-assignment.md) section to learn how to assign a channel to the display.

## 새 장치 구성 생성 {#creating-a-new-device-config}

장치 구성은 아직 설치되지 않은 실제 디지털 신호 체계 장치의 자리 표시자 역할을 합니다.

아래 절차에 따라 새 장치 구성을 생성하십시오.

1. 예를 들어, 적절한 표시로 이동합니다 `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Select your display folder and tap/click **View Dashboard** in the action bar.
1. Tap/click the **+ Add Device Config** on the top right of the **Devices** panel.

1. Select the **Device Config** as the required template as and tap/click **Next**.

1. Enter the properties as required and tap/click **Create**.

The device config is created and added to the current display (in the following demonstration, the new device config is *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

장치 구성이 위치에 있는 사용자의 디스플레이로 설정되면 다음 단계에서는 디스플레이에 채널을 지정합니다.

>[!NOTE]
>
>장치 구성이 위치에 있는 사용자의 디스플레이로 설정되면 다음 단계에서는 디스플레이에 채널을 지정합니다.
>
>As shown in the figure below, if the device config is displayed as unassigned in the **DEVICES** pannel, if no channel is assigned to that particular device config.
>
>채널 생성 및 관리에 대한 사전 이해가 있어야 합니다. 자세한 [내용은 채널](managing-channels.md) 만들기 및 관리를 참조하십시오.

![chlimage_1-9](assets/chlimage_1-9.png)

## 디스플레이 대시보드 {#display-dashboard}

디스플레이 대시보드에서는 장치의 디스플레이 장치 및 장치 구성을 관리하기 위한 다양한 패널을 제공합니다.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>각 항목을 개별적으로 살펴보는 대신 대시보드 목록을 선택하고 항목에 대한 벌크 작업을 트리거할 수 있습니다.
>
>예를 들어, 다음 이미지는 디스플레이 대시보드에서 여러 채널을 선택할 수 있는 방법을 보여줍니다.

![cqdoc9456](assets/cqdoc9456.gif)

### 디스플레이 정보 패널 {#display-information-panel}

**디스플레이 정보** 패널은 디스플레이 속성을 제공합니다.

Click on the (**...**) in the top right corner in the **DISPLAY INFORMATION **panel to view the properties and preview the display.

![chlimage_1-10](assets/chlimage_1-10.png)

#### 속성 보기 {#viewing-properties}

디스플레이의 속성을 보거나 변경하려면 **속성**&#x200B;을 클릭하십시오.

Additionally, you can adjust the event timer value for your interactive channel in **Idle timeout **property under **Display** tab. 기본값은 *300초*&#x200B;로 설정되어 있습니다.

Use **CRXDE Lite**, to access the **idleTimeout** property, that is, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### 지정된 채널 패널 {#assigned-channels-panel}

**지정된 채널** 패널에는 이 장치에 지정된 채널이 표시됩니다.

![chlimage_1-11](assets/chlimage_1-11.png)

### 장치 패널 {#devices-panel}

**장치** 패널은 장치 구성에 대한 정보를 제공합니다.

Click on the (**...**) in the top right corner in the **DEVICES **panel to add device configs and update devices.

![chlimage_1-12](assets/chlimage_1-12.png)

또한 장치 구성을 클릭하여 속성을 보거나 장치를 할당하거나 완전히 삭제합니다.

![chlimage_1-13](assets/chlimage_1-13.png)

#### 다음 단계 {#the-next-steps}

위치에 대한 디스플레이 생성을 완료하면 디스플레이를 위한 채널을 지정해야 합니다.

See [Assign Channels](channel-assignment.md) for more details.
