---
title: AEM Screens에서 적응형 표현물 사용
description: AEM Screens에서 적응형 렌디션을 사용하는 방법을 알아봅니다.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# AEM Screens에서 적응형 표현물 사용 {#adaptive-renditions}

## 소개 {#introduction}

적응형 렌디션을 사용하면 장치가 고객 정의 규칙에 따라 장치에 가장 적합한 렌디션을 자동으로 선택할 수 있습니다. 디바이스는 이러한 규칙에 따라 에셋의 가장 적절한 렌디션을 자동으로 다운로드하고 재생하여 고객이 다음 디자인에만 집중할 수 있도록 합니다 *main* 경험.

## 목표 {#objective}

이제 AEM Screens 컨텐츠 작성자는 모든 컨텐츠 변형을 수동으로 만들지 않고도 장치별 자산 렌디션을 자동으로 다운로드하고 재생하도록 구성할 수 있습니다.
개발자가 렌디션 매핑 속성 및 규칙을 추가한 후에는 에셋에 렌디션 매핑을 적용한 다음 AEM Screens 채널에 포함할 준비가 된 것입니다.

>[!IMPORTANT]
>AEM Screens Adobe 채널에서 적응형 렌디션 사용을 시작하기 전에 이 기능의 아키텍처 개요 및 구성에 대해 학습하는 것이 좋습니다. 다음을 참조하십시오 [적응형 표현물: 아키텍처 개요 및 구성](/help/user-guide/adaptive-renditions.md).

## 채널에서 적응형 표현물 사용 {#using-adaptive-renditions}

>[!NOTE]
>추가한 후 [스크린 프로젝트에 대한 렌디션 매핑 속성](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) 및 [렌디션 매핑 규칙](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), 콘텐츠 작성자는 이제 에셋에 렌디션을 적용할 준비가 되었습니다.

### 자산에 렌디션 적용 {#apply-renditions-assets}

Tour Screens 채널에서 사용할 자산에 렌디션을 적용하려면 다음을 수행합니다.

1. 다음 위치로 이동 **에셋** AEM 인스턴스의 폴더입니다.
1. 간판 표시에 더 적합한 에셋 버전 만들기(예: ) `seahorse.jpg`.
1. 렌디션 이름 지정 패턴(예: ) 선택`landscape`에서 정의된 것과 유사 **패턴** 의 속성 **CRXDE Lite**. 다음을 참조하십시오 [렌디션 매핑 규칙 추가](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) 을 참조하십시오.
1. 클릭 **렌디션 추가** 아래 그림과 같이 렌디션을 업로드합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 이름이 변경된 에셋 파일을 선택합니다. 추가하는 렌디션에는 패턴(3단계에서 정의됨)이 포함되어야 합니다. 예를 들면 다음과 같습니다. `seahorse-landscape.png`.
1. 에셋을 추가한 경우 에셋을 선택하고 을 클릭합니다 **게시 관리** 을 클릭하여 자산을 게시합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >다음을 참조하십시오 [온디맨드 콘텐츠 업데이트](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) 게시를 관리하고 작성자에서 게시로 콘텐츠 업데이트를 장치에 전달하는 방법에 대해 자세히 알아봅니다.

## 마이그레이션 전략 {#migration-strategy}

>[!IMPORTANT]
>대규모 네트워크의 경우 Adobe은 위험을 완화하기 위해 마이그레이션을 점차적으로 수행할 것을 권장합니다. 그 이유는 이 기능으로 인해 매니페스트와 파일 저장소 형식이 변경될 수 있기 때문입니다. 추가 `sling:configRef` 전체 프로젝트에는 모든 플레이어를 기능 팩 6.5.9로 업데이트하는 작업이 포함됩니다. 일부 플레이어를 업데이트한 경우 `sling:configRef` 모든 플레이어가 기능 팩 6.5.9로 업데이트된 디스플레이, 위치 또는 채널 폴더에만 해당됩니다.

다음 다이어그램은 대규모 네트워크에 대한 마이그레이션 전략을 보여 줍니다.

![이미지](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

이 기능을 사용하려면 매핑 규칙을 하나 이상 추가하고 디스플레이 및 채널의 컨텍스트에서 렌디션 매핑 구성을 확인할 수 있는지 확인합니다. 마이그레이션하려면 아래 단계를 따르십시오.

1. 추가 [렌디션 매핑 규칙](/help/user-guide/adaptive-renditions.md).
1. 새 채널의 폴더를 만들고 렌디션 매핑 구성을 가리키는 참조를 추가합니다.
1. 기존 채널을 대체하는 채널을 만들고 렌디션을 업로드합니다.
1. 새 채널에 디스플레이를 재할당합니다.
1. 렌디션 매핑 구성을 가리키는 마이그레이션된 디스플레이 또는 위치에 참조를 추가합니다.
1. 나머지 모든 채널 및 디스플레이에 대해 3, 4, 5단계를 반복합니다.

   >[!NOTE]
   >마이그레이션을 완료한 후 채널, 디스플레이 및 위치에서 모든 구성 참조를 제거하고 프로젝트 콘텐츠 노드에 단일 구성 참조를 추가해야 합니다.
