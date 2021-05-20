---
title: 파일에서 새 프로젝트 가져오기
seo-title: 파일에서 새 프로젝트 가져오기
description: 이 기능을 사용하면 위치 세트를 CSV/XLS 스프레드시트에서 AEM Screens 프로젝트로 일괄적으로 가져올 수 있습니다.
seo-description: 이 기능을 사용하면 위치 세트를 CSV/XLS 스프레드시트에서 AEM Screens 프로젝트로 일괄적으로 가져올 수 있습니다.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: 화면 관리
role: Administrator
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 3%

---

# 파일 {#new-project-importer-from-file}에서 새 프로젝트 가져오기

이 섹션에서는 위치 세트를 CSV/XLS 스프레드시트에서 AEM Screens 프로젝트로 일괄적으로 가져오는 기능에 대해 설명합니다.

## 소개 {#introduction}

AEM Screens 프로젝트를 설정할 때 조직에서 처음으로 모든 위치를 만들어야 합니다. 프로젝트에 많은 위치가 포함되어 있으면 많은 클릭 및 UI에서 기다리는 작업이 번거롭게 됩니다.

이 기능의 목표는 프로젝트를 설정하는 데 필요한 시간을 줄이고 예산 문제를 해결하는 것입니다.

작성자가 스프레드시트를 입력 파일로 제공하고 시스템이 백 엔드에서 위치 트리를 자동으로 만들 수 있도록 함으로써 이 기능은 다음과 같습니다.

* *UI를 수동으로 클릭하는 것보다 성능이 훨씬 향상됩니다*
* *고객이 보유한 위치를 자체 시스템에서 내보내고 AEM에서 직접 가져올 수 있도록 해줍니다.*

따라서 초기 프로젝트 설정 중에 또는 기존 AEM Screens을 새 위치로 확장할 때 시간과 비용을 절약할 수 있습니다.

## 아키텍처 개요 {#architectural-overview}

다음 다이어그램은 프로젝트 가져오기 기능에 대한 아키텍처 개요를 보여줍니다.

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 데이터 모델 {#data-model}

프로젝트 가져오기에 대한 데이터 모델은 아래에 설명되어 있습니다.

>[!NOTE]
>
>현재 릴리스는 위치만 가져올 수 있습니다.

| **속성** | **설명** |
|---|---|
| ***경로 {string*}** | 위치의 리소스 경로입니다 |
| ***[./jcr:title] {string*}** | 사용할 템플릿의 이름(*screens/core/templates/location*) |
| ***템플릿 {string}*** | 페이지에 사용할 선택적 제목 |
| ***[./jcr:description] {string}*** | 페이지에 사용할 선택적 설명 |

스프레드시트(CSV/XLS) 파일에는 다음 열이 필요합니다.

* **경로 {string}**  가져올 위치의 경로입니다. 여기서 경로의 루트는 프로젝트의 위치 폴더(즉,  */content/screens/* /locations/foo *로 &lt;project>*&#x200B;가져올 폴더)입니다

* **템플릿 {string}** 새 위치에 사용할 서식 파일은 &quot;location&quot;이지만 나중에 모든 스크린 서식 파일(&quot;display&quot;, &quot;sequencecchannel 등)로 확장됩니다.
* **[./*] {string}** 위치에 설정할 모든 선택적 속성(즉, )입니다./jcr:title, ./jcr:description, ./foo,/막대). 현재 릴리스에서는 현재 필터링할 수 없습니다

>[!NOTE]
>
>위의 조건과 일치하지 않는 열은 무시됩니다. 예를 들어, 시트(CSV/XLS) 파일에 **경로**,**템플릿**,**제목** 및 **description** 이외의 다른 열이 정의되어 있는 경우 해당 필드는 무시되고 **프로젝트 가져오기 프로그램**&#x200B;은 프로젝트를 AEM Screens 프로젝트로 가져올 수 있는 추가 필드의 유효성을 검사하지 않습니다.

## 프로젝트 가져오기 도구 사용 {#using-project-importer}

다음 섹션에서는 AEM Screens 프로젝트에서 Project Importer를 사용하는 방법을 설명합니다.

>[!CAUTION]
>
>제한 사항:
>
>* CSV/XLS/XLSX 확장 이외의 파일은 현재 릴리스에서 지원되지 않습니다.
>* 가져온 파일 및 &quot;&quot;로 시작하는 모든 항목에 대한 속성 필터링이 없습니다./&quot;를 가져옵니다.

>



### 전제 조건 {#prerequisites}

* **DemoProjectImport** 라는 새 프로젝트를 만듭니다.

* 가져와야 하는 샘플 CSV 또는 Excel 파일을 사용합니다.

데모 목적으로 아래 섹션에서 Excel 파일을 다운로드할 수 있습니다.

[파일 가져오기](assets/minimal-file.xls)

### 최소 필수 필드 {#importing-the-file-with-minimum-required-fields} 가 있는 파일 가져오기

최소 필수 필드가 있는 위치 폴더로 파일을 가져오려면 아래 단계를 따르십시오.

>[!NOTE]
>
>다음 예제에서는 프로젝트를 가져오는 데 필요한 최소 4개의 필드를 보여줍니다.

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens 프로젝트(**DemoProjectImport**)로 이동합니다.

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 측면 막대에서 ** DemoProjectImporter **—>** **—>** 위치 가져오기** 프로젝트를 선택합니다.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. **가져오기** 마법사가 열립니다. 위치에 있는 프로젝트에 대해 가지고 있는 파일을 선택하거나 *사전 요구 사항* 섹션에서 다운로드한 파일(***minimal-file.xls***)을 선택합니다.

   파일을 선택한 후 **다음**&#x200B;을 클릭합니다.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 가져오기 마법사에서 파일(위치)의 콘텐츠를 확인하고 **가져오기**&#x200B;를 클릭합니다.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 따라서 이제 프로젝트에 가져온 모든 위치를 볼 수 있습니다.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
