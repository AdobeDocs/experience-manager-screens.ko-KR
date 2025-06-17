---
title: 디스플레이 만들기 및 관리
description: AEM Screens에서 디스플레이 및 장치 구성을 만드는 방법에 대해 알아봅니다. 또한 디스플레이 대시보드에 대해서도 알아봅니다.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 1%

---

# 디스플레이 만들기 및 관리 {#creating-and-managing-displays}

디스플레이는 서로의 옆에 위치된 스크린들의 가상 그룹화이다. 디스플레이는 설치와 관련하여 영구적입니다. 콘텐츠 작성자가 작업하고 항상 를 실제 카운터 부분이 아닌 논리 표시로 참조하는 개체입니다.

위치를 만들 때는 위치에 대한 디스플레이를 만들어야 합니다.

이 페이지에서는 Screens용 디스플레이 생성 및 관리 방법을 보여 줍니다.

**필수 구성 요소**:

* [Screens 구성 및 배포](configuring-screens-introduction.md)
* [Screens 프로젝트 만들기 및 관리](creating-a-screens-project.md)
* [채널 만들기 및 관리](managing-channels.md)
* [위치 생성 및 관리](managing-locations.md)

## 새 디스플레이 만들기 {#creating-a-new-display}

>[!NOTE]
>
>디스플레이를 만들기 전에 위치를 만듭니다. 자세한 내용은 [위치 만들기 및 관리](managing-locations.md)를 참조하십시오.

1. 적절한 위치(예: `http://localhost:4502/screens.html/content/screens/TestProject`)로 이동합니다.
1. 위치 폴더를 클릭하고 작업 표시줄에서 더하기 아이콘 옆에 있는 **만들기**&#x200B;를 클릭합니다.
1. **만들기** 마법사에서 **표시**&#x200B;를 클릭한 다음 **다음**&#x200B;을 클릭합니다.
1. 표시 위치에 대한 **이름** 및 **제목**&#x200B;을 입력하십시오.
1. **디스플레이** 탭에서 레이아웃의 세부 정보를 선택합니다. 원하는 **해상도**&#x200B;를 선택합니다(예: **풀 HD**). 장치 수를 수평 및 수직으로 선택합니다.
1. **만들기**&#x200B;를 클릭합니다.

디스플레이(*StoreDisplay*)를 만들어 위치(*SanJose*)에 추가합니다.

![디스플레이](assets/display.gif)

디스플레이가 있는 경우 다음 단계는 해당 특정 디스플레이에 대한 장치 구성을 만드는 것입니다.

>[!NOTE]
>
>**다음 단계**:
>
>위치에 대한 디스플레이를 만들 때 디스플레이에 채널을 할당하여 콘텐츠를 사용합니다.
>
>디스플레이에 채널을 할당하는 방법에 대해 알아보려면 [채널 할당](channel-assignment.md) 섹션을 참조하십시오.

## 새 장치 구성 만들기 {#creating-a-new-device-config}

장치 구성은 아직 설치되지 않은 실제 디지털 사이니지 장치의 자리 표시자 역할을 합니다.

1. 적절한 디스플레이(예: `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`)로 이동합니다.
1. 표시 폴더를 클릭하고 작업 표시줄에서 **대시보드 보기**&#x200B;를 클릭합니다.
1. **장치** 패널의 오른쪽 상단에서 **+ 장치 구성 추가**&#x200B;를 클릭합니다.

1. 필요한 템플릿으로 **장치 구성**&#x200B;을 클릭하고 **다음**&#x200B;을 클릭합니다.

1. 필요에 따라 속성을 입력하고 **만들기**&#x200B;를 클릭합니다.

장치 구성이 만들어지고 현재 디스플레이에 추가됩니다(다음 데모에서는 새 장치 구성이 *DeviceConfig*&#x200B;임).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>장치 구성이 해당 위치의 디스플레이에 설정되면 다음 단계는 디스플레이에 채널을 할당하는 것입니다.
>
>아래 그림과 같이 장치 구성이 **DEVICES** 패널에 할당되지 않은 것으로 표시되면 특정 장치 구성에 채널이 할당되지 않은 것입니다.
>
>채널을 만들고 관리하는 방법을 미리 알고 있어야 합니다. 자세한 내용은 [채널 만들기 및 관리](managing-channels.md)를 참조하십시오.

![chlimage_1-9](assets/chlimage_1-9.png)

## 디스플레이 대시보드 {#display-dashboard}

디스플레이 대시보드는 디스플레이 디바이스를 관리하기 위한 다양한 패널을 제공합니다. 또한 장치를 구성할 수 있습니다.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>각 항목을 개별적으로 검토하지 않고 대시보드 목록을 클릭하고 항목에 대한 일괄 작업을 트리거할 수 있습니다.
>
>예를 들어 다음 이미지는 디스플레이 대시보드에서 여러 채널을 클릭하는 방법을 보여 줍니다.

![cqdoc9456](assets/cqdoc9456.gif)

### 정보 패널 표시 {#display-information-panel}

**디스플레이 정보** 패널에서 디스플레이 속성을 제공합니다.

속성을 보고 디스플레이를 미리 볼 수 있도록 **정보 표시** 패널의 오른쪽 상단 모서리에서 (**...**)을 클릭합니다.


#### 속성 보기 {#viewing-properties}

디스플레이 속성을 보거나 변경하려면 **속성**&#x200B;을 클릭하세요.

또한 **디스플레이** 탭에서 대화형 채널의 이벤트 타이머 값을 조정할 수 있습니다. 기본값은 *300초*(으)로 설정되어 있습니다.

**CRXDE Lite**&#x200B;을(를) 사용하여 **idleTimeout** 속성, 즉 `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`에 액세스합니다.


### 할당된 채널 패널 {#assigned-channels-panel}

**할당된 채널** 패널에 이 장치에 할당된 채널이 표시됩니다.


### 장치 패널 {#devices-panel}

**장치** 패널에서 장치 구성에 대한 정보를 제공합니다.

장치 구성을 추가하고 장치를 업데이트할 수 있도록 **장치** 패널의 오른쪽 상단 모서리에서 (**...**)을(를) 클릭합니다.

또한 장치 구성을 클릭하여 속성을 보거나 장치를 할당하거나 완전히 삭제합니다.

![chlimage_1-13](assets/chlimage_1-13.png)

#### 다음 단계 {#the-next-steps}

위치에 대한 디스플레이 만들기를 완료하면 디스플레이에 대한 채널을 할당합니다.

자세한 내용은 [채널 할당](channel-assignment.md)을 참조하세요.
