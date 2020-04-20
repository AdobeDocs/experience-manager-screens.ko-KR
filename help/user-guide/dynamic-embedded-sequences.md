---
title: 동적 포함된 시퀀스 사용
seo-title: 동적 포함된 시퀀스 사용
description: AEM Screens 프로젝트에서 동적 포함된 시퀀스를 구현하는 방법을 알려면 이 페이지를 따르십시오.
seo-description: AEM Screens 프로젝트에서 동적 포함된 시퀀스를 구현하는 방법을 알려면 이 페이지를 따르십시오.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: b39c76fc7af4fb46596d4a995fe011d00b212d7c

---


# 동적 포함된 시퀀스 사용 {#using-dynamic-embedded-sequence}

동적 포함된 시퀀스 사용에 대한 내용은 다음과 같습니다.

* **개요**
* **AEM Screens에서 동적 포함된 경험 사용**
* **결과 보기**
* **사용자 제한 및 ACL 수정**

## 개요 {#overview}

***동적 포함된*** 시퀀스는 상위 하위 계층 구조를 따르는 대규모 프로젝트에 대해 만듭니다. 이 경우 하위 폴더는 채널 폴더가 아니라 위치 폴더 내에서 참조됩니다. It allows the user to embed a sequence inside a channel by ***Channel Role***. 사용자는 기본 채널 내에 포함된 시퀀스를 사용하여 서로 다른 사무실에 대한 위치별 자리 표시자를 정의할 수 있습니다.

디스플레이에 채널을 지정하는 동안 디스플레이의 경로를 지정하거나 컨텍스트별로 실제 채널로 해결할 채널의 역할을 지정할 수 있습니다.

동적 포함된 시퀀스를 사용하려면 채널 역할별로 채널을 ***지정합니다***. 채널 역할은 표시 컨텍스트를 정의합니다. 역할은 다양한 동작에 의해 타깃팅되며 역할을 수행하는 실제 채널과 독립적입니다. 이 섹션에서는 역할별로 채널을 정의하는 사용 사례와 해당 컨텐츠를 글로벌 채널에 활용할 수 있는 방법에 대해 설명합니다. 역할을 할당에 대한 식별자로 생각할 수도 있고, 의 컨텍스트에서 채널에 대한 별칭으로 생각할 수도 있습니다.

### 동적 포함된 시퀀스 사용의 이점 {#benefits-of-using-dynamic-embedded-sequences}

채널 폴더 대신 시퀀스 채널을 위치 내에 배치할 때 얻을 수 있는 주요 이점은 로컬 또는 지역 작성자가 계층 구조의 상위 채널에서 편집할 수 없도록 제한하면서 해당 채널과 관련된 컨텐츠를 편집할 수 있다는 것입니다.

Referencing a *Channel By Role*, allows you to create local version of a channel, in order to dynamically resolve location-specific content and also allows you to create a global channel that leverages the content for the location-specific channels.

>[!NOTE]
>
>**포함된 시퀀스 및 동적 포함된 시퀀스**
>
>동적 포함된 시퀀스는 포함된 시퀀스와 유사하지만 사용자가 한 채널에 대한 변경 사항/업데이트가 관련된 다른 채널에 전파되는 계층을 따를 수 있습니다. 상위-하위 계층 구조를 따르며 이미지나 비디오와 같은 자산도 포함합니다.
>
>***동적 포함된 시퀀스*** 기능을 사용하면 위치별 컨텐츠를 표시할 수 있지만 ***포함된 시퀀스는*** 컨텐츠의 일반 슬라이드 쇼만 표시합니다. 또한 동적 포함된 시퀀스를 설정하는 동안 채널 역할 및 이름을 사용하여 채널을 구성해야 합니다. 실질적인 구현은 아래 단계를 참조하십시오.
>
>포함된 시퀀스 구현에 대한 자세한 내용은 AEM Screens [의 포함된 시퀀스를](embedded-sequences.md) 참조하십시오.

다음 예에서는 다음 주요 용어에 초점을 맞춰 솔루션을 제공합니다.

