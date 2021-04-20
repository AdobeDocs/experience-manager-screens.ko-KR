---
title: AEM Screens의 음성 인식
description: 이 페이지에서는 AEM Screens의 음성 인식 기능에 대해 설명합니다.
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 3%

---


# AEM Screens {#voice-recognition}의 음성 인식

>[!IMPORTANT]
>
>**중요 개인 정보**
>
>음성 인식 기능을 사용하는 경우 해당 지역에 해당하는 모든 법적 및 윤리적 가이드라인을 따르십시오(플레이어가 음성 인식을 사용하고 있다는 것을 최종 사용자에게 가시적인 통지 제공 포함). Adobe Inc은 음성 관련 정보를 수신, 저장 또는 처리하지 않습니다. AEM Screens 플레이어는 검색 엔진에 내장된 표준 웹 음성 API를 사용합니다. 백그라운드에서 이 API는 음성을 텍스트로 변환하기 위해 Google의 서버에 음성 양식을 전송하며 이 텍스트는 구성된 키워드에 대해 플레이어에 의해 일치됩니다.
>
>자세한 내용은 [웹 음성 API](https://www.google.com/chrome/privacy/whitepaper.html#speech)의 Google 개인 정보 보호 백서를 참조하십시오.


음성 인식 기능을 사용하면 음성 인터랙션을 기반으로 AEM Screens 채널의 컨텐츠를 변경할 수 있습니다.

콘텐츠 작성자는 음성을 사용하도록 디스플레이를 구성할 수 있습니다. 이 기능의 목적은 고객이 자신의 디스플레이와 상호 작용하는 방법으로 음성을 활용할 수 있도록 하는 것입니다. 이와 유사한 사용 사례로는 상점에서 제품 추천 찾기, 식사 및 레스토랑에서 메뉴 항목 주문 등이 있습니다. 이 기능은 사용자의 액세스 가능성을 높이고 고객 경험을 대폭 향상시킬 수 있습니다.

>[!NOTE]
>플레이어 하드웨어는 마이크와 같은 음성 입력을 지원해야 합니다.

## 음성 인식 구현 {#implementing}

>[!IMPORTANT]
> 음성 인식 기능은 Chrome OS 및 Windows 플레이어에서만 사용할 수 있습니다.

AEM Screens 프로젝트에서 음성 인식을 구현하려면 디스플레이에 대한 음성 인식을 활성화하고 각 채널을 고유한 태그와 연결하여 채널 전환을 트리거해야 합니다.

다음 섹션에서는 AEM Screens 프로젝트에서 음성 인식 기능을 활성화하고 사용하는 방법에 대해 설명합니다.

## 전체 화면으로 컨텐츠 보기 또는 분할 화면 채널 스위치 {#sequence-channel}

음성 인식 기능을 사용하기 전에 프로젝트에 맞게 설정된 컨텐츠가 포함된 프로젝트와 채널이 있는지 확인합니다.

1. 다음 예에서는 아래 그림과 같이 **VoiceDemo** 및 3개의 시퀀스 채널 **Main**, **ColdDrinks** 및 **HotDrinks**&#x200B;이라는 데모 프로젝트를 보여줍니다.

   ![이미지](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >채널을 만들거나 채널에 컨텐츠를 추가하는 방법에 대해 알아보려면 [채널 만들기 및 관리](/help/user-guide/managing-channels.md)를 참조하십시오.

   또는,

   아래 그림에서와 같이 3개의 시퀀스 채널 **Main**, **ColdDrines** 및 **HotDrinks** 및 추가 1x2 분할 화면 채널 **SplitScreen**&#x200B;을 만들 수 있습니다.

   ![이미지](assets/voice-recognition/vr-emb-1.png)

1. 각 채널로 이동하고 컨텐츠를 추가합니다. 예를 들어 **VoiceDemo** —> **채널** —> **Main**&#x200B;으로 이동하여 채널을 선택합니다. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 열고 필요에 따라 내용(이미지/비디오)을 추가합니다. 마찬가지로 **ColdDrinks** 및 **HotDrinks** 채널 모두에 컨텐츠를 추가합니다.

   이제 채널에는 아래 그림과 같이 자산(이미지)이 포함됩니다.

   **기본**:

   ![이미지](assets/voice-recognition/vr-4.png)

   **콜드드음료**:

   ![이미지](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![이미지](assets/voice-recognition/vr-2.png)

   프로젝트에 화면 분할 채널을 추가한 경우 **SplitScreen**&#x200B;으로 이동하여 포함된 두 개의 시퀀스를 드래그하여 놓은 다음 아래 그림과 같이 **ColdDrinks** 및 **HotDrinks** 채널 모두에 경로를 추가합니다.
   ![이미지](assets/voice-recognition/vr-emb-6.png)


### 채널 {#setting-tags}에 대한 태그 설정

채널에 컨텐츠를 추가했으면 각 채널로 이동하고 음성 인식을 트리거하는 적절한 태그를 추가해야 합니다.

채널에 태그를 추가하려면 아래 절차를 따르십시오.

1. 각 채널로 이동하고 컨텐츠를 추가합니다. 예를 들어 **VoiceDemo** —> **채널** —> **Main**&#x200B;으로 이동하여 채널을 선택합니다.

1. 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![이미지](assets/voice-recognition/vr-5.png)

1. **기본 사항** 탭으로 이동하여 **태그** 필드에서 이미 기존 태그를 선택하거나 새 태그를 만듭니다.

   아래 그림과 같이 태그를 새 이름으로 입력하고 `return` 키를 눌러 새 태그를 만들 수 있습니다.

   ![이미지](assets/voice-recognition/vr-6.png)

   또는,

   또한 프로젝트에 대해 AEM 인스턴스에서 미리 태그를 만들고 선택할 수도 있습니다. [태그 만들기](#creating-tags)에 설명된 단계를 따르면 다음 그림과 같이 위치에서 태그를 선택하고 채널에 추가할 수 있습니다.

   ![이미지](assets/voice-recognition/vr-tag1.png)

1. 마찬가지로 **hot**&#x200B;이라는 이름의 태그를 **HotDrinks** 채널에 추가합니다.

1. 화면 분할 채널을 사용하는 경우 아래 그림과 같이 태그(**hot** 및 **cold**)를 모두 **SplitScreen** 채널 속성에 추가합니다.

   ![이미지](assets/voice-recognition/vr-emb-7.png)

1. 완료되면 **저장 및 닫기**&#x200B;를 클릭합니다.


### {#creating-tags} 태그 만들기

태그를 만들려면 아래 절차를 따르십시오.

1. AEM 인스턴스로 이동합니다.

1. 도구 아이콘 —> **태그 지정**을 클릭합니다.
   ![이미지](assets/voice-recognition/vr-7.png)

1. **만들기** —> **네임스페이스 만들기**를 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag3.png)

1. 프로젝트의 이름을 입력합니다(예: **VoiceDemo**). **만들기**&#x200B;를 클릭합니다.

1. **VoiceDemo** 프로젝트를 선택하고 작업 표시줄에서 **태그 만들기**를 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag4.png)

1. 태그 이름을 입력하고 **제출**을 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag5.png)

이제 AEM Screens 프로젝트에서 이러한 태그를 사용할 수 있습니다.

### 디스플레이에 채널 지정 및 음성 인식 활성화 {#channel-assignment}

1. 아래 그림과 같이 **위치** 폴더에 디스플레이를 만듭니다.

   ![이미지](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >디스플레이에 채널을 지정하는 방법에 대해 알아보려면 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)를 참조하십시오.

1. **LobbyDisplay** 채널에 **Main**, **ColdDrinks** 및 **HotDrinks** 채널을 할당합니다. 또한 프로젝트에 **SplitScreen** 채널을 사용하는 경우 해당 채널을 디스플레이에 지정해야 합니다.

   >[!NOTE]
   >분할 화면 채널을 만든 경우 디스플레이에 **SplitScreen** 채널을 지정합니다.

1. 채널을 할당하는 동안 다음 속성을 각 채널에 설정합니다.

   | **채널 이름** | **우선 순위** | **지원되는 이벤트** |
   |---|---|---|
   | 기본 | 2 | 초기 로드, 유휴 화면, 타이머 |
   | HotDrinks | 1 | 사용자 상호 작용 |
   | ColdDrinks | 1 | 사용자 상호 작용 |
   | 분할 화면 | 1 | 사용자 상호 작용 |

   >[!NOTE]
   >
   >디스플레이에 채널을 지정하는 방법에 대해 알아보려면 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)를 참조하십시오.

