---
title: AEM Screens에서 응용 표현물 사용
description: 이 페이지에서는 AEM Screens에서 응용 표현물을 사용하는 방법을 설명합니다.
source-git-commit: 68e7a47d7a9b10d1d3fecb7a7f7d96bbbde1c48a
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# AEM Screens에서 응용 표현물 사용 {#adaptive-renditions}

## 소개 {#introduction}

응용 변환을 사용하여 장치는 고객이 정의한 규칙에 따라 장치에 대해 가장 적합한 변환을 자동으로 선택할 수 있습니다. 장치는 이러한 규칙에 따라 자산의 가장 적절한 렌디션을 자동으로 다운로드 및 재생하므로 고객은 *main* 환경을 디자인하는 데에만 집중할 수 있습니다.

## 목표 {#objective}

이제 AEM Screens 컨텐츠 작성자는 모든 컨텐츠 변형을 수동으로 만들지 않고도 자동으로 다운로드 및 재생되도록 장치별 자산 변환을 구성할 수 있습니다.
개발자가 표현물 매핑 속성 및 규칙을 추가하면 이제 표현물 매핑을 자산에 적용하고 나중에 AEM Screens 채널에 포함할 수 있습니다.

>[!IMPORTANT]
>응용 표현물 사용을 시작하기 전에 AEM Screens 채널에서 이 기능의 아키텍처 개요 및 구성에 대해 학습하는 것이 좋습니다. [응용 표현물 을 참조하십시오. 아키텍처 개요 및 구성](/help/user-guide/adaptive-renditions.md) 을 참조하십시오.

## 채널에서 응용 표현물 사용 {#using-adaptive-renditions}

>[!NOTE]
>이제 컨텐츠 작성자로서 [변환 매핑 속성을 Screens 프로젝트](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) 및 [변환 매핑 규칙](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)에 추가했으면 렌디션을 자산에 적용할 준비가 되었습니다.

### 자산에 표현물 적용 {#apply-renditions-assets}

Tour Screens 채널에서 사용할 자산에 변환을 적용하려면 아래 절차를 따르십시오.

1. AEM 인스턴스의 **Assets** 폴더로 이동합니다.

1. 간판 디스플레이에 더 적합한 자산 버전(예: `seahorse.jpg`)을 만드십시오.

1. **CRXDE Lite**&#x200B;에서 **pattern** 속성에 정의된 것과 유사한 표현물 이름 지정 패턴(예:`landscape`)을 선택합니다. 자세한 내용은 [변환 매핑 규칙 추가](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)를 참조하십시오.

1. 패턴(3단계에서 정의됨)이 포함되도록 자산 파일의 이름을 변경합니다(예: `seahorse-landscape.png`).

1. 아래 그림과 같이 **변환 추가**&#x200B;를 클릭하여 표현물을 업로드합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

1. 자산을 추가한 후 자산을 선택하고 작업 표시줄에서 **게시 관리**&#x200B;를 클릭하여 자산을 게시합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >게시 관리 및 컨텐츠 업데이트 전달에 대한 자세한 내용은 [온디맨드 콘텐츠 업데이트](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en)를 참조하십시오.


## 마이그레이션 전략 {#migration-strategy}

>[!IMPORTANT]
>대규모 네트워크의 경우, 이 기능이 매니페스트 및 파일 저장소 형식에 변경 사항을 도입하므로 위험을 완화하도록 마이그레이션을 단계적으로 수행하는 것이 좋습니다. 전체 프로젝트에 `sling:configRef`을 추가하면 모든 플레이어가 기능 팩 6.5.9로 업데이트됩니다. 일부 플레이어를 업데이트한 경우 모든 플레이어가 기능 팩 6.5.9로 업데이트된 디스플레이, 위치 또는 채널 폴더에만 `sling:configRef`을 추가해야 합니다.

다음 다이어그램은 큰 네트워크에 대한 마이그레이션 전략을 보여 줍니다.

![이미지](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

이 기능을 활성화하려면 적어도 한 개의 매핑 규칙을 추가하고 디스플레이 및 채널 컨텍스트에서 표현물 매핑 구성을 확인할 수 있는지 확인하십시오. 아래 절차에 따라 마이그레이션하십시오.

1. [변환 매핑 규칙](/help/user-guide/adaptive-renditions.md)을 추가합니다.
1. 새 채널용 폴더를 만들고 변환 매핑 구성을 가리키는 참조를 추가합니다.
1. 이전 채널을 대체하는 새 채널을 만들고 렌디션을 업로드합니다.
1. 디스플레이를 새 채널에 재할당합니다.
1. 마이그레이션된 디스플레이 또는 위치에 대한 참조를 추가하여 표현물 매핑 구성을 가리킵니다.
1. 나머지 모든 채널 및 디스플레이에 대해 3, 4 및 5단계를 반복합니다.

   >[!NOTE]
   >마이그레이션을 완료한 후 채널, 표시 및 위치에서 모든 구성 참조를 제거하고 프로젝트 컨텐츠 노드에 단일 구성 참조를 추가해야 합니다.

