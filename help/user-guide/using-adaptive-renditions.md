---
title: AEM Screens에서 응용 표현물 사용
description: 이 페이지에서는 AEM Screens에서 응용 표현물을 사용하는 방법을 설명합니다.
index: false
source-git-commit: d3a54ed85b9fa2ddf3918161566ba2c82c373be0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---

# AEM Screens에서 응용 표현물 사용 {#adaptive-renditions}

## 소개 {#introduction}

응용 변환을 사용하여 장치는 고객이 정의한 규칙에 따라 장치에 대해 가장 적합한 변환을 자동으로 선택할 수 있습니다. 장치는 이러한 규칙에 따라 자산의 가장 적절한 렌디션을 자동으로 다운로드 및 재생하므로 고객은 *main* 환경을 디자인하는 데에만 집중할 수 있습니다.

## 목표 {#objective}

이제 AEM Screens 컨텐츠 작성자는 모든 컨텐츠 변형을 수동으로 만들지 않고도 자동으로 다운로드 및 재생되도록 장치별 자산 변환을 구성할 수 있습니다.
개발자가 표현물 매핑 속성 및 규칙을 추가하면 이제 표현물 매핑을 자산에 적용하고 나중에 AEM Screens 채널에 포함할 수 있습니다.

>[!IMPORTANT]
>응용 표현물 사용을 시작하기 전에 AEM Screens 채널에서 이 기능의 아키텍처 개요 및 구성에 대해 학습하는 것이 좋습니다. 응용 표현물 을 참조하십시오. 아키텍처 개요 및 구성 을 참조하십시오.

## 마이그레이션 전략 {#migration-strategy}

>[!IMPORTANT]
>대규모 네트워크의 경우, 이 기능이 매니페스트 및 파일 저장소 형식에 변경 사항을 도입하므로 위험을 완화하도록 마이그레이션을 단계적으로 수행하는 것이 좋습니다.

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


## AEM Screens 채널에서 표현물 업로드 및 적응형 표현물 사용 {#upload-renditions}

1. 간판 디스플레이에 더 적합한 자산 버전(예: `portrait orientation`)을 만드십시오.

1. 변환 이름 지정 패턴(예:`portrait`)을 선택합니다.

1. 패턴을 포함하도록 자산 파일 이름을 변경합니다(예: `my_asset_portrait.png`).

1. 아래 그림과 같이 **변환 추가**&#x200B;를 클릭하여 표현물을 업로드합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-rendition.png)