---
title: AEM Screens Player를 사용한 작업
description: AEM Screens 플레이어, 관리 UI 및 채널 전환기 작업에 대해 알아봅니다.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: 107e296237a98b7d69744b5ec4b87142d7de61cd
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# AEM Screens Player를 사용한 작업

AEM Screens 플레이어에서 채널 콘텐츠 및 기타 설정을 관리할 수 있습니다.

>[!NOTE]
>
>OS X AEM Screens 플레이어의 전체 화면 모드를 종료할 수 있도록 ***Ctrl+Cmd+F***&#x200B;를 누릅니다.

디스플레이에 채널을 할당하면 AEM Screens Player에 콘텐츠가 표시됩니다. 대시보드에서 관리 UI의 환경 설정을 사용하거나 플레이어 자체에서 플레이어의 설정을 구성할 수 있습니다.

## 장치 대시보드 사용 {#using-the-device-dashboard}

AEM 작성 인스턴스를 통해 액세스할 수 있는 장치 대시보드에서 장치에 대한 환경 설정을 구성할 수 있습니다.

1. 프로젝트에서 장치 대시보드로 이동합니다(예: ***프로젝트 테스트*** > ***장치***).

   작업 표시줄에서 **장치** 및 **장치 관리자**&#x200B;를 클릭합니다.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 장치 대시보드를 열 수 있도록 장치를 클릭합니다.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. **환경 설정** 패널을 확인하십시오. 이 두 가지 옵션에서 플레이어에 대한 **관리 UI** 및 **채널 전환기**&#x200B;를 활성화하거나 비활성화할 수 있습니다.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 관리자 UI {#the-admin-ui}

환경 설정 패널에서 **관리자 UI**&#x200B;를 활성화하면 사용자가 Screens 플레이어에서 관리자 설정을 열 수 있습니다. 또한 장치 대시보드에서 이 옵션을 비활성화하면 사용자가 플레이어에서 관리 UI를 열 수 없습니다.

Screens 플레이어에서 관리자 UI를 보려면 왼쪽 상단 모서리를 길게 눌러 터치 사용 AEM Screens 플레이어에서 또는 마우스를 사용하여 관리자 메뉴를 엽니다. 등록이 완료되고 채널이 로드된 후에 정보가 표시됩니다.

