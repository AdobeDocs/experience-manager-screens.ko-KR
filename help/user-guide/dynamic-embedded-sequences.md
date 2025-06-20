---
title: 동적 포함 시퀀스 사용
description: AEM Screens 프로젝트에서 동적 포함된 시퀀스를 구현하는 방법을 알아봅니다.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2451'
ht-degree: 1%

---

# 동적 포함 시퀀스 사용 {#using-dynamic-embedded-sequence}

동적 임베디드 시퀀스 사용 에서는 다음 주제를 다룹니다.

* **개요**
* **AEM Screens에서 동적 임베드된 경험 사용**
* **결과 보기**
* **사용자 제한 및 ACL 수정**

## 개요 {#overview}

***동적 포함 시퀀스***&#x200B;이(가) 부모-자식 계층 구조를 따르는 대규모 프로젝트에 대해 만들어집니다. 이 경우 자식 항목은 채널 폴더가 아닌 위치 폴더 내에서 참조됩니다. 사용자가 ***채널 역할***&#x200B;별 시퀀스를 채널 내에 포함할 수 있습니다. 이를 통해 사용자는 기본 채널 내에 임베드된 시퀀스를 사용하여 서로 다른 사무실에 대한 위치별 자리 표시자를 정의할 수 있습니다.

채널을 디스플레이에 할당할 때 디스플레이 경로를 지정할 수 있습니다. 또는 컨텍스트별로 실제 채널로 확인되는 채널의 역할을 지정할 수 있습니다.

동적 포함 시퀀스를 사용하려면 ***채널 역할***&#x200B;별로 채널을 할당합니다. 채널 역할은 디스플레이의 컨텍스트를 정의합니다. 역할은 다양한 작업을 대상으로 하며 역할을 수행하는 실제 채널과는 독립적입니다. 이 섹션에서는 역할별로 채널을 정의하는 사용 사례와 해당 콘텐츠를 글로벌 채널에 적용하는 방법에 대해 설명합니다. 또한 역할을 할당에 대한 식별자나 컨텍스트에서 채널에 대한 별칭으로 생각할 수 있습니다.

### 동적 임베디드 시퀀스 사용의 이점 {#benefits-of-using-dynamic-embedded-sequences}

채널 폴더 대신 위치 내에 시퀀스 채널을 배치하면 로컬 또는 지역 작성자가 시퀀스 채널과 관련된 콘텐츠를 편집할 수 있습니다. 또한 계층 구조 상단에 있는 채널 편집을 제한할 수 있습니다.

역할별 *채널*&#x200B;을(를) 참조하면 채널의 로컬 버전을 만들 수 있습니다. 이렇게 하면 위치별 콘텐츠를 동적으로 해결하고 위치별 채널에 콘텐츠를 사용하는 전역 채널을 만들 수도 있습니다.

>[!NOTE]
>
>**포함된 시퀀스 대 동적 포함된 시퀀스**
>
>Dynamic Embedded Sequence는 포함된 시퀀스와 유사하지만 한 채널에 대한 변경 사항 및 업데이트가 관련된 다른 채널에 전파되는 계층 구조를 따를 수 있습니다. 이 시퀀스는 상위-하위 계층 구조를 따르며 이미지나 비디오와 같은 에셋도 포함합니다.
>
>***포함된 동적 시퀀스***&#x200B;를 사용하면 위치별 콘텐츠를 표시할 수 있지만 ***포함된 시퀀스***&#x200B;는 콘텐츠의 일반 슬라이드 쇼만 표시합니다. 또한 동적 임베디드 시퀀스를 설정하는 동안 채널 역할과 이름을 사용하여 채널을 구성합니다. 실제 구현은 아래 단계를 참조하십시오.
>
>포함된 시퀀스를 구현하는 방법에 대한 자세한 내용은 AEM Screens에서 [포함된 시퀀스](embedded-sequences.md)을(를) 참조하십시오.

다음 예제에서는 다음 주요 용어에 초점을 맞춰 솔루션을 제공합니다.

* 전역 시퀀스에 대한 ***주 시퀀스 채널***&#x200B;입니다.
* ***동적 포함 시퀀스*** 구성 요소를 사용할 수 있습니다.
* **동적 포함 시퀀스 구성 요소의 *역할***과(와) 일치하는 디스플레이에 *역할*이(가) 있는 각 위치의 ***개별 시퀀스 채널***.

