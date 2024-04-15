---
title: 적응형 렌디션 아키텍처 개요 및 구성
description: AEM Screens의 적응형 표현물 CRXDE Lite에서 아키텍처 개요 및 구성에 대해 알아봅니다.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 3%

---

# 적응형 표현물: 아키텍처 개요 및 구성 {#adaptive-renditions}

## 소개 {#introduction}

적응형 렌디션을 사용하면 장치가 고객 정의 규칙에 따라 장치에 가장 적합한 렌디션을 자동으로 선택할 수 있습니다. 디바이스는 이러한 규칙에 따라 에셋의 가장 적절한 렌디션을 자동으로 다운로드하고 재생하여 고객이 다음 디자인에만 집중할 수 있도록 합니다 *main* 경험.

## 목표 {#objective}

이제 AEM Screens 개발자로서 모든 콘텐츠 변형을 수동으로 만들지 않고도 장치별 에셋 렌디션을 자동으로 다운로드하고 재생하도록 구성할 수 있습니다. 콘텐츠 작성자가 AEM Screens 채널에서 이 기능을 사용하기 전에 적응형 렌디션을 구성합니다.

## 아키텍처 개요 {#architectural-overview}

적응형 렌디션은 특정 명명 규칙에 따라 이름이 지정된 에셋에 대한 여러 렌디션을 갖는 개념을 기반으로 합니다. 특정 렌디션을 재생하려면 예상되는 기능이 있는 장치에서만 확인할 수 있는 미디어 쿼리 식을 평가해야 합니다.

연관된 렌디션 이름 지정 패턴이 있는 기능은 아래 그림과 같이 세로 또는 가로와 같은 렌디션 매핑 규칙을 정의합니다. 사용 가능한 모든 표현식을 계산한 후 화면 플레이어는 일치하는 규칙에 해당하는 명명 패턴을 수집합니다. 패턴은 렌디션 이름에서 패턴을 찾아 시퀀스 재생 중에 올바른 렌디션을 찾는 데 사용됩니다.

![이미지](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screens 프로젝트에 렌디션 매핑 속성 추가 {#rendition-mapping-new}

적응형 렌디션 기능을 활성화하려면 다음 매핑 규칙이 있어야 하며 채널 및 디스플레이에 대한 CA(컨텍스트 인식) 구성을 해결해야 합니다.

>[!NOTE]
>콘텐츠 인식 구성에 대한 자세한 내용은 을 참조하십시오. [여기](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

아래 단계에 따라 설정을 구성하십시오.

1. 다음으로 이동 **CRXDE Lite**. 다음과 같은 경우 확인 **렌디션 매핑** 구성이 다음 위치에 있음 `/conf/screens/sling:configs/rendition-mapping`을 참조하십시오.

   >![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >최신 기능 팩 202109을 설치한 경우 **렌디션 매핑** 에 미리 채워진 노드 구조 `/conf/screens/sling:configs/rendition-mapping` CRXDE Lite. 다음을 참조하십시오 [기능 팩 202109 릴리스 정보](/help/user-guide/release-notes-fp-202109.md) 최신 기능 팩에 대한 자세한 내용을 보려면 .
   >기존 프로젝트의 경우 Screens 프로젝트에 **렌디션 매핑** 구성이 연결되었습니다. 다음을 참조하십시오 [기존 프로젝트에 렌디션 매핑 추가](#rendition-mapping-existing) 섹션에 자세히 설명되어 있습니다.

### 기존 프로젝트에 렌디션 매핑 속성 추가 {#rendition-mapping-existing}

1. 다음으로 이동 **CRXDE Lite**.

1. 를 추가하여 렌디션 매핑 연결을 명시적으로 정의 `sling:configRef` 을(를) 가리키는 속성 `/conf/screens` 아래 그림과 같이 프로젝트 콘텐츠 노드로 이동합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 렌디션 매핑 규칙 추가 {#add-rendition-mapping-rules}

렌디션 매핑에 노드를 추가하려면 아래 단계를 따르십시오.

1. 이 경로로 이동 `/conf/screens/sling:configs/rendition-mapping` 출처: **CRXDE Lite**.
1. 아래에 노드 만들기 **렌디션 매핑**. 마우스 오른쪽 버튼 클릭 **렌디션 매핑** 및 선택 **만들기** > **노드 만들기**&#x200B;을 참조하십시오.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 다음을 입력합니다. **이름** 매핑 규칙: **rule1** 및 노드 **유형** 다음으로: **`nt:unstructured`** 위치: **노드 만들기** 대화 상자. 선택 **확인**.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 쿼리 표현식이 포함된 값으로 표현식 속성을 추가합니다.

   >[!NOTE]
   >다음을 참조하십시오 [미디어 쿼리 구문 사용](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) 자세히 알아보십시오.

   선택 **rule1** 만든 후 입력한 값 **표현식** 위치: **이름** 및 **(orientation:landscape)** 위치: **값**&#x200B;아래에 표시된 대로 를 클릭합니다. **추가**&#x200B;를 선택합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 렌디션 이름 지정 패턴을 포함하는 값으로 패턴 속성을 추가합니다.

   >[!NOTE]
   >표현식이 true로 평가되는 경우 패턴 속성에 정의된 값이 새 자산 렌디션과 일치하고 선택됩니다.

   패턴 속성을 추가하려면 다음을 선택합니다. **rule1** 만든 후 입력한 값 **패턴** 위치: **이름** 및 **가로** 위치: **값**&#x200B;아래에 표시된 대로 를 클릭합니다. **추가**&#x200B;를 선택합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 선택 **모두 저장** 에서 만든 노드 아래의 속성을 확인합니다. **렌디션 매핑**.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 다음 단계 {#next-steps}

콘텐츠 작성자는 렌디션 매핑 속성 및 규칙을 추가한 후 에셋을 구성할 수 있습니다. 이 작업은 적응형 표현물을 사용하여 수행할 수도 있고, 대규모 네트워크용으로 디바이스를 마이그레이션하여 AEM Screens 채널에서 이 기능을 사용할 수도 있습니다. 다음을 참조하십시오 [AEM Screens에서 적응형 표현물 사용](/help/user-guide/using-adaptive-renditions.md) 추가 정보.
