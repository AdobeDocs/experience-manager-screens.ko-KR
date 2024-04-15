---
title: 전환 적용
description: AEM Screens 프로젝트에 전환을 적용하는 방법을 알아봅니다.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 전환 적용 {#applying-transitions}

이 섹션에서는 **전환** 구성 요소가 서로 다른 에셋(이미지 및 비디오) 사이에 있고 채널에 임베드된 시퀀스가 있습니다.

>[!CAUTION]
>
>의 속성에 대해 자세히 알아보려면 **전환** 구성 요소, 참조 [전환](adding-components-to-a-channel.md#transition).

## 채널의 에셋에 전환 구성 요소 추가 {#adding-transition}

AEM Screens 프로젝트에 전환 구성 요소를 추가하려면 아래 단계를 따르십시오.

>[!NOTE]
>
>**전제 조건**
>
>AEM Screens 프로젝트 만들기 **테스트 프로젝트** 채널 포함 **테스트 전환**. 또한 출력을 볼 위치 및 디스플레이를 설정합니다.

1. 채널로 이동 **테스트 전환** 및 선택 **편집** 작업 표시줄에서

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >다음 **테스트 전환** 채널에 이미 에셋(이미지 및 비디오)이 거의 없습니다. 예를 들어 **테스트 전환** 채널에는 아래에 표시된 대로 세 개의 이미지와 두 개의 비디오가 포함됩니다.

   ![image2](assets/transitions2.png)


1. 을(를) 끌어다 놓습니다. **전환** 구성 요소를 편집기에 추가합니다.

   >[!CAUTION]
   >
   >채널의 에셋에 전환을 추가하기 전에 순차적 채널의 첫 번째 에셋 앞에 전환을 추가하지 마십시오. 채널의 첫 번째 항목은 전환이 아닌 자산이어야 합니다.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >기본적으로 다음과 같은 전환 구성 요소의 속성이 **유형** 이(가) (으)로 설정됨 **페이드** 및 **기간** 이(가) (으)로 설정됨 *1600밀리초*. 또한 적용 중인 에셋보다 긴 전환 지속 시간을 설정하는 것은 바람직하지 않습니다.

1. 또한 다음을 추가하는 경우 **포함된 시퀀스** 구성 요소(시퀀스 채널 포함)는 이 채널 편집기에 추가할 수 있으며 끝에 전환 구성 요소를 추가할 수 있습니다. 이렇게 하면 다음 이미지에 표시된 대로 컨텐츠가 올바른 순서로 재생됩니다.

   ![image3](assets/transitions5.png)
