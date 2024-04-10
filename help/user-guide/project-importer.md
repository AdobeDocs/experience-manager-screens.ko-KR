---
title: 파일의 새 프로젝트 가져오기
description: 이 기능을 사용하면 CSV/XLS 스프레드시트에서 AEM Screens 프로젝트로 위치 세트를 일괄 가져올 수 있습니다.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 1%

---

# 파일의 새 프로젝트 가져오기 {#new-project-importer-from-file}

이 섹션에서는 CSV/XLS 스프레드시트에서 AEM Screens 프로젝트로 위치 세트를 일괄 가져오는 기능에 대해 설명합니다.

## 소개 {#introduction}

조직에서 처음으로 AEM Screens 프로젝트를 설정하는 경우 모든 위치도 만들어야 합니다. 프로젝트에 많은 위치가 포함된 경우 UI에서 많은 항목을 클릭하고 기다리는 지루한 작업이 발생합니다.

이 기능의 목표는 프로젝트를 설정하는 데 필요한 시간을 줄여 예산 문제를 해결하는 것입니다.

작성자가 스프레드시트를 입력 파일로 제공하고 시스템에서 백엔드에 위치 트리를 자동으로 만들도록 함으로써 다음과 같은 기능을 제공합니다.

* *ui를 통해 수동으로 클릭하는 것보다 훨씬 우수한 성능 달성*
* *고객이 보유한 위치를 자체 시스템에서 내보내고 AEM에서 직접 쉽게 가져올 수 있습니다*

이렇게 하면 초기 프로젝트 설정 중에 또는 기존 AEM Screens을 새 위치로 확장할 때 시간과 비용을 절약할 수 있습니다.

## 아키텍처 개요 {#architectural-overview}

다음 다이어그램은 프로젝트 가져오기 기능의 아키텍처 개요를 보여 줍니다.

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 데이터 모델 {#data-model}

프로젝트 가져오기에 대한 데이터 모델은 아래에 설명되어 있습니다.

>[!NOTE]
>
>현재 릴리스는 위치 가져오기만 지원합니다.

| **속성** | **설명** |
|---|---|
| ***`path {string*}`*** | 위치에 대한 리소스 경로 |
| ***`[./jcr:title] {string*}`*** | 사용할 템플릿의 이름(위치) *screens/core/templates/location*) |
| ***`template {string}`*** | 페이지에 사용할 선택적 제목 |
| ***`[./jcr:description] {string}`*** | 페이지에 사용할 선택적 설명 |

스프레드시트(CSV/XLS) 파일에는 다음 열이 필요합니다.

* **경로 {string}** - 가져올 위치의 경로. 여기서 경로의 루트는 프로젝트의 위치 폴더입니다(즉, *`/foo`* 을(를) (으)로 가져옴 *`/content/screens/<project>/locations/foo`*)
* **템플릿 {string}** - 새 위치에 사용할 템플릿은 현재 허용되는 유일한 값이 &quot;위치&quot;이지만 향후 모든 Screens 템플릿으로 확장됩니다(`display`, `sequencechannel`등)
* **[/*] {string}** - 위치에 설정할 모든 옵션 속성(즉, `./jcr:title`, `./jcr:description`, `./foo, ./bar`). 현재 릴리스에서는 필터링을 허용하지 않습니다.

>[!NOTE]
>
>위의 조건과 일치하지 않는 열은 모두 무시됩니다. 예를 들어 시트(CSV/XLS) 파일에 다음 이외의 다른 열이 정의되어 있는 경우 **경로**, **템플릿**, **제목**, 및 **설명** 파일에서 해당 필드는 무시됩니다. 및, **프로젝트 가져오기** 에서는 프로젝트를 AEM Screens 프로젝트로 가져오기 위한 추가 필드에 대한 유효성을 검사하지 않습니다.

## 프로젝트 가져오기 사용 {#using-project-importer}

다음 섹션에서는 AEM Screens 프로젝트에서 프로젝트 가져오기를 사용하는 방법에 대해 설명합니다.

>[!CAUTION]
>
>제한 사항:
>
>* CSV/XLS/XLSX 확장명 이외의 파일은 현재 릴리스에서 지원되지 않습니다.
>* 가져온 파일 및 &quot;&quot;로 시작하는 모든 항목에 대한 속성 필터링이 없습니다./&quot;을(를) 가져옵니다.
>

### 사전 요구 사항 {#prerequisites}

* 제목이 인 프로젝트 만들기 **DemoProjectImport**

* 가져와야 하는 샘플 CSV 또는 Excel 파일을 사용합니다.

데모 목적으로 아래 섹션에서 Excel 파일을 다운로드할 수 있습니다.

[파일 가져오기](assets/minimal-file.xls)

### 최소 필수 필드가 있는 파일 가져오기 {#importing-the-file-with-minimum-required-fields}

최소 필수 필드가 있는 위치 폴더로 파일을 가져오려면 아래 단계를 따르십시오.

>[!NOTE]
>
>다음 예제에서는 프로젝트를 가져오는 데 필요한 최소 4개의 필드를 보여줍니다.

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens 프로젝트(**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 프로젝트 선택,** DemoProjectImporter **>** 만들기 **>** 사이드 바** 위치 가져오기

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. 다음 **가져오기** 마법사가 표시됩니다. 위치가 있는 프로젝트의 파일을 선택하거나 파일(***minimal-file.xls***)에서 다운로드했습니다. *전제 조건* 섹션.

   파일을 선택했으면 **다음**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 가져오기 마법사에서 파일(위치)의 내용을 확인하고 **가져오기**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 따라서 이제 프로젝트로 가져온 모든 위치를 볼 수 있습니다.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