1. 디스플레이에 채널을 지정했으면 **LobbyDisplay**&#x200B;로 이동하여 디스플레이를 선택합니다. 작업 표시줄에서 **속성**&#x200B;을 선택합니다.

1. **표시** 탭으로 이동하여 **컨텐트**&#x200B;에서 **음성 사용** 옵션을 활성화합니다.

   ![이미지](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >디스플레이에서 음성 인식 기능을 활성화해야 합니다.

### Chrome Player에서 콘텐트 보기 {#viewing-content}

이전 단계가 완료되면 크롬 장치를 등록하여 출력을 볼 수 있습니다.

>[!NOTE]
>AEM Screens 플레이어에서 장치를 등록하는 방법을 알려면 [장치 등록](device-registration.md)을 참조하십시오.

**시퀀스 채널에 대해 원하는 출력**

**Main** 채널에서 내용을 재생하지만 *와 같은 키워드&#x200B;**핫**이(가) 포함된 단어를 사용할 때 채널에서&#x200B;**HotDrinks**채널의 내용을 재생하기 시작합니다.*

마찬가지로 *와 같은 키워드&#x200B;**cold**과 함께 단어를 사용하는 경우&#x200B;**ColdDrinks**채널의 내용을 재생하기 시작합니다.*

**분할 화면 채널에 대해 원하는 출력**

**Main** 채널에서 내용을 재생하고 있지만, **hot** 및 **cold**&#x200B;와 같은 키워드가 있는 단어를 함께 사용할 때 *핫 및 cold 음료*&#x200B;에 대한 메뉴를 볼 때 채널에서 **SplitScreen**&#x200B;의 내용을 재생하기 시작합니다. 채널. *뒤로 기본 메뉴*&#x200B;로 돌아가면 기본 채널로 다시 전환됩니다.