* 전역 시퀀스의 ***기본 시퀀스 채널***
* ***로컬에 사용자 정의 가능한 시퀀스의 각 부분에 대한 동적 포함된 시퀀스*** 구성 요소
* ***디스플레이에서*** 동적 포함된 시퀀스 구성 요소의 *역할과* 일치하는 역할을 **가진 개별 시퀀스 채널&#x200B;**.**

>[!NOTE]
>
>To learn more about channel assignment, see **[Channel Assignment](channel-assignment.md)**under Authoring section in AEM Screens documentation.

## 동적 포함된 시퀀스 사용 {#using-dynamic-embedded-sequence-2}

다음 섹션에서는 AEM Screens 채널에서 동적 포함된 시퀀스 생성에 대해 설명합니다.

### 전제 조건 {#prerequisites}

이 기능을 구현하기 전에 동적 포함된 시퀀스 구현을 시작할 수 있는 다음 사전 요구 사항을 준비하십시오.

* AEM Screens 프로젝트 만들기(이 예에서는 **데모**)

* 채널 폴더 아래에 **글로벌** 채널 **만들기**

* 글로벌 채널에 컨텐츠 **추가** (*관련&#x200B;**자산은**Resources.zip을*&#x200B;확인하십시오)

다음 이미지는 채널 **폴더에 글로벌** 채널이 있는 **데모** 프로젝트를 **보여줍니다** .
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### 리소스 {#resources}

다음 리소스(이미지 및 자산에 추가)를 다운로드하고 데모용 채널 컨텐츠로 추가로 사용할 수 있습니다.

[파일 가져오기](assets/resources.zip)

>[!NOTE]
>
>프로젝트를 만드는 방법과 시퀀스 채널을 만드는 방법에 대한 자세한 내용은 아래 리소스를 참조하십시오.
>
>* **[프로젝트 만들기 및 관리](creating-a-screens-project.md)**
>* **[채널 관리](managing-channels.md)**
>



AEM Screens 프로젝트에서 동적 포함된 시퀀스 구현에는 다음 세 가지 주요 작업이 포함됩니다.

1. **채널, 위치 및 표시를 포함한 프로젝트 분류 설정**
1. **예약 생성**
1. **각 디스플레이에 예약 지정**

다음 단계에 따라 기능을 구현합니다.

>[!CAUTION]
>
>동적 포함된 시퀀스를 구현하는 동안 각 위치 아래에 **채널을** 만드는 **동안** 이름 및 제목 필드를주의하십시오. 명칭에 대한 지침을 주의 깊게 따르십시오.

1. **두 위치 폴더를 만듭니다.**

   AEM Screens **프로젝트에서 위치** 폴더로 이동하고 두 개의 위치 폴더를 영역 A와 영역 **B로** **만듭니다**.

   >[!NOTE]
   >
   >영역 A위치 폴더를 만드는 **동안** 제목을 **A로** 입력하면 **Name** 필드를 비워 두면 **** **** RegionA위치 이름이 자동으로 선택됩니다.
   >
   >다음과 같이 위치 폴더 영역 B **를**&#x200B;만드는 경우도 마찬가지입니다.

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >
   >위치를 만드는 방법에 대한 자세한 내용은 위치 **[만들기 및 관리를 참조하십시오](managing-locations.md)**.

1. **각 위치 폴더 아래에 두 개의 위치 및 채널을 만듭니다.**

   1. 데모 **—> 위치** —> **영역** A로 **이동합니다**.
   1. 영역 **A를** 선택하고 작업 표시줄에서 **+ 만들기를** 클릭합니다.
   1. 마법사에서 **위치** (제목)를 **스토어** **1로**&#x200B;선택합니다. 유사하게, Store 2라는 제목의 마법사에서 Title **을** Store **2****라는**&#x200B;다른 위치를만듭니다. Store 1 및 Store **2** 를 만드는 동안 이름 **필드를 비워** 둘 **수**&#x200B;있습니다.
   1. 단계(b)를 반복하고 이제 **마법사에서** 시퀀스 채널을 선택합니다. 이 채널에 **대해** **제목을** 영역 **A** 및이름을 **region **으로 입력합니다.
   >[!CAUTION]
   >
   >채널 영역 A를 **만드는**&#x200B;동안 **A로** 채널 **영역을** 입력하고 **NameArea** 를 RegionEither로 ****&#x200B;입력하십시오.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   마찬가지로, 영역 B 아래에 **스토어 3** 및 **스토어** 4라는 **두**&#x200B;위치를만듭니다. 또한 영역 B와 **** 같이 **제목을** **** 포함하는 시퀀스 **채널을** 만들고 **이름을**&#x200B;범위영역으로 만듭니다.

   >[!CAUTION]
   >
   >지역 A와 지역 B에서 만든 채널에 대해 동일한 이름을 사용할 **수** 있도록 **** **영역을**&#x200B;지정하십시오.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **각 위치에서 디스플레이 및 채널 만들기를 참조하십시오.**

   1. 데모 **—> 위치** —> **위치** 영역 **A** — **스토어** 1로이동합니다.
   1. 스토어 **1을** 선택하고 작업 **표시줄에서** + 만들기를 클릭합니다.
   1. 마법사에서 **표시를** 선택하고 Store1Display **를 만듭니다.**
   1. 단계(b)를 반복하고 이번에는 **마법사에서** 시퀀스 채널을 선택합니다. 제목으로 **Store** 1Channel **을** 입력하고 **이름을** Store ****&#x200B;로입력합니다.
   >[!CAUTION]
   >
   >시퀀스 채널을 만들 때는 **채널의 제목을** 요구 사항으로 지정할 수 있지만 **이름은** 모든 로컬 채널에서 동일해야 합니다.
   >
   >이 예에서는 A와 B **** 라는 ******아래에** 있는 **동일한** A **및 B******&#x200B;영역 및 1 **채널 아래Store 1**&#x200B;영역, Store 2, Store 2 **, Store 3, Store 3 및 Store ShareStoreStore 같은** 채널 및 BStore과 동일한Store **** ****&#x200B;을 브랜드에 있는 채널들이 있습니다.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   마찬가지로 Store2Display로 **표시하고** Store **2** 에서 **채널 Store** 2Channel **을**&#x200B;만듭니다(이름이storeDisplay로 표시됨).

   >[!NOTE]
   >
   >Store 1 및 Store 2에서 만든 채널과 동일한 이름을 **스토어로** 사용할 **수** ****&#x200B;있는지확인하십시오.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   위의 단계에 따라 채널을 만들고 영역 B 아래에 **있는 스토어 3** 및 **스토어 4** 에 **표시할**&#x200B;수있습니다. 다시 한 번, Store3Channel을 **만들** 때 **Store** 와 **Store** 4Channel을 **각각** 만들 때 동일한 이름을저장하도록 하십시오.

   다음 이미지는 스토어 3의 디스플레이 및 채널을 **보여줍니다**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   다음 이미지는 Store 4의 디스플레이 및 채널을 **보여줍니다**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **각 위치의 채널에 컨텐츠를 추가합니다.**

   데모 위치 **->** 위치 **A** -> **영역** A **> 클릭 영역** A와 클릭Edit 작업 표시줄에서 Edit **** 로 이동합니다. 채널에 추가할 자산을 드래그하여 놓습니다.

   >[!NOTE]
   >
   >위의 리소스 ***섹션에서 Resources.zip*** 파일을 사용하여 **이미지를** 채널 컨텐츠의 자산으로 사용할 수 있습니다.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   마찬가지로 **데모** -> **위치** -> **영역 B ->** 영역 B **와 클릭 작업 표시줄에서 편집** **** 및 삭제 동작으로 이동하여 아래 표시된 대로 자산을 채널에 끌어 놓습니다.

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   다음 채널에 컨텐츠를 추가하려면 위의 단계 및 리소스를 따르십시오.

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **예약 만들기**

   AEM Screens **프로젝트에서** 예약 폴더를 찾아 선택하고 작업 **표시줄에서 만들기를 클릭하여** 새 일정을 만듭니다.

   다음 이미지는 데모 **프로젝트에서 만든** AdSchedule을 **보여줍니다** .

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **일정에 채널 지정**

   1. 데모 **—> 일정** —> **광고** 예약 **대시보드로 이동하고 작업** 표시줄에서 **** 대시보드를 클릭합니다.
   1. 지정된 채널에서 **+ 채널** **할당** 패널을 클릭하여 채널 **할당** 대화상자를엽니다.
   1. Select **Reference Channel**.. by path.
   1. 채널 경로를 **데모** —> **채널** —> ***글로벌*** ***으로***&#x200B;선택합니다.
   1. Enter the **Channel Role** as **GlobalAdSegment**.
   1. 지원되는 **이벤트를 초기 로드** , **유휴**&#x200B;화면 **,**&#x200B;사용자 상호 작용 및 **사용자 상호 작용으로**&#x200B;선택합니다.
   1. **저장**&#x200B;을 클릭합니다.
   **영역에 대한 역할별 채널 지정:**

   1. 지정된 채널에서 **+ 채널** **할당** 패널을 클릭하여 채널 **할당** 대화상자를엽니다.
   1. 참조 **채널**&#x200B;선택... 이름 기준.
   1. 채널 **이름을** **영역으로**&#x200B;입력합니다.*
   1. Enter the **Channel Role** as **RegionAdSegment**.
   1. **저장**&#x200B;을 클릭합니다.
   **스토어에 대한 역할별 채널 지정:**

   1. 지정된 채널에서 **+ 채널** **할당** 패널을 클릭하여 채널 **할당** 대화상자를엽니다.
   1. 참조 **채널**&#x200B;선택... 이름 기준.
   1. 채널 **이름을** **스토어로**&#x200B;입력합니다.
   1. Enter the **Channel Role** as **StoreAdSegment**.
   1. **저장**&#x200B;을 클릭합니다.
   다음 이미지는 경로 및 역할별로 지정된 채널을 보여줍니다.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **전역 채널에 동적 포함된 시퀀스 구성을 참조하십시오.**

   먼저 Demo **프로젝트에서 만든 글로벌** 채널로 **이동합니다** .

   Click **Edit** from the action to open the editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   채널 편집기에서 두 개의 **동적 포함된 시퀀스** 구성 요소를 드래그하여 놓습니다.

   구성 요소 중 하나에서 속성을 열고 채널 지정 **역할을** RegionAdSegment로 **입력합니다**.

   마찬가지로, 다른 구성 요소를 선택하고 속성을 열어 채널 지정 **역할을** StoreAdSegment로 **입력합니다**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **각 디스플레이에 스케줄 지정**

   1. 데모 **—>** 위치 **—>** 위치 **—>** A **—>Store 1****—>** Store1Display각 표시로 이동합니다.
   1. Click **Dashboard** from the action to open the display dashboard.
   1. 클릭 **중...** 지정된 **채널 및 예약** 패널에서 을 클릭하고 **+예약 할당을 클릭합니다**.
   1. 예약 경로를 선택합니다(예: 여기, 데모 **—> 일정** **—>** AdSchedule ****).
   1. **저장**&#x200B;을 클릭합니다.

## 결과 보기 {#viewing-the-results}

채널 설정 및 전체 표시가 완료되면 AEM Screens 플레이어를 실행하여 컨텐츠를 보십시오.

>[!NOTE]
>
>AEM Screen Player에 대한 자세한 내용은 다음 리소스를 참조하십시오.
>
>* [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/)
>* [AEM Screens 플레이어 작업](working-with-screens-player.md)



다음 출력은 디스플레이 경로에 따라 AEM Screens 플레이어의 채널 컨텐츠를 확인합니다.

**시나리오 1**:

표시 경로를 데모 **—>** 위치 **—>** 영역 **—>** 영역 **—> 스토어 1** 을 **지정하는 경우 스토어 1**&#x200B;디스플레이에 있는 컨텐츠가 AEM Screens 플레이어에 표시됩니다.

![channeldisplay1](assets/channeldisplay1.gif)

**시나리오 1**:

표시 경로를 데모 **—>** 위치 **—>** 영역 **—>** 영역 **—> 스토어 3** B **** Store 3DisplayFollowing 컨텐츠가 AEM Screens 플레이어에 표시됩니다.

![channeldisplay2](assets/channeldisplay2.gif)

## 사용자 제한 및 ACL 수정 {#restricting-users-and-modifying-the-acls}

계층 구조에서 상위 채널의 편집에서 제한되지만 글로벌, 지역 또는 로컬 작성자가 관련 컨텐츠를 편집할 수 있습니다.

사용자가 위치에 따라 컨텐츠에 대한 액세스를 제한하려면 ACL을 수정해야 합니다.

### 사용 사례 예 {#example-use-case}

다음 예에서는 위의 데모 프로젝트에 대해 세 명의 사용자를 만들 수 있습니다.

권한은 다음과 같습니다.

**그룹**:

* **글로벌 작성자**:데모 프로젝트의 모든 위치 및 채널에 액세스할 수 있고 모든 **읽기,** 쓰기 및 편집 권한을 가진 사용자로 구성됩니다.

* **지역 작성자**:영역 A 및 영역 B에 대한 읽기, 쓰기 및 편집 권한이 **있는** 사용자로 **구성됩니다**.

* **스토어 작성자**:Store 1, Store 2, **Store 3**, **Store** 4 **및 Store** 4 **에 대한 읽기, 쓰기 및 편집 권한을 가진 사용자로**&#x200B;구성됩니다.

#### 사용자 그룹, 사용자 및 ACL 설정 단계 {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>개별 또는 팀이 프로젝트를 처리하도록 ACL을 사용하여 프로젝트를 분리하는 방법에 대해 자세히 알아보려면 ACL **설정을 참조하십시오**.

아래 절차에 따라 권한을 기준으로 그룹, 사용자 및 ACL을 수정합니다.

1. **그룹 만들기**

   1. Adobe Experience **Manager로 이동합니다**.
   1. 도구 **—> 보안** **—> 그룹을** **클릭합니다**.
   1. 그룹 **만들기를** 클릭하고 **ID에 글로벌** 작성자를 **입력합니다**.
   1. Click **Save &amp; Close**.
   마찬가지로, 지역 작성자 및 **스토어** 작성자와 같은 다른 두 개의 그룹을 **만듭니다**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **사용자 만들기 및 그룹에 사용자 추가**

   1. Adobe Experience **Manager로 이동합니다**.
   1. 도구 **—> 보안** —> **사용자** 를 **클릭합니다**.
   1. 사용자 **만들기를** 클릭하고 **ID에 전역** 사용자를 **입력합니다**.
   1. 암호를 **입력하고** 이 사용자의 암호를 확인합니다.
   1. 그룹 **탭을 클릭하고** 그룹 **선택**&#x200B;에 그룹 이름을 입력합니다 **. 예를 들어,** 글로벌 작성자를 **입력하여 해당** 그룹에 글로벌사용자를추가합니다.
   1. Click **Save &amp; Close**.
   마찬가지로, 지역-사용자 및 **스토어** 사용자와 같은 **다른 사용자를** 만들고 **해당 사용자를** 지역 작성자 **및 스토어-작성자** 각각두 명의 다른 사용자를 만듭니다.

   >[!NOTE]
   >
   >그룹의 사용자를 추가한 다음 각 특정 사용자 그룹에 권한을 할당하는 것이 좋습니다.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **모든 그룹을 작성자에게 추가**

   1. Adobe Experience **Manager로 이동합니다**.
   1. 도구 **—> 보안** **—> 그룹을** **클릭합니다**.
   1. 목록에서 **기여자를** 선택하고 멤버 **탭을** 선택합니다.
   1. 글로벌 **작성자** , **지역**&#x200B;작성자 **및** 스토어-작성자와 작성자와 같은 **그룹을** 선택합니다.
   1. Click **Save &amp; Close**.

1. **각 그룹에 대한 권한 액세스**

   1. 사용자 관리자로 *이동하고* 이 UI를 사용하여 다른 그룹에 대한 권한을 수정합니다.
   1. 글로벌 **작성자를** 검색하고 **권한** 탭을 클릭합니다(아래 그림 참조).
   1. 마찬가지로, 지역 작성자 및 **스토어 작성자에 대한** 권한에 **액세스할 수 있습니다**.
   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **각 그룹에 대한 권한 수정**

   **글로벌 작성자의 경우:**

   1. Navigate to the **Permissions** tab
   1. /content/screens/demo ***로*** 이동하고 모든 권한을 확인합니다.
   1. /content/screens/demo/locations ***로*** 이동하고 모든 권한을 확인합니다.
   1. /content/screens/demo/locations/region-a로 ***이동하여*** 모든 권한을 확인합니다. 마찬가지로 **region-b**&#x200B;권한을 확인합니다.
   단계를 이해하려면 아래 그림을 참조하십시오.
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   다음 이미지는 **이제** Channel **에 액세스할 수 있는 권한을 가지며,** All **및 All** With Global Store, Store 2 Global Store, Store 3 Store 및 Store 4 Global StoreStoreStore 3 Store 및 Store 4 Store를 모두 표시하는 Channel **** ****************&#x200B;및 Store 4를 표시합니다.

   ![글로벌](assets/global.gif)

   **지역 작성자:**

   1. Navigate to the **Permissions** tab.
   1. /content/screens/demo로 ***이동하고 읽기*** 권한만 **확인합니다** .
   1. /content/screens/demo/locations ***로*** 이동하고 읽기 **권한만 확인합니다** .
   1. /content/screens/demo/channels ***로*** 이동하고 글로벌 채널에 대한 권한을 **선택 취소합니다** .
   1. /content/screens/demo/locations ***/*** region-a로&#x200B;****** 이동하여 모든 권한을 확인합니다. 마찬가지로 **region-b**&#x200B;권한을 확인합니다.
   단계를 이해하려면 아래 그림을 참조하십시오.

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   다음 이미지는 현재 Region이 **Region에 액세스할 수 있다는** 것과 B에 **액세스할 수** 있는 **4개의**&#x200B;스토어, All Store 1 **, Store 3, Store 3, Store 4**&#x200B;에 대한 4개의 스토어, 즉 Vertisal Store 및 Store4 **는 Global Channel****** **** 에 액세스할 수 없지만 Region에 액세스할 수 있다는 것을 보여줍니다.

   ![region](assets/region.gif)

   **스토어 작성자:**

   1. Navigate to the **Permissions** tab.
   1. /content/screens/demo로 ***이동하고 읽기*** 권한만 **확인합니다** .
   1. /content/screens/demo/locations ***로*** 이동하고 읽기 **권한만 확인합니다** .
   1. /content/screens/demo/channels ***로*** 이동하고 글로벌 채널에 대한 권한을 **선택 취소합니다** .
   1. /content/screens/demo/locations/region-a로 ***이동하고*** 읽기 **권한만 확인합니다** . 마찬가지로 **region-b** 에 대한 읽기 **권한만 확인합니다**.
   1. /content/screens/demo/locations ***/*** region-a /store-1 ****** 로 이동하여 모든 권한을 확인합니다. 마찬가지로 **store-2, store-3,** 및 **store-4**&#x200B;권한을 확인합니다.
   단계를 이해하려면 아래 그림을 참조하십시오.

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   다음 이미지는 **이제** User가 **The** 2 ****, 3, Store 3, And 4Store에 **대한 액세스 권한만 가지지만, 즉 4개의 StoreStore**&#x200B;에 대한 네 개의 Store는 Also AccessStore **** ******** ****&#x200B;에 액세스할 수 없지만, Also Access to access to the permissions (Access A A A A Global Store and B RegionVertisionAlityAlegeArea) Alege AlegeAlityAlity는 Aleas AlityAlityAlsoAlityArea).

   ![스토어](assets/store.gif)

>[!NOTE]
>
>권한 설정에 대한 자세한 내용은 ACL [설정을 참조하십시오](setting-up-acls.md).

