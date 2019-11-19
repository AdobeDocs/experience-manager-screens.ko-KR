---
title: 포함된 시퀀스
seo-title: 포함된 시퀀스
description: 이 페이지에 따라 사용자가 상위 채널에서 구성 요소를 추가하고 다른 채널의 컨텐츠를 다시 사용하고 이를 상위 채널에 포함할 수 있도록 해주는 채널용의 포함된 시퀀스에 대해 알아보십시오.
seo-description: 이 페이지에 따라 사용자가 상위 채널에서 구성 요소를 추가하고 다른 채널의 컨텐츠를 다시 사용하고 이를 상위 채널에 포함할 수 있도록 해주는 채널용의 포함된 시퀀스에 대해 알아보십시오.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 포함된 시퀀스 {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## 포함된 시퀀스 추가 {#adding-embedded-sequences}

다음 구성 요소를 시퀀스 채널에 추가할 수 있습니다.

* 포함된 시퀀스
* 동적 포함된 시퀀스

>[!NOTE]
>
>스크린 프로젝트에서 다른 구성 요소를 사용하는 방법에 대해 알려면 [채널에 구성 요소 추가](adding-components-to-a-channel.md)를 참조하십시오.

### 포함된 시퀀스 추가 {#adding-an-embedded-sequence}

포함된 시퀀스를 채널에 추가할 수 있습니다. 포함된 시퀀스는 이미지나 비디오와 같은 에셋을 포함하는 다른 채널입니다. 포함된 시퀀스를 추가하면 사용자가 ***채널 경로별로 채널에 시퀀스를 추가할 수 있습니다***.

>[!NOTE]
>
>***채널 경로 ***채널에 대한 명시적 참조를 정의합니다.
>
>*채널 경로*&#x200B;에 대해 자세히 알려면 스크린 작성에서 [채널 지정](channel-assignment.md)을 참조하십시오.

아래 절차에 따라 채널에 포함된 시퀀스를 추가하십시오.

1. 페이지를 포함할 채널을 선택합니다. For example, **We.Retail In-Store** --&gt; **Channels** --&gt;** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 왼쪽 사이드바에서 구성 요소 아이콘을 클릭하여 포함된 페이지를 추가합니다. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. 채널의 **채널 경로**&#x200B;를 선택합니다.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. 사용자가 지속 기간을 지정하는 경우, 하위 시퀀스는 지정된 시각에 중단됩니다(즉, 컷오프).

1. 부분 무료 **재생 전략을** **정상으로**&#x200B;설정합니다.

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!NOTE]
>
>**중요 사항:**
>
>포함된 시퀀스에 사용된 채널을 동일한 디스플레이에 지정해야 합니다.
>
>이전 단계에서 채널에 포함된 시퀀스를 추가한 후 아래 절차를 따르십시오.
>
>1. 디스플레이로 이동하고 위치 폴더에서 디스플레이를 **선택합니다** .
>1. 작업 **표시줄에서** 대시보드를 클릭하여 표시 대시보드로 이동합니다.
>1. 지정된 채널 및 예약된 **패널에서** + 채널 **지정을 선택하여** 채널 **할당 대화**&#x200B;상자를엽니다.
   >
   >
1. 채널 경로에서 (포함된 시퀀스에 사용됨)에 있는 채널의 경로를 **선택합니다**.
>1. 우선 순위가 **기본** 채널보다 낮아야 합니다.
   >
   >
1. 지원되는 이벤트를 선택하지 **마십시오**.
>1. 완료되면 **저장을** 클릭합니다.
>



다음 예에서는 포함된 시퀀스(**유휴 채널 - 야간**)를 이미 존재하는 채널(**유휴 채널**)에 추가하는 것을 보여줍니다.

![new2](assets/new2.gif)

### 동적 포함된 시퀀스 추가 {#adding-a-dynamic-embedded-sequence}

동적 포함된 시퀀스를 채널에 추가할 수 있습니다. 동적 포함된 시퀀스는 포함된 시퀀스와 유사하지만 동적 포함된 시퀀스를 사용하면 하나의 채널에 수행된 변경/업데이트 사항이 관련된 다른 하나의 채널에 전파되는 계층 구조를 사용자가 따를 수 있습니다. 상위-하위 계층 구조를 따르며 이미지나 비디오와 같은 자산도 포함합니다. 동적 시퀀스를 추가하면 사용자가 채널 역할별로 채널을 추가할 수 있습니다.

>[!NOTE]
>
>***채널 역할***&#x200B;은 디스플레이 컨텍스트를 정의합니다.
>
>*채널 역할*&#x200B;에 대해 자세히 알려면 스크린 작성에서 [채널 지정](channel-assignment.md)을 참조하십시오.

아래 절차에 따라 채널에 포함된 시퀀스를 추가하십시오.

1. 동적 시퀀스를 포함할 채널을 선택합니다. For example, **We.Retail In-Store** --&gt; **Channels** --&gt; **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 왼쪽 사이드바에서 구성 요소 아이콘을 클릭하여 동적 포함된 시퀀스를 추가합니다. 다이내믹&#x200B;****** 내장 시퀀스 **를 편집기로 드래그하여 놓습니다.

1. Double-click the **Dynamic** **Embedded Sequence **component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. 부분 무료 **재생 전략을** **정상으로**&#x200B;설정합니다. By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![latest](assets/latest.gif)