>[!NOTE]
>
>채널 할당에 대한 자세한 내용은 AEM Screens 설명서의 작성 섹션에서 **[채널 할당](channel-assignment.md)**&#x200B;을 참조하십시오.

## 동적 포함 시퀀스 사용 {#using-dynamic-embedded-sequence-2}

다음 섹션에서는 AEM Screens 채널에서 동적 포함된 시퀀스를 만드는 방법에 대해 설명합니다.

### 사전 요구 사항 {#prerequisites}

이 기능의 구현을 시작하기 전에 동적 포함 시퀀스 구현을 시작하기 위한 다음 사전 요구 사항이 준비되었는지 확인하십시오.

* AEM Screens 프로젝트를 만듭니다(이 예제에서는 **데모**).
* **채널** 폴더에 **전역** 채널을 만듭니다.
* **전역** 채널에 콘텐츠를 추가합니다(*관련 자산에 대한&#x200B;**Resources.zip**&#x200B;확인*).

다음 이미지는 **채널** 폴더에 **전역** 채널이 있는 **데모** 프로젝트를 보여 줍니다.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### 리소스 {#resources}

다음 리소스(이미지 및 에셋에 추가)를 다운로드하고 데모용 채널 콘텐츠로 추가로 사용할 수 있습니다.

[파일 가져오기](assets/resources.zip)

>[!NOTE]
>
>프로젝트를 만드는 방법 및 시퀀스 채널을 만드는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.
>
>* **[프로젝트 만들기 및 관리](creating-a-screens-project.md)**
>* **[채널 관리](managing-channels.md)**
>

AEM Screens 프로젝트에서 동적 임베디드 시퀀스를 구현하는 데에는 다음 세 가지 주요 작업이 포함됩니다.

1. **채널, 위치 및 디스플레이를 포함한 프로젝트 분류 설정**
1. **일정 만들기**
1. **각 디스플레이에 일정 할당**

아래 단계에 따라 기능을 구현하십시오.

>[!CAUTION]
>
>동적 포함 시퀀스를 구현하는 동안 각 위치에서 채널을 만드는 동안 **Name** 및 **Title** 필드를 주의하십시오. 명명법에 대한 지침을 주의 깊게 따르십시오.

1. **두 개의 위치 폴더를 만듭니다.**

   AEM Screens 프로젝트의 **위치** 폴더로 이동하고 **지역 A** 및 **지역 B**(으)로 두 개의 위치 폴더를 만듭니다.

   >[!NOTE]
   >
   >**지역 A** 위치 폴더를 만드는 동안 **Title**&#x200B;을(를) **지역 A**(으)로 입력해야 하며 **이름** 필드를 비워 둘 수 있으므로 자동으로 **지역 A** 이름이 선택됩니다.
   >
   >아래와 같이 위치 폴더 **지역 B**&#x200B;을 만드는 경우도 마찬가지입니다.

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >위치를 만드는 방법을 알아보려면 **[위치 만들기 및 관리](managing-locations.md)**&#x200B;를 참조하세요.

1. **각 위치 폴더 아래에 두 개의 위치와 채널을 만듭니다.**

   1. **데모** > **위치** > **지역 A**(으)로 이동합니다.
   1. **영역 A**&#x200B;을(를) 클릭하고 작업 표시줄에서 **+ 만들기**&#x200B;를 클릭합니다.
   1. **제목**&#x200B;을 **스토어 1**(으)로 사용하는 마법사에서 **위치**&#x200B;를 클릭합니다. 마찬가지로 마법사에서 **Title**&#x200B;을(를) **Store 2**(으)로 사용하여 **Store 2**(으)로 다른 위치를 만듭니다. **저장소 1** 및 **저장소 2**&#x200B;을(를) 만드는 동안 **이름** 필드를 비워 둘 수 있습니다.
   1. (b) 단계를 반복하고 이제 마법사에서 **시퀀스 채널**&#x200B;을 클릭합니다. 이 채널의 **Title**&#x200B;을(를) **지역 A**(으)로 입력하고 **이름**&#x200B;을(를) **지역**(으)로 입력하십시오.

   >[!CAUTION]
   >
   >**지역 A** 채널을 만드는 동안 **제목**&#x200B;을 **지역 A**(으)로 입력하고 **이름**&#x200B;을(를) **지역**(으)로 입력하십시오.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   마찬가지로 **지역 B**&#x200B;에 **스토어 3** 및 **스토어 4**(으)로 제목이 지정된 두 위치를 만드십시오. 또한 **Title**&#x200B;을(를) **Region B**(으)로 사용하고 **Name**&#x200B;을(를) **Region**(으)로 사용하여 **시퀀스 채널**&#x200B;을 만듭니다.

   >[!CAUTION]
   >
   >**지역 A** 및 **지역 B**&#x200B;에서 만든 채널에 대해 **지역**&#x200B;과 동일한 이름을 사용할 수 있는지 확인하십시오.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **각 위치에 디스플레이 및 채널을 만듭니다.**

   1. **데모** > **위치** > **지역 A** > **스토어 1**&#x200B;로 이동합니다.
   1. 작업 표시줄에서 **저장소 1**&#x200B;을(를) 클릭하고 **+ 만들기**&#x200B;를 클릭합니다.
   1. 마법사에서 **표시**&#x200B;를 클릭하고 **`Store1Display`**&#x200B;을(를) 만듭니다.
   1. (b) 단계를 반복하고 이번에는 마법사에서 **시퀀스 채널**&#x200B;을 클릭합니다. **제목**&#x200B;을(를) **`Store1Channel`**(으)로 입력하고 **이름**&#x200B;을(를) **스토어**(으)로 입력합니다.

   >[!CAUTION]
   >
   >시퀀스 채널을 만드는 경우 채널의 **제목**&#x200B;이(가) 요구 사항으로 설정될 수 있지만 **이름**&#x200B;은(는) 모든 로컬 채널에서 동일해야 합니다.
   >이 예제에서 **지역 A** 및 **지역 B** 아래의 채널은 **지역**(으)로 **이름**&#x200B;을 공유하고 **`Store 1`**, **`Store 2`**, **`Store 3`** 및 **`Store 4`** 아래의 채널은 **스토어**(으)로 **이름**&#x200B;을 공유합니다.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   마찬가지로 **`Store2Display`**(으)로 표시를 만들고 **`Store `2**(이름: **store**) 아래에 **`Store2Channel`** 채널을 만드십시오.

   >[!NOTE]
   >**`Store 1`** 및 **`Store 2`**&#x200B;에서 만든 채널에 대해 **스토어**&#x200B;와 동일한 이름을 사용할 수 있는지 확인하십시오.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   채널을 만들고 **지역 B**&#x200B;의 **`Store 3`** 및 **`Store 4`**&#x200B;에 표시할 수 있도록 이전 단계를 따르십시오. **`Store3Channel`** 및 **`Store4Channel`** 채널을 만드는 동안 **스토어**&#x200B;와(과) 동일한 **이름**&#x200B;을(를) 사용하는지 확인하십시오.

   다음 이미지는 **`Store 3`**&#x200B;의 디스플레이 및 채널을 보여 줍니다.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   다음 이미지는 **`Store 4`**&#x200B;의 디스플레이 및 채널을 보여 줍니다.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **각 위치의 채널에 콘텐츠를 추가합니다.**

   **데모** > **위치** > **지역 A** > **지역 A**(으)로 이동한 다음 작업 표시줄에서 **편집**&#x200B;을 클릭합니다. 채널에 추가하려는 자산을 드래그 앤 드롭합니다.

   >[!NOTE]
   >위의 **리소스** 섹션의 ***Resources.zip*** 파일을 사용하여 이미지를 채널 콘텐츠의 자산으로 사용할 수 있습니다.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   마찬가지로 **데모** > **위치** > **지역 B** > **지역 B**(으)로 이동한 다음 작업 표시줄에서 **편집**&#x200B;을 클릭하여 자산을 채널로 드래그 앤 드롭합니다.

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   다음 채널에 컨텐츠를 추가할 수 있도록 이전 단계 및 리소스를 따릅니다.

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **일정 만들기**

   AEM Screens 프로젝트의 **일정** 폴더로 이동하여 클릭합니다. 작업 표시줄에서 **만들기**&#x200B;를 클릭합니다.

   다음 이미지는 **데모** 프로젝트에서 만든 **AdSchedule**&#x200B;을 보여 줍니다.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **일정에 채널 할당**

   1. **데모** > **일정** > **Ad일정**(으)로 이동한 다음 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.
   1. **할당된 채널** 패널에서 **+ 채널 할당**&#x200B;을 클릭하면 **채널 할당** 대화 상자를 열 수 있습니다.
   1. 경로별로 **참조 채널**&#x200B;을 클릭하세요.
   1. **데모** > ***채널*** > ***전역***&#x200B;과(와) 마찬가지로 **채널 경로**&#x200B;을(를) 클릭합니다.
   1. **GlobalAdSegment**&#x200B;과(와) 마찬가지로 **채널 역할**&#x200B;을(를) 입력하십시오.
   1. **초기 로드**, **유휴 화면** 및 **사용자 상호 작용**&#x200B;과 같이 **지원되는 이벤트**&#x200B;를 클릭합니다.
   1. **저장**&#x200B;을 클릭합니다.

   **지역에 대해 역할별 채널 할당:**

   1. **할당된 채널** 패널에서 **+ 채널 할당**&#x200B;을 클릭합니다.
   1. 채널 할당 대화 상자에서 이름별로 **참조 채널**&#x200B;을 클릭합니다.
   1. **채널 이름**&#x200B;을(를) **지역***(으)로 입력하십시오.
   1. **채널 역할**&#x200B;을(를) **RegionAdSegment**(으)로 입력하십시오.
   1. **저장**&#x200B;을 클릭합니다.

   **역할별로 저장소 채널 할당:**

   1. **할당된 채널** 패널에서 **+ 채널 할당**&#x200B;을 클릭합니다.
   1. 채널 할당 대화 상자에서 이름별로 **참조 채널**&#x200B;을 클릭합니다.
   1. **채널 이름**&#x200B;을(를) **스토어**(으)로 입력하십시오.
   1. **채널 역할**&#x200B;을(를) **StoreAdSegment**(으)로 입력하십시오.
   1. **저장**&#x200B;을 클릭합니다.

   다음 이미지는 경로 및 역할별로 할당된 채널을 보여줍니다.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **전역 채널에 동적 포함 시퀀스를 구성하는 중입니다.**

   **데모** 프로젝트에서 처음 만든 **전역** 채널로 이동합니다.

   작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   편집기에서 채널 편집기에서 두 개의 **동적 포함 시퀀스** 구성 요소를 끌어서 놓습니다.

   구성 요소 중 하나에서 속성을 열고 **채널 할당 역할**&#x200B;을(를) **RegionAdSegment**(으)로 입력하십시오.

   마찬가지로 다른 구성 요소를 클릭하고 속성을 열어 **채널 할당 역할**&#x200B;을(를) **StoreAdSegment**(으)로 입력하십시오.

   ![채널 표시4](assets/channeldisplay4.gif)

1. **각 디스플레이에 일정 할당**

   1. **데모** > **위치** > **지역 A** >**스토어 1** >**`Store1Display`**&#x200B;와 같이 각 표시로 이동합니다.
   1. 작업 표시줄에서 **대시보드**&#x200B;를 클릭합니다.
   1. 대시보드에서 **할당된 채널 및 일정** 패널에서 **..**&#x200B;을(를) 클릭한 다음 **+일정 할당**&#x200B;을 클릭합니다.
   1. 예약에 대한 경로를 클릭합니다(예: **데모** > **일정** > **AdSchedule**).
   1. **저장**&#x200B;을 클릭합니다.

## 결과 보기 {#viewing-the-results}

채널 및 표시에 대한 설정이 완료되면 AEM Screens Player를 실행하여 콘텐츠를 봅니다.

>[!NOTE]
>
>AEM Screens Player에 대해 알아보려면 다음 리소스를 참조하십시오.
>
>* [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/)
>* [AEM Screens 플레이어로 작업](working-with-screens-player.md)


다음 출력은 표시 경로에 따라 AEM Screens Player에서 채널 컨텐츠를 확인합니다.

**시나리오 1**:

표시 경로를 **데모** > **위치** > **지역 A** > **스토어** > **`Store1Display`**(으)로 할당하면 AEM Screens 플레이어에 다음 콘텐츠가 표시됩니다.

![채널 표시1](assets/channeldisplay1.gif)

**시나리오 1**:

표시 경로를 **데모** > **위치** > **지역 B** > **스토어 3** > **`Store3Display`**(으)로 할당하면 AEM Screens 플레이어에 다음 콘텐츠가 표시됩니다.

![채널 표시2](assets/channeldisplay2.gif)

## 사용자 제한 및 ACL 수정 {#restricting-users-and-modifying-the-acls}

계층 구조 상단에 있는 채널 편집이 제한되어 있는 동안 전역, 지역 또는 로컬 작성자를 만들어 관련 콘텐츠를 편집할 수 있습니다.

위치에 따라 콘텐츠에 대한 사용자의 액세스를 제한할 수 있도록 ACL을 편집합니다.

### 예제 사용 사례 {#example-use-case}

다음 예에서는 위의 데모 프로젝트에 대해 세 명의 사용자를 만들 수 있습니다.

권한은 각 그룹에 다음과 같이 지정됩니다.

**그룹**:

* **Global-Author**: **데모** 프로젝트의 모든 위치와 채널에 액세스할 수 있고 모든 읽기, 쓰기 및 편집 권한을 가진 사용자로 구성됩니다.

* **Region-Author**: **Region A** 및 **Region B**&#x200B;에 대한 읽기, 쓰기 및 편집 권한이 있는 사용자로 구성됩니다.

* **Store-Author**: **Store 1**, **Store 2**, **Store 3** 및 **Store 4**&#x200B;에 대한 읽기, 쓰기 및 편집 권한만 있는 사용자로 구성됩니다.

#### 사용자 그룹 생성, 사용자 및 ACL 설정 단계 {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>ACL을 사용하여 각 개인 또는 팀이 고유한 프로젝트를 처리하도록 프로젝트를 분리하는 방법에 대한 자세한 내용은 **ACL 설정**&#x200B;을 참조하십시오.

그룹, 사용자를 만들고 권한에 따라 ACL을 수정하려면 아래 단계를 따르십시오.

1. **그룹 만들기**

   1. **Adobe Experience Manager**(으)로 이동합니다.
   1. **도구** > **보안** > **그룹**&#x200B;을 클릭합니다.
   1. **그룹 만들기**&#x200B;를 클릭하고 **ID**&#x200B;에 **Global-Author**&#x200B;을(를) 입력하십시오.
   1. **저장 및 닫기**&#x200B;를 클릭합니다.

   마찬가지로 **Region-Author** 및 **Store-Author**&#x200B;와 같은 두 개의 다른 그룹을 만드십시오.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **사용자 만들기 및 그룹에 사용자 추가**

   1. **Adobe Experience Manager**(으)로 이동합니다.
   1. **도구** > **보안** > **사용자**&#x200B;를 클릭합니다.
   1. **사용자 만들기**&#x200B;를 클릭한 다음 **ID**&#x200B;에서 **전역 사용자**&#x200B;를 입력하십시오.
   1. **암호**&#x200B;를 입력하고 이 사용자의 암호를 확인하십시오.
   1. **그룹** 탭을 클릭하고 **그룹 클릭**&#x200B;에 그룹 이름을 입력합니다. 예를 들어 **전역 작성자**&#x200B;를 입력하여 **전역 사용자**&#x200B;를 해당 그룹에 추가합니다.
   1. **저장 및 닫기**&#x200B;를 클릭합니다.

   마찬가지로 **Region-User** 및 **Store-User**&#x200B;과 같은 다른 사용자를 만들고 각각 **Region-Author** 및 **Store-Author**&#x200B;에 추가하십시오.

   >[!NOTE]
   >가장 좋은 방법은 그룹에 사용자를 추가한 다음 각 특정 사용자 그룹에 권한을 할당하는 것입니다.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **기여자에게 모든 그룹 추가**

   1. **Adobe Experience Manager**(으)로 이동합니다.
   1. **도구** > **보안** > **그룹**&#x200B;을 클릭합니다.
   1. 목록에서 **참가자**&#x200B;를 클릭하고 **구성원** 탭을 클릭합니다.
   1. 기여자에게 **Global-Author**, **Region-Author,** 및 **Store-Author**&#x200B;와 같은 **Group**&#x200B;을(를) 클릭하십시오.
   1. **저장 및 닫기**&#x200B;를 클릭합니다.

1. **각 그룹의 사용 권한에 액세스**

   1. *사용자 관리자*(으)로 이동하고 이 UI를 사용하여 다른 그룹에 대한 권한을 수정합니다.
   1. 아래 그림과 같이 **글로벌 작성자**&#x200B;를 검색하고 **권한** 탭을 클릭합니다.
   1. 마찬가지로 **Region-Author** 및 **Store-Author**&#x200B;에 대한 사용 권한에 액세스할 수 있습니다.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **각 그룹에 대한 권한 수정**

   **글로벌 작성자용:**

   1. **권한** 탭으로 이동
   1. ***/content/screens/demo***(으)로 이동하여 모든 권한을 확인하십시오.
   1. ***/content/screens/demo/locations***(으)로 이동하여 모든 권한을 확인하십시오.
   1. ***/content/screens/demo/locations/region-a***(으)로 이동하여 모든 권한을 확인하십시오. 마찬가지로 **`region-b`**&#x200B;에 대한 권한을 확인하십시오.

   단계를 이해하려면 다음 그림을 참조하십시오.
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   다음은 **Global-User**&#x200B;이(가) **Global 채널**&#x200B;에 액세스할 수 있음을 보여 줍니다. **스토어 1**, **스토어 2**, **스토어 3**, **스토어 4** 등 4개 스토어를 모두 사용하여 **지역 A** 및 **지역 B**&#x200B;에 액세스할 수 있습니다.

   ![전역](assets/global.gif)

   **지역 작성자용:**

   1. **권한** 탭으로 이동합니다.
   1. ***/content/screens/demo***(으)로 이동하여 **읽기** 권한만 확인합니다.
   1. ***/content/screens/demo/locations***(으)로 이동하여 **읽기** 권한만 확인합니다.
   1. ***/content/screens/demo/channels***(으)로 이동하고 **전역** 채널에 대한 권한을 선택 취소합니다.
   1. ***/content/screens/demo/locations***/***region-a***(으)로 이동하여 모든 권한을 확인하십시오. 마찬가지로 **`region-b`**&#x200B;에 대한 권한을 확인하십시오.

   단계를 이해할 수 있도록 다음 이미지를 참조하십시오.

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   다음은 지역 사용자가 **지역 A** 및 **지역 B**&#x200B;에 모두 액세스할 수 있음을 보여 줍니다. 그리고 네 개의 스토어, 즉 **스토어 1**, **스토어 2**, **스토어 3** 및 **스토어 4**&#x200B;에 모두 액세스하지만 **전역** 채널에는 액세스하지 않습니다.

   ![지역](assets/region.gif)

   **스토어 작성자용:**

   1. **권한** 탭으로 이동합니다.
   1. ***/content/screens/demo***(으)로 이동하여 **읽기** 권한만 확인합니다.
   1. ***/content/screens/demo/locations***(으)로 이동하여 **읽기** 권한만 확인합니다.
   1. ***/content/screens/demo/channels***(으)로 이동하고 **전역** 채널에 대한 권한을 선택 취소합니다.
   1. ***/content/screens/demo/locations/region-a***(으)로 이동하여 **읽기** 권한만 확인합니다. 마찬가지로 **`region-b`**&#x200B;에 대한 **읽기** 권한만 확인하십시오.
   1. ***/content/screens/demo/locations***/***region-a /store-1***(으)로 이동하여 모든 권한을 확인하십시오. 마찬가지로 **store-2, store-3,** 및 **store-4**&#x200B;에 대한 권한을 확인하십시오.

   단계를 이해할 수 있도록 다음 이미지를 참조하십시오.

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   다음은 **Store-User**&#x200B;이(가) **Store 1**, **Store 2**, **Store 3** 및 **Store 4**&#x200B;에만 액세스할 수 있음을 보여 줍니다. 그러나 **전역** 또는 지역(**지역 A** 및 **지역 B**) 채널에 액세스할 수 있는 권한이 없습니다.

   ![스토어](assets/store.gif)

>[!NOTE]
>
>권한 설정에 대한 자세한 내용은 [ACL 설정](setting-up-acls.md)을 참조하세요.
