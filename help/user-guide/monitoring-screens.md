---
title: 장치 컨트롤 센터 문제 해결
seo-title: 스크린 모니터링
description: 장치 대시보드를 사용하여 Screens 플레이어 활동 및 장치의 성능을 모니터링하고 문제를 해결하려면 이 페이지를 따르십시오.
seo-description: 장치 대시보드를 사용하여 Screens 플레이어 활동 및 장치의 성능을 모니터링하고 문제를 해결하려면 이 페이지를 따르십시오.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 장치 컨트롤 센터 문제 해결 {#troubleshooting-device-control-center}

장치 대시보드를 사용하여 Screens 플레이어 활동 및 장치의 성능을 모니터링하고 문제를 해결할 수 있습니다. 이 페이지에서는 Screens 플레이어 및 지정된 장치에 대해 감지된 성능 문제를 모니터링하고 해결하는 방법에 대한 정보를 제공합니다.

## 장치 제어 센터에서 모니터링 및 문제 해결 {#monitor-and-troubleshoot-from-device-control-center}

활동을 모니터링하고 장치 대시보드를 사용하여 Screens 플레이어의 문제를 해결할 수 있습니다.

### 장치 대시보드 {#device-dashboard}

아래 절차에 따라 장치 대시보드로 이동합니다.

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 목록에는 아래 그림과 같이 할당되고 할당되지 않은 장치가 표시됩니다.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 장치(**NewTestDevice**)를 선택하고 작업 **표시줄에서** 대시보드를 클릭합니다.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 이 페이지에는 장치 정보, 활동 및 장치 활동 및 기능을 모니터링할 수 있는 장치 세부 사항이 표시됩니다.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 장치 활동 모니터링 {#monitor-device-activity}

[ **활동** ] 패널에는 타임스탬프가 있는 스크린 플레이어의 마지막 ping이 표시됩니다. 마지막 ping은 장치가 서버에 연결한 마지막 시간에 해당합니다.

![chlimage_1](assets/chlimage_1.png)

또한 **활동** 패널의 오른쪽 상단 모서리에서 로그 수집을 클릭하여 **플레이어의 로그를** 봅니다.

### 장치 세부 사항 업데이트 {#update-device-details}

장치 **IP** , 스토리지 사용량, 펌웨어 버전 및 디바이스 플레이어 가동 시간을 보려면 장치 세부 사항 패널을 확인하십시오.

![chlimage_1-1](assets/chlimage_1-1.png)

또한 캐시 **지우기** 및 **업데이트를** 클릭하여 디바이스의 캐시를 [지우고 이](screens-glossary.md) 패널에서 펌웨어버전을 각각 업데이트합니다.

**또한...를**&#x200B;클릭합니다.[장치 세부 사항] 패널의 오른쪽 **위** 모서리에서 플레이어를 다시 시작하거나 새로 고칩니다.

![chlimage_1-2](assets/chlimage_1-2.png)

### 장치 정보 업데이트 {#update-device-information}

구성 **업데이트, 장치 모델** , 장치 OS 및 셸 정보를 보려면 장치 정보 패널을 확인하십시오.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

또한 장치 정보 패널의 오른쪽 위 모서리에서 (**..**.)를 클릭하여 속성을 보거나 장치를 업데이트합니다.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

속성을 **클릭하여** 장치 **속성** 대화 상자를 표시합니다. 장치 제목을 편집하거나 구성 업데이트 옵션을 수동 또는 **자동으로 선택할** 수 **있습니다**.

>[!NOTE]
>
>장치의 자동 또는 수동 업데이트와 관련된 이벤트에 대한 자세한 내용은 채널 관리의 장치 ***대시보드에서 자동 및 수동*** 업데이트 섹션을 [참조하십시오](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 플레이어 스크린샷 보기 {#view-player-screenshot}

**PLAYER 스크린샷 **패널에서 장치에서 플레이어 스크린샷을 볼 수 있습니다.

플레이어 스크린샷 패널의 오른쪽 위 모서리에 있는 (**...**)을 클릭하고 **스크린샷 새로 고침 **을 선택하여 실행 중인 플레이어의 스냅샷을 봅니다.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 환경 설정 관리 {#manage-preferences}

[ **환경 설정** ] 패널에서는 사용자가 **장치의** Admin **UI**, **Channel Switcher** 및Remote Debugging에 대한 환경 설정을 변경할수 있습니다.

>[!NOTE]
>
>이 옵션에 대한 자세한 내용은 AEM Screens [플레이어를 참조하십시오](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

또한 오른쪽 **상단** 모서리에서 설정을 클릭하여 장치 환경 설정을 업데이트합니다. 다음 기본 설정을 업데이트할 수 있습니다.

* **서버 URL**
* **해상도**
* **재부팅 예약**
* **최대 아니오. 보관할 로그 파일**
* **로그 수준**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>다음 로그 수준 중 하나를 선택할 수 있습니다.
>
>* **사용 안함**
>* **디버그**
>* **정보**
>* **경고**
>* **오류**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGI 설정 문제 해결 {#troubleshoot-osgi-settings}

장치가 서버에 데이터를 게시할 수 있도록 하려면 빈 레퍼러를 활성화해야 합니다. 예를 들어 빈 레퍼러 속성이 비활성화된 경우 장치는 스크린샷을 다시 게시할 수 없습니다.

현재 이러한 기능 중 일부는 OSGI 구성에서 Apache *Sling Referrer 필터* [비어 있음]이 활성화된 경우에만 사용할 수 있습니다. 대시보드에 보안 설정이 이러한 기능 중 일부가 작동하지 않을 수 있다는 경고가 표시될 수 있습니다.

아래 절차에 따라 Apache Sling 레퍼러 필터 빈 허용

1. Adobe Experience **Manager 웹 콘솔**&#x200B;구성(즉,)으로 이동합니다 `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. **allow.empty **옵션을 선택합니다.
1. **저장**&#x200B;을 클릭합니다.

![chlimage_1-3](assets/chlimage_1-3.png)

### 추천 {#recommendations}

다음 섹션에서는 네트워크 링크, 서버 및 플레이어를 모니터링하여 상태를 파악하고 문제에 대응할 것을 권장합니다.

AEM에서는 다음을 위한 내장 모니터링을 제공합니다.

* *AEM Screens* 플레이어가 작동 중임을 나타내는 하트비트 5초마다.
* *플레이어에 현재 표시된 내용을 보여주는 플레이어의 스크린샷입니다* .
* 플레이어에 *설치된* AEM Screens 플레이어 펌웨어 버전.
* *플레이어에서 사용 가능한 저장소 공간* .

타사 소프트웨어를 사용한 원격 모니터링을 위한 권장 사항:

* 플레이어에 대한 CPU 사용량.
* AEM Screens 플레이어 프로세스가 실행 중인지 확인합니다.
* 플레이어의 원격 재시작/재부팅.
* 실시간 알림을 참조하십시오.

원격 로그인이 문제를 진단하고 플레이어를 다시 시작할 수 있도록 플레이어 하드웨어 및 OS를 배포하는 것이 좋습니다.

#### 추가 리소스 {#additional-resources}

채널에서 [재생되는 비디오를 디버그 및](troubleshoot-videos.md) 문제 해결하려면 비디오 재생 구성 및 문제 해결을 참조하십시오.