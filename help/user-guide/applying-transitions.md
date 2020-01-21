---
title: 전환 적용
seo-title: 전환 적용
description: 화면 프로젝트에 전환을 적용하는 방법을 알아보려면 이 페이지를 따르십시오.
seo-description: 화면 프로젝트에 전환을 적용하는 방법을 알아보려면 이 페이지를 따르십시오.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 389a44e3f6175e0a43a6e99edd3048f2b8455d0b

---


# 전환 적용 {#applying-transitions}

이 섹션에서는 채널의 여러 자산( **이미지 및 비디오** )과 포함된 시퀀스 사이에 전환 구성 요소를 적용할 수 있는 방법에 대해 설명합니다.


>[!CAUTION]
>
>전환 구성 요소의 속성에 대해 자세히 알아보려면 **전환을** 참조하십시오 [](adding-components-to-a-channel.md#transition).

## 채널의 자산에 전환 구성 요소 추가 {#adding-transition}

아래 절차에 따라 전환 구성 요소를 AEM Screens 프로젝트에 추가하십시오.

>[!NOTE]
>
>**전제 조건**
> 채널 TestTransition을 **사용하여 AEM Screens 프로젝트** TestProject를 **만듭니다**. 또한 위치 및 디스플레이를 설정하여 출력을 봅니다.

1. 채널 TestTransition으로 **이동하고** 작업 **표시줄에서 편집을** 클릭합니다.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >TestTransition **채널에** 이미 자산(이미지 및 비디오)이 거의 없습니다. 예를 들어 TestTransition **채널에는** 다음과 같이 세 개의 이미지와 두 개의 비디오가 포함되어 있습니다.

   ![image2](assets/transitions2.png)


1. 전환 **구성 요소를** 편집기에 드래그하여 놓습니다.
   >[!CAUTION]
   >
   >채널의 자산에 전환을 추가하기 전에 순차적 채널의 첫 번째 자산 앞에 전환을 추가하지 않아야 합니다. 채널의 첫 번째 항목은 전환이 아닌 자산이어야 합니다.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >기본적으로 유형(Type)과 같은 전환 구성 요소의 속성은 **페이드** (Fade) **로** 설정되며 **지속 시간** (Duration)은 *1600ms*&#x200B;로설정됩니다.  또한 적용되는 자산보다 긴 전환 기간을 설정하는 것은 바람직하지 않습니다.

1. 또한 이 채널 편집기에 **포함된 시퀀스** 구성 요소(시퀀스 채널 포함)를 추가하는 경우 아래 그림과 같이 컨텐츠가 순서대로 재생되도록 끝 부분에 전환 구성 요소를 추가할 수 있습니다.

   ![image3](assets/transitions5.png)

