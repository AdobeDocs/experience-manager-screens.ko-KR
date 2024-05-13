---
title: 직접 배치 워크플로 구성
description: 이 페이지에서는 직접 배치 워크플로우 구성을 중점적으로 다룹니다.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# 직접 배치 워크플로 구성 {#direct-placement-workflow}

사전 정의된 AEM Screens 채널에 에셋을 프로그래밍 방식으로 삽입할 수 있는 에셋 워크플로 구성에 대해 알아볼 수 있도록 이 페이지를 따르십시오.

이 섹션에서는 다음 주제를 다룹니다.

* 개요
* 직접 배치 워크플로우 구성

## 개요 {#overview}

직접 배치 워크플로 구성은 AEM Screens 프로젝트 채널을 자산의 특정 폴더에 매핑하며, 해당 폴더에서 에셋을 배치할 수 있도록 합니다. Adobe은 일괄 오프라인 업데이트를 트리거하여 게시를 완료할 것을 권장합니다.

또는 콘텐츠 작성자는 를 수동으로 클릭할 수 있습니다. **오프라인 컨텐츠 업데이트**.

>[!NOTE]
>
>벌크 오프라인 업데이트를 사용하는 방법을 알아보려면 다음을 참조하십시오. [서비스로서의 콘텐츠 업데이트](/help/user-guide/content-update-as-a-service.md).

## 직접 배치 워크플로우 구성 {#configuring-workflow}

>[!IMPORTANT]
>
>구성을 시작하기 전에 `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. 패키지를 설치한 후에는 AEM 인스턴스 > 도구(아이콘) >에서 해당 패키지를 보고 액세스할 수 있습니다 **워크플로** > **워크플로 모델**.

직접 배치 워크플로우를 구성하려면 아래 단계를 수행합니다.

1. AEM 인스턴스에서 AEM Screens으로 이동하여 이라는 Screens 프로젝트를 만듭니다. **자산 워크플로우**.

1. 이라는 제목이 있는 채널 만들기 **Workflow-Assets** 다음 아래에 **채널** 폴더를 삭제합니다.

