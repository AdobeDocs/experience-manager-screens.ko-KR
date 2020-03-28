---
title: '직접 배치 워크플로우 구성 '
seo-title: 직접 배치 워크플로우 구성
description: 이 페이지에서는 직접 배치 워크플로우 구성을 강조 표시합니다.
seo-description: 이 페이지에서는 직접 배치 워크플로우 구성을 강조 표시합니다.
translation-type: tm+mt
source-git-commit: 19baf90409eab4c72fb38e992c272338b0098d89

---


# 직접 배치 워크플로우 구성 {#direct-placement-workflow}

사전 정의된 AEM Screens 채널에 자산을 프로그래밍 방식으로 삽입할 수 있도록 해주는 자산 워크플로우를 구성하려면 이 페이지를 따르십시오.

이 섹션에서는 다음과 같은 주제를 다룹니다.

* 개요
* 직접 배치 워크플로우 구성

## 개요 {#overview}

직접 배치 워크플로우 구성은 AEM Screens 프로젝트 채널을 자산의 특정 폴더에 매핑하고 해당 폴더에 있는 자산을 배치할 수 있도록 합니다. 게시를 완료하려면 일괄 오프라인 업데이트를 트리거하는 것이 좋습니다.

또는 컨텐츠 작성자는 오프라인 컨텐츠 업데이트를 수동으로 클릭할 **수 있습니다**.

>[!NOTE]
> 일괄 오프라인 업데이트를 사용하는 방법에 대한 자세한 내용은 서비스로 [컨텐츠 업데이트를 참조하십시오](/help/user-guide/content-update-as-a-service.md).

## 직접 배치 워크플로우 구성 {#configuring-workflow}

>[!IMPORTANT]
> 구성을 시작하기 전에 데모 패키지를 설치해야 [합니다](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). 패키지를 설치한 후에는 AEM 인스턴스 —> 도구(아이콘) —> 워크플로우 —> 워크플로우 **모델에서** 보고 액세스할 **수 있습니다**.

아래 절차에 따라 직접 배치 워크플로우를 구성합니다.

1. AEM 인스턴스에서 AEM Screens로 이동하고 자산 워크플로우라는 제목의 Screens 프로젝트를 **만듭니다**.

1. 채널 폴더 아래에 워크플로우 **자산으로** 지정된 채널을 **만듭니다** .

1. 
