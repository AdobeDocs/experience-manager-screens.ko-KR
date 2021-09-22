---
title: AEM Screens의 응용 표현물
description: 이 페이지에서는 AEM Screens의 응용 표현물에 대한 아키텍처 개요 및 구성에 대해 설명합니다.
index: false
source-git-commit: f9e10463418ddc44f75c7d6c689298dcba20338f
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 3%

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

## 응용 표현물 사용을 위한 설정 구성 {#setup-adaptive-renditions}

응용 표현물 기능을 활성화하려면 다음 매핑 규칙이 있어야 하며, 채널 및 디스플레이에 대해 컨텍스트 인식(CA) 구성을 확인할 수 있어야 합니다.

>[!NOTE]
>내용 인식 구성에 대한 자세한 내용은 여기 [여기](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)를 참조하십시오.

아래 절차에 따라 설정을 구성하십시오.

1. **CRXDE Lite**&#x200B;로 이동합니다. 아래 그림과 같이 **rendition-mapping** 구성이 `JCR`에 있는지 확인합니다.

   >[!NOTE]
   >모든 최신 기능 팩에는 이 노드 구조가 미리 채워져 있습니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. 스크린 프로젝트에 렌디션 매핑 구성이 연결되어 있는지 확인합니다.

   * 스크린 프로젝트 마법사로 만든 모든 새 프로젝트에는 **렌디션-매핑** 구성을 가리키는 참조가 포함됩니다.

      ![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * 이전 버전의 Screens 프로젝트에서 `/conf/screens` 속성을 프로젝트 콘텐츠 노드에 추가하여 연결을 명시적으로 정의해야 합니다.`sling:configRef`

      ![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## 작성자 및 게시 설정 {#setup-author-publish}

응용 표현물을 사용하기 전에 작성자 및 게시에서 다음 권장 사항을 고려하십시오.

* 변환 매핑은 수동으로 복제해야 합니다.

* 자산 표현물은 기본적으로 복제되지 않습니다. 모든 관련 자산은 수동으로 복제해야 합니다.

## 변환 매핑 규칙 추가 {#add-rendition-mapping-rules}

1. 매핑 규칙을 추가하려면 **렌디션-매핑** 노드 아래에 `nt:unstructured` 유형의 노드를 만들어야 합니다.

1. 쿼리 식을 포함하는 값으로 표현식 속성을 추가합니다.

   >[!NOTE]
   >자세한 내용은 [미디어 쿼리 구문 사용](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)을 참조하십시오.

1. 표현식이 true로 평가되는 경우 선택할 표현물 이름 지정 패턴을 포함하는 값과 함께 패턴 속성을 추가합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## 다음 단계 {#next-steps}

이제 컨텐츠 작성자로서 표현물을 구성 및 업로드했으면 적응형 표현물을 사용하고, AEM Screens 채널에서 이 기능을 사용할 수 있도록 대형 네트워크에 대해 장치를 마이그레이션할 수 있습니다. 자세한 내용은 [응용 표현물 사용](/help/user-guide/using-adaptive-renditions.md)을 참조하십시오.