>[!NOTE]
>
>또한 AEM Screens Player 앱 가동 시간을 보고 앱 상태를 확인할 수도 있습니다.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 구성 메뉴 옵션 액세스 {#configuration-options}

아래 그림과 같이 측면 메뉴에서 **구성** 옵션을 클릭하면 구성을 업데이트할 수 있습니다.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

구성 메뉴를 사용하여 다음 설정을 수정할 수 있습니다.

* 이 대화 상자에서 **펌웨어**, **환경 설정** 또는 **팩토리로**&#x200B;을(를) 다시 설정합니다.

* AEM Screens 플레이어에 대해 보관할 최대 로그 파일 수를 **최대 번호로 지정하십시오.**&#x200B;을(를) 유지할 로그 파일의 수입니다.

* Screens 플레이어에 대해 **관리 메뉴**, **채널 전환기** 및 **활동 UI**&#x200B;를 활성화하거나 비활성화합니다.

  **구성** 메뉴에서 **활동 UI**&#x200B;을(를) 사용하도록 설정하면 AEM Screens 플레이어가 아래 그림과 같이 플레이어의 오른쪽 상단 모서리에 *플레이어 활동 알림*&#x200B;을 표시합니다.

  ![이미지](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>**펌웨어 업데이트** 옵션은 Android™ 플레이어와 같은 Cordova에서만 작동합니다.

>[!NOTE]
>
>프로덕션 배포에서는 **관리자 UI**&#x200B;을(를) 사용하지 않도록 설정하는 것이 좋습니다.

#### 콘텐츠 캐시 메뉴 옵션 액세스 {#content-cache-options}

AEM Screens Player의 관리 UI에서 채널 및 애플리케이션에 대한 캐시를 지울 수 있습니다.

캐시를 업데이트할 수 있도록 측면 레일에서 **콘텐츠 캐시**&#x200B;를 클릭하십시오.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 채널 전환기 {#the-channel-switcher}

환경 설정 패널에서 **채널 전환기**&#x200B;를 활성화하면 사용자가 Screens 플레이어에서 채널 선택 설정을 열 수 있습니다.

또한 장치 대시보드에서 이 옵션을 비활성화하면 사용자가 Screens 플레이어에서 채널 환경 설정을 제어할 수 없습니다.

Screens 플레이어에서 채널 설정을 전환하고 제어할 수 있습니다.

플레이어에서 채널 전환기를 보려면 왼쪽 아래 모서리를 길게 눌러 채널 및 기타 기능을 전환할 수 있는 채널 전환기를 엽니다.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Screens 플레이어에서 플레이어에 대한 관리 메뉴 및 채널 전환기를 활성화하거나 비활성화할 수도 있습니다.
>
>(아래 섹션에 설명된 대로 *Screens 플레이어에서 환경 설정 변경*&#x200B;을 참조하십시오.)

### AEM Screens 플레이어에서 환경 설정 관리

플레이어 자체에서 관리자 UI 및 채널 전환기에 대한 설정을 변경할 수도 있습니다.

플레이어에서 환경 설정을 변경하려면:

1. 유휴 채널의 왼쪽 상단 모서리를 길게 눌러 관리 패널을 엽니다.
1. 왼쪽 작업 메뉴에서 **구성**(으)로 이동합니다.
1. **관리자 UI** 또는 **채널 전환기**&#x200B;에 대한 구성을 활성화하거나 비활성화합니다.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens 플레이어 문제 해결

AEM Screens 플레이어(하드웨어 및 소프트웨어)와 관련된 다양한 문제를 해결할 수 있습니다.

| **문제** | **권장 사항** |
|---|---|
| 플레이어 저장소가 꽉 찼습니다. | 불필요한 파일 제거 |
| 플레이어 네트워크 손실 | Cat-5 또는 Cat-6 케이블을 사용합니다. Wifi의 경우 라우터에서 플레이어 장치까지의 거리를 줄입니다 |
| AEM Screens 플레이어 충돌 | AEM Screens 플레이어가 항상 실행되도록 하는 watchdog 앱을 사용하는 것이 좋습니다 |
| AEM Screens Player 설정 누락 | AEM 서버 연결 확인 |
| 플레이어 다시 시작 또는 재부팅 후 AEM Screens Player가 자동으로 시작되지 않음 | OS 시작 폴더 또는 초기화 절차 확인 |
| AEM Screens Player에 잘못되었거나 오래된 콘텐츠가 표시됨 | 네트워크 연결 확인 |

### AEM Screens 플레이어 업데이트

AEM Screens Player에 대한 업데이트에는 두 가지 유형이 있습니다.

| **메서드** | **세부 정보** | 원격 **방법** | **자동화** | **가동 중지 시간** |
|---|---|---|---|---|
| 펌웨어 업데이트 | 원격 명령을 통해 기존 설치된 플레이어에 적용됩니다. 업데이트 후 플레이어가 기존 콘텐츠로 자동 다시 로드됩니다. | 예 | 사용자 정의 | 거의 - 1~3초 |
| 플레이어 쉘 업데이트 | 플레이어에 배포되는 새 실행 파일입니다. 이 기능을 사용하려면 플레이어에서 새 바이너리를 원격으로 복사하고 현재 실행 중인 바이너리를 중지하고 새 버전을 시작해야 합니다. 패키지의 사전 로드를 다시 다운로드해야 할 수 있습니다. | 예(원격 셸의 방식으로) | 사용자 정의 | 아니요 |

## 플레이어 장치에 대한 하드웨어 선택 지침 {#hardware-selection-guidelines-for-player-device}

>[!NOTE]
>
>**사용되지 않음:** 이 하드웨어 선택 지침은 사용되지 않으며 새 배포에 사용해서는 안 됩니다. 하드웨어 사양 및 권장 사항은 특정 배포 요구 사항 및 사용 사례에 따라 자격을 갖춘 AV 통합자가 제공해야 합니다.

다음 섹션에서는 Screens 프로젝트에 대한 하드웨어 선택 지침을 제공합니다.

* PC 플레이어와 디스플레이 패널 또는 프로젝터 모두에 대해 항상 ***상업용*** 또는 ***산업용*** 등급 구성 요소를 공급하십시오.

* 항상 디지털 간판 시장을 제공하는 공급업체와 협력하십시오.
* 항상 주변 온도 및 상대 습도와 같은 환경 요인을 고려합니다.
* 항상 전원 요구 사항 및 전원 조절 상태를 검토하십시오.
* 애플리케이션에 필요한 성능 요구 사항과 I/O 포트를 주의 깊게 검토하십시오.

다음 표에는 AEM Screens 프로젝트에 대한 일반적인 사용 사례와 함께 하드웨어 구성이 요약되어 있습니다.

<table>
 <tbody>
  <tr>
   <td>플레이어 구성</td>
   <td>프로세서</td>
   <td>메모리</td>
   <td>스토리지 SSD</td>
   <td>GPU</td>
   <td>디스플레이</td>
   <td>I/O</td>
   <td>일반적인 사용 사례</td>
  </tr>
  <tr>
   <td>기본</td>
   <td>듀얼 코어, i3 또는 엔트리급 쿼드 코어 Intel® Atom 프로세서</td>
   <td><p>4GB 메모리</p> <p>2MB 캐시</p> </td>
   <td><p>*ChromeOS 32GB</p> <p>*Windows 128GB</p> </td>
   <td>온보드</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> 이더넷/무선<br /> 2xUSB</td>
   <td>
    <ul>
     <li>표준 전체 화면 루프<br /> </li>
     <li>시간대 지정</li>
    </ul> </td>
  </tr>
  <tr>
   <td>표준</td>
   <td>쿼드 코어, Intel® Core™ i5 프로세서</td>
   <td><p>8GB 메모리</p> <p>4MB 캐시</p> </td>
   <td>128GB</td>
   <td>온보드</td>
   <td>3840x2160(<code>4K</code>)</td>
   <td>DVI, HDMI<br /> 이더넷/무선,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>단일 Source 다이내믹 콘텐츠</li>
     <li>단순 대화형</li>
     <li>1-3 영역 레이아웃</li>
    </ul> </td>
  </tr>
  <tr>
   <td>고급</td>
   <td>쿼드 코어, 하이퍼스레딩, 인텔® 코어™ i7 프로세서</td>
   <td><p>16GB 메모리</p> <p>8MB 캐시</p> </td>
   <td>256GB</td>
   <td>전용 그래픽 GPU</td>
   <td>3840x2160(<code>4K</code>)</td>
   <td>DVI, HDMI<br /> 이더넷/무선,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4개 이상의 콘텐츠 영역, 동시 비디오 재생</li>
     <li>다중 페이지 인터랙티브</li>
     <li>다중 Source 데이터 트리거</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
