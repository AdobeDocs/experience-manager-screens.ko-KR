---
title: AEM Screens의 응용 표현물
description: 이 페이지에서는 AEM Screens의 응용 표현물에 대한 아키텍처 개요 및 구성에 대해 설명합니다.
index: false
source-git-commit: 3ced907f4611ff7499ca4c013c4b25e1315e3726
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 2%

---


# 응용 표현물: 아키텍처 개요 및 구성 {#adaptive-renditions}

## 소개 {#introduction}

응용 변환을 사용하여 장치는 고객이 정의한 규칙에 따라 장치에 대해 가장 적합한 변환을 자동으로 선택할 수 있습니다. 장치는 이러한 규칙에 따라 자산의 가장 적절한 렌디션을 자동으로 다운로드 및 재생하므로 고객은 *main* 환경을 디자인하는 데에만 집중할 수 있습니다.

## 목표 {#objective}

이제 AEM Screens 개발자로서, 모든 컨텐츠 변형을 수동으로 만들지 않고도 자동으로 다운로드 및 재생되도록 장치별 자산 변환을 구성할 수 있습니다. 컨텐츠 작성자가 AEM Screens 채널에서 이 기능을 사용할 수 있으려면 먼저 적응형 표현물을 구성해야 합니다.

## 아키텍처 개요 {#architectural-overview}

응용 표현물은 특정 이름 지정 규칙에 따라 이름이 지정된 여러 자산 표현물을 갖는 아이디어를 기반으로 합니다. 특정 변환을 재생하는 결정은 예상 기능이 있는 장치에서만 확인할 수 있는 미디어 쿼리 표현식을 평가하여 수행됩니다.

연결된 변환 이름 지정 패턴을 갖는 기능은 아래 그림과 같이 세로 또는 가로와 같은 변환 매핑 규칙을 정의합니다. 사용 가능한 모든 표현식을 계산하면 Screens 플레이어에서 일치하는 규칙에 해당하는 이름 지정 패턴을 수집합니다. 패턴은 변환 이름에서 패턴을 찾아 시퀀스 재생 중에 올바른 변환을 찾는 데 사용됩니다.

![이미지](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 스크린 프로젝트에 변환 매핑 속성 추가 {#rendition-mapping-new}

응용 표현물 기능을 활성화하려면 다음 매핑 규칙이 있어야 하며, 채널 및 디스플레이에 대해 컨텍스트 인식(CA) 구성을 확인할 수 있어야 합니다.

>[!NOTE]
>내용 인식 구성에 대한 자세한 내용은 여기 [여기](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)를 참조하십시오.

아래 절차에 따라 설정을 구성하십시오.

1. **CRXDE Lite**&#x200B;로 이동합니다. 아래 그림과 같이 **rendition-mapping** 구성이 `/conf/screens/sling:configs/rendition-mapping`에 있는지 확인합니다.

   >![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >최신 기능 팩 202109을 설치한 경우 CRXDE Lite에 **렌디션-매핑** 노드 구조가 미리 채워진 상태로 표시됩니다. `/conf/screens/sling:configs/rendition-mapping` 최신 기능 팩에 대한 자세한 내용은 [기능 팩 202109](/help/user-guide/release-notes-fp-202109.md)에 대한 릴리스 노트 를 참조하십시오.
   >기존 프로젝트의 경우 Screens 프로젝트에 **rendition-mapping** 구성이 연결되어 있는지 확인합니다. 자세한 내용은 [기존 프로젝트에 변환 매핑 추가](#rendition-mapping-existing) 섹션을 참조하십시오.

### 기존 프로젝트에 변환 매핑 속성 추가 {#rendition-mapping-existing}

1. **CRXDE Lite**&#x200B;로 이동합니다.

1. 아래 그림과 같이 `/conf/screens`을 가리키는 `sling:configRef` 속성을 프로젝트 컨텐츠 노드에 추가하여 변환 매핑 연결을 명시적으로 정의합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 작성자 및 게시 설정 {#setup-author-publish}

응용 표현물을 사용하기 전에 작성자 및 게시에서 다음 권장 사항을 고려하십시오.

* 변환 매핑은 수동으로 복제해야 합니다.

* 자산 표현물은 기본적으로 복제되지 않습니다. 모든 관련 자산은 수동으로 복제해야 합니다.

## 변환 매핑 규칙 추가 {#add-rendition-mapping-rules}

변환 매핑 아래에 노드를 추가하려면 아래 단계를 따르십시오.

1. **CRXDE Lite**&#x200B;에서 이 경로 `/conf/screens/sling:configs/rendition-mapping`로 이동합니다.

1. **rendition-mapping** 아래에 노드를 만듭니다. **렌디션-매핑**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **만들기** —> **노드 만들기**&#x200B;를 클릭하십시오.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. **노드 만들기** 대화 상자에서 **규칙1** 및 **노드**&#x200B;비구조화&#x200B;**와 같은 매핑 규칙에 대한**&#x200B;이름&#x200B;**을 입력합니다.** **확인**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 쿼리 식이 포함된 값과 함께 표현식 속성을 추가해야 합니다.

   >[!NOTE]
   >자세한 내용은 [미디어 쿼리 구문 사용](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)을 참조하십시오.

   만든 **규칙1**&#x200B;을 클릭하고, 아래와 같이 **이름**&#x200B;에 **표현식**&#x200B;을 입력하고 **값**&#x200B;에 **(orientation:landscape)**&#x200B;을 입력합니다. **추가**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 변환 이름 지정 패턴을 포함하는 값으로 패턴 속성을 추가합니다.

   >[!NOTE]
   >패턴 속성에 정의된 값은 새 자산 표현물과 일치하며 표현식이 true로 평가되는 경우 선택됩니다.

   패턴 속성을 추가하려면 만든 **규칙1**&#x200B;을 클릭하고, 아래와 같이 **이름**&#x200B;에 **pattern**&#x200B;을 입력하고 **값**&#x200B;에 **가로**&#x200B;를 입력합니다. **추가**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. **모두 저장**&#x200B;을 클릭하면 **rendition-mapping**&#x200B;에서 생성한 노드 아래에 속성이 표시됩니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 다음 단계 {#next-steps}

이제 컨텐츠 작성자로서 표현물을 구성 및 업로드했으면 적응형 표현물을 사용하고, AEM Screens 채널에서 이 기능을 사용할 수 있도록 대형 네트워크에 대해 장치를 마이그레이션할 수 있습니다. 자세한 내용은 [응용 표현물 사용](/help/user-guide/using-adaptive-renditions.md)을 참조하십시오.
