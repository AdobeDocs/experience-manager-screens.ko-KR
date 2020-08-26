---
title: AEM Screens 음성 인식
description: 이 페이지에서는 AEM Screens의 음성 인식 기능에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: b7d7d4ec200d3eb7cd7bac4253c8664e5bd4de81
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---


# AEM Screens 음성 인식 {#voice-recognition}

>[중요 사항]
>**중요 개인 정보**
>음성 인식 기능을 사용하는 경우 해당 지역에 적용되는 모든 법적 및 윤리적 가이드라인을 따릅니다(플레이어가 음성 인식을 사용하고 있다는 것을 최종 사용자에게 가시적 통지하는 것을 포괄적으로 포함). Adobe Inc, 음성 관련 정보를 수신하거나 저장 또는 처리하지 않습니다. AEM Screens 플레이어는 검색 엔진에 내장된 표준 웹 음성 API를 사용합니다. 비하인드 스토리에서는 음성을 텍스트로 변환하기 위해 Google의 서버로 음성 양식이 전송되며 이 텍스트는 구성된 키워드에 대해 플레이어와 일치합니다.
>
>자세한 내용은 [웹 음성 API의 Google 개인 정보 보호 백서를](https://www.google.com/chrome/privacy/whitepaper.html#speech) 참조하십시오.


## 개요 {#overview}

음성 인식 기능을 사용하면 음성 인터랙션을 기반으로 AEM Screens 채널에서 컨텐츠를 변경할 수 있습니다.

콘텐츠 작성자는 음성을 사용하도록 디스플레이를 구성할 수 있습니다. 이 기능의 목적은 고객이 음성을 디스플레이와 상호 작용하는 방법으로 활용할 수 있도록 하는 것입니다. 이와 유사한 활용 사례로는 상점에서 제품 추천 찾기, 식사 및 레스토랑에서 메뉴 항목 주문 등이 있습니다. 이 기능은 사용자에게 접근성을 높여주며 고객 경험을 크게 향상시킬 수 있습니다.


>[!NOTE]
>플레이어 하드웨어는 마이크와 같은 음성 입력을 지원해야 합니다.

>[!IMPORTANT]
> 음성 인식 기능은 크롬 및 전자 플레이어에서만 사용할 수 있습니다.

## 음성 인식 구현 {#implementing}


AEM Screens 프로젝트에서 음성 인식을 구현하려면 디스플레이에 대한 음성 인식을 활성화하고 각 채널을 고유한 태그와 연결하여 채널 전환을 트리거해야 합니다.

다음 섹션에서는 AEM Screens 프로젝트에서 음성 인식 기능을 활성화하고 사용하는 방법에 대해 설명합니다.

### 프로젝트 설정 {#setting-up}

음성 인식 기능을 사용하기 전에 프로젝트에 맞게 설정된 컨텐츠가 포함된 프로젝트와 채널이 있는지 확인하십시오.

1. 다음 예에서는 아래 그림에 표시된 것처럼 **VoiceDemo** 및 세 개의 시퀀스 채널 **Main**, **ColdDraw**&#x200B;및 **** HotDrages라는 데모 프로젝트를 소개합니다.

   ![이미지](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >채널을 만들거나 채널에 컨텐츠를 추가하는 방법에 대해 알아보려면 채널 만들기 및 [관리를 참조하십시오](/help/user-guide/managing-channels.md)

1. 각 채널로 이동하고 컨텐츠를 추가합니다. 예를 들어 **VoiceDemo** —> **채널** —> **기본** 으로이동하여채널을 선택합니다. 작업 표시줄에서 **편집을** 클릭하여 편집기를 열고 요구 사항에 따라 컨텐츠(이미지/비디오)를 추가합니다. 마찬가지로 **ColdDrinks** 및 **HotDrinks** 채널에 컨텐츠를 추가할 수 있습니다.

   이제 채널에는 아래 그림과 같이 자산(이미지)이 포함됩니다.

   **기본**:

   ![이미지](assets/voice-recognition/vr-4.png)

   **콜드드음료**:

   ![이미지](assets/voice-recognition/vr-3.png)

   **뜨거운 음료**:

   ![이미지](assets/voice-recognition/vr-2.png)

### 채널에 대한 태그 설정 {#setting-tags}

채널에 컨텐츠를 추가한 후에는 각 채널로 이동하고 음성 인식을 트리거하는 적절한 태그를 추가해야 합니다.

채널에 태그를 추가하려면 아래 절차를 따르십시오.

1. 각 채널로 이동하고 컨텐츠를 추가합니다. 예를 들어 **VoiceDemo** —> **채널** —> **기본** 으로이동하여채널을 선택합니다.

1. Click **Properties** from the action bar.

   ![이미지](assets/voice-recognition/vr-5.png)

1. 기본 **탭으로** 이동하여 태그 **필드에서 기존 태그를** 선택하거나 새 태그를 만듭니다.

   아래 그림과 같이 태그 및 히트 `return` 키에 새 이름을 입력하여 새 태그를 만들 수 있습니다.

   ![이미지](assets/voice-recognition/vr-6.png)

   또는,

   프로젝트에 대해 사전에 AEM 인스턴스에서 태그를 만들고 선택할 수도 있습니다. 태그 만들기에 설명된 단계를 [따라](#creating-tags)다음 그림과 같이 위치에서 태그를 선택하고 채널에 추가할 수 있습니다.

   ![이미지](assets/voice-recognition/vr-tag1.png)

1. 완료되면 **저장 및** 닫기를 클릭합니다.

마찬가지로, HotDrinks **채널에** 뜨거운 **으로** 명명된 태그를 추가합니다.

#### 태그 만들기 {#creating-tags}

태그를 만들려면 아래 절차를 따르십시오.

1. AEM 인스턴스로 이동합니다.
1. 도구 —> **태깅을 클릭합니다**.
   ![이미지](assets/voice-recognition/vr-7.png)
1. 만들기 **—> 네임스페이스** 만들기를 클릭합니다 ****.
   ![이미지](assets/voice-recognition/vr-7.png)
1. 프로젝트의 이름을 입력합니다. 예: **VoiceDemo** 를 클릭하고 만들기를 클릭합니다.
1. VoiceDemo **프로젝트를** 선택하고 작업 **모음에서 태그** 만들기를 클릭합니다.
1. 제출을 **클릭합니다**.


### 디스플레이에 채널 지정 및 음성 인식 활성화 {#channel-assignment}

1. 아래 그림과 같이 **위치** 폴더에 디스플레이를 만듭니다.

   ![이미지](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >디스플레이에 채널을 지정하는 방법에 대해 알아보려면 디스플레이 [만들기 및 관리를 참조하십시오](/help/user-guide/managing-displays.md).

1. 채널을 **Main**, **ColdDrinks**&#x200B;및 **HotDrinks** 에 할당하고 **LobbyDisplayYou를**&#x200B;통해

1. 채널을 할당하는 동안 다음 속성을 각 채널에 설정합니다.

   | **채널 이름** | **우선 순위** | **지원되는 이벤트** |
   |---|---|---|
   | 기본 | 2 | 초기 로드, 유휴 화면, 타이머 |
   | HotDrinks | 1 | 사용자 상호 작용 |
   | 콜드음료 | 1 | 사용자 상호 작용 |

   >[!NOTE]
   >
   >디스플레이에 채널을 지정하는 방법에 대해 알아보려면 디스플레이 [만들기 및 관리를 참조하십시오](/help/user-guide/managing-displays.md).

1. 디스플레이에 채널을 지정했으면 **LobbyDisplay로** 이동하고 디스플레이를 선택합니다. 작업 **표시줄에서** 속성을 선택합니다.

1. 표시 **탭으로** 이동하고 **컨텐츠** 아래에서 **음성 사용**&#x200B;옵션을활성화합니다.

   ![이미지](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >디스플레이에서 음성 인식 기능을 활성화해야 합니다.

#### Chrome Player에서 콘텐트 보기 {#viewing-content}

이전 단계가 완료되면 크롬 장치를 등록하고 출력을 볼 수 있습니다.

>[!NOTE]
>AEM Screens 플레이어에서 [장치를 등록하는](device-registration.md) 방법은 장치 등록을 참조하십시오.

이 예에서는 Chrome Player에서 출력을 보여 줍니다.

![newimage](assets/voice-recognition/voice-video.gif)












