---
title: AEM Screens의 음성 인식
description: AEM Screens에서 음성 인식 및 사용 방법에 대해 자세히 알아보십시오.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 2%

---

# AEM Screens의 음성 인식 {#voice-recognition}

>[!IMPORTANT]
>
>**중요 개인 정보 정보**
>
>음성 인식 기능을 사용할 때는 해당 지역에 적용되는 모든 법적 및 윤리적 지침을 따르십시오. 이러한 지침에는 플레이어가 음성 인식을 사용하고 있다는 것을 최종 사용자에게 명확하게 알리는 작업이 포함되지만, 이에 국한되지 않습니다. Adobe은 음성 관련 정보를 수신, 저장 또는 처리하지 않습니다. AEM Screens 플레이어는 검색 엔진에 내장된 표준 웹 음성 API를 사용합니다. 백그라운드에서 이 API는 음성 변환 양식을 Google 서버로 전송하여 음성에서 텍스트로 변환합니다. 플레이어는 구성된 키워드에 대해 텍스트를 일치시킵니다.
>
>자세한 내용은 [웹 음성 API에 대한 Google 개인 정보 보호 백서](https://www.google.com/chrome/privacy/whitepaper.html#speech)를 참조하십시오.


음성 인식 기능을 사용하면 음성 상호 작용에 의해 AEM Screens 채널에서 콘텐츠를 변경할 수 있습니다.

콘텐츠 작성자는 음성이 활성화되도록 디스플레이를 구성할 수 있습니다. 이 기능의 목적은 고객이 디스플레이와 상호 작용하는 방법으로 음성을 사용할 수 있도록 하는 것입니다. 이와 유사한 사용 사례로는 매장에서 제품 추천을 받거나, 저녁 식사 및 레스토랑에서 메뉴 항목을 주문하는 것이 있습니다. 이 기능은 사용자의 접근성을 높이고 고객 경험을 크게 향상시킬 수 있습니다.

>[!NOTE]
>플레이어 하드웨어는 마이크로폰과 같은 음성 입력을 지원해야 한다.

## 음성 인식 구현 {#implementing}

>[!IMPORTANT]
> 음성 인식 기능은 Chrome OS 및 Windows 플레이어에서만 사용할 수 있습니다.

AEM Screens 프로젝트에서 음성 인식을 구현하려면 표시에 대해 음성 인식을 활성화하고 각 채널을 고유한 태그와 연결하여 채널 전환을 트리거합니다.

다음 섹션에서는 AEM Screens 프로젝트에서 음성 인식 기능을 활성화하고 사용하는 방법에 대해 설명합니다.

## 전체 화면 또는 분할 화면 채널 전환으로 컨텐츠 보기 {#sequence-channel}

음성 인식 기능을 사용하기 전에 프로젝트와 채널에 프로젝트에 대한 콘텐츠가 설정되어 있는지 확인하십시오.

1. 다음 예제에서는 아래 그림과 같이 이름이 **VoiceDemo**&#x200B;인 데모 프로젝트와 세 개의 시퀀스 채널 **Main**, **ColdDrinks** 및 **HotDrinks**&#x200B;을(를) 보여 줍니다.

   ![이미지](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >채널을 만들거나 채널에 콘텐츠를 추가하는 방법은 [채널 만들기 및 관리](/help/user-guide/managing-channels.md)를 참조하세요.

   또는,

   아래 그림과 같이 세 개의 시퀀스 채널 **Main**, **ColdDrinks** 및 **HotDrinks**&#x200B;을(를) 만들고 1x2 분할 Screens 채널 **SplitScreen**&#x200B;을 한 개 더 만들 수 있습니다.

   ![이미지](assets/voice-recognition/vr-emb-1.png)

1. 각 채널로 이동하고 콘텐츠를 추가합니다. 예를 들어 **VoiceDemo** > **채널** > **기본**(으)로 이동한 다음 채널을 클릭합니다. 작업 표시줄에서 **편집**&#x200B;을 클릭한 다음 요구 사항에 따라 콘텐츠(이미지/비디오)를 추가하십시오. 마찬가지로 **ColdDrinks**&#x200B;와(과) **HotDrinks** 채널 모두에 콘텐츠를 추가하십시오.

   이제 아래 그림과 같이 채널에는 에셋(이미지)이 포함됩니다.

   **주**:

   ![이미지](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![이미지](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![이미지](assets/voice-recognition/vr-2.png)

   Screens 분할 채널을 프로젝트에 추가한 경우 **SplitScreen**(으)로 이동하여 포함된 시퀀스 두 개를 드래그 앤 드롭합니다. 아래 그림과 같이 **ColdDrinks** 및 **HotDrinks** 채널에 경로를 추가합니다.
   ![이미지](assets/voice-recognition/vr-emb-6.png)


### 채널에 대한 태그 설정 {#setting-tags}

채널에 컨텐츠를 추가한 후 각 채널로 이동하여 음성 인식을 트리거할 적절한 태그를 추가합니다.

채널에 태그를 추가하려면 아래 단계를 따르십시오.

1. 각 채널로 이동하고 콘텐츠를 추가합니다. 예를 들어 **VoiceDemo** > **채널** > **기본**(으)로 이동한 다음 채널을 클릭합니다.

1. 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

   ![이미지](assets/voice-recognition/vr-5.png)

1. **기본 사항** 탭으로 이동한 다음 **태그** 필드에서 기존 태그를 클릭하거나 태그를 만듭니다.

   아래 그림과 같이 태그의 새 이름을 입력하여 태그를 만들고 `return` 키를 누를 수 있습니다.

   ![이미지](assets/voice-recognition/vr-6.png)

   또는,

   프로젝트에 대해 미리 AEM 인스턴스에서 태그를 만든 다음 선택할 수도 있습니다. [태그 만들기](#creating-tags)에 설명된 단계를 수행하면 아래 그림과 같이 위치에서 태그를 클릭하여 채널에 추가할 수 있습니다.

   ![이미지](assets/voice-recognition/vr-tag1.png)

1. 마찬가지로 제목이 **hot**&#x200B;인 태그를 **HotDrinks** 채널에 추가하십시오.

1. 분할 Screens 채널을 사용하는 경우 아래 그림과 같이 태그(**hot** 및 **cold**)를 **SplitScreen** 채널 속성에 모두 추가합니다.

   ![이미지](assets/voice-recognition/vr-emb-7.png)

1. 완료되면 **저장 및 닫기**&#x200B;를 클릭하십시오.


### 태그 만들기 {#creating-tags}

태그를 만들려면 아래 단계를 따르십시오.

1. AEM 인스턴스로 이동합니다.

1. 도구 아이콘 > **태그 지정**을 클릭합니다.
   ![이미지](assets/voice-recognition/vr-7.png)

1. **만들기** > **네임스페이스 만들기**를 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag3.png)

1. 프로젝트 이름(예: **VoiceDemo**)을 입력하고 **만들기**&#x200B;를 클릭합니다.

1. **VoiceDemo** 프로젝트를 클릭하고 작업 표시줄에서 **태그 만들기**를 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag4.png)

1. 태그 이름을 입력하고 **제출**을 클릭합니다.
   ![이미지](assets/voice-recognition/vr-tag5.png)

이제 AEM Screens 프로젝트에서 이러한 태그를 사용할 수 있습니다.

### 디스플레이에 채널 할당 및 음성 인식 활성화 {#channel-assignment}

1. 아래 그림과 같이 **위치** 폴더에 표시를 만듭니다.

   ![이미지](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >디스플레이에 채널을 할당하는 방법에 대한 자세한 내용은 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)를 참조하세요.

1. **LobbyDisplay**&#x200B;에 **Main**, **ColdDrinks** 및 **HotDrinks** 채널을 할당하십시오. 또한 프로젝트에 **SplitScreen** 채널을 사용하는 경우 디스플레이에 할당해야 합니다.

   >[!NOTE]
   >분할 화면 채널을 만든 경우 디스플레이에 **SplitScreen** 채널을 할당하십시오.

1. 채널을 할당하는 동안 각 채널에 다음 속성을 설정합니다.

   | **채널 이름** | **우선 순위** | **지원되는 이벤트** |
   |---|---|---|
   | 기본 | 2 | 초기 로드, 유휴 화면, 타이머 |
   | HotDrinks | 1 | 사용자 상호 작용 |
   | 콜드드드링크 | 1 | 사용자 상호 작용 |
   | SplitScreen | 1 | 사용자 상호 작용 |

   >[!NOTE]
   >
   >디스플레이에 채널을 할당하는 방법에 대한 자세한 내용은 [디스플레이 만들기 및 관리](/help/user-guide/managing-displays.md)를 참조하세요.

1. 디스플레이에 채널을 할당한 후 **LobbyDisplay**(으)로 이동하여 디스플레이를 클릭합니다. 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

1. **디스플레이** 탭으로 이동하여 **콘텐츠**&#x200B;에서 **음성 사용** 옵션을 활성화하십시오.

   ![이미지](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >디스플레이로부터 음성 인식 기능을 활성화하는 것은 필수적이다.

### Chrome 플레이어에서 컨텐츠 보기 {#viewing-content}

위의 단계가 완료되면 Chrome 장치를 등록하여 출력을 볼 수 있습니다.

>[!NOTE]
>[장치 등록](device-registration.md)을 참조하세요.

**시퀀스 채널에 대해 원하는 출력**

**Main** 채널이 콘텐츠를 재생하고 있습니다. 그러나 *뜨거운 음료를 마시고 싶습니다*&#x200B;와 같이 **hot** 키워드가 있는 단어를 사용하면 채널은 **HotDrinks** 채널의 콘텐츠를 재생합니다.

마찬가지로 *차가운 음료를 마시고 싶습니다*&#x200B;와 같이 **cold** 키워드가 있는 단어를 사용하는 경우 채널은 **ColdDrinks** 채널의 콘텐츠를 재생합니다.

**분할 Screens 채널에 대해 원하는 출력**

**Main** 채널이 콘텐츠를 재생하고 있습니다. 그러나 *뜨거운 음료와 차가운 음료에 대한 메뉴를 보고 싶습니다*&#x200B;와 같이 **뜨거운 음료**&#x200B;와 **차가운 음료**&#x200B;를 함께 사용하는 단어를 사용하면 채널은 **SplitScreen** 채널의 콘텐츠를 재생합니다. *주 메뉴로 돌아가기*&#x200B;를 지정하면 **주** 채널로 되돌아갑니다.
