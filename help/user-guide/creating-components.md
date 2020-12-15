---
title: 구성 요소 만들기
seo-title: 구성 요소 만들기
description: AEM 구성 요소는 웹 페이지에서 사용할 수 있는 컨텐츠를 보존, 형식 지정 및 렌더링하는 데 사용됩니다. 채널 작성 및 구성 요소 렌더링에 대해 알려면 이 페이지를 따르십시오.
seo-description: AEM 구성 요소는 웹 페이지에서 사용할 수 있는 컨텐츠를 보존, 형식 지정 및 렌더링하는 데 사용됩니다. 채널 작성 및 구성 요소 렌더링에 대해 알려면 이 페이지를 따르십시오.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---


# 구성 요소 {#creating-components} 만들기

AEM 구성 요소는 웹 페이지에서 사용할 수 있는 컨텐츠를 보존, 형식 지정 및 렌더링하는 데 사용됩니다.

>[!NOTE]
>
>AEM 구성 요소 만들기에 대한 자세한 내용은 AEM 구성 요소 개발을 참조하십시오.

## 제작 채널 {#authoring-channels}

채널은 디스플레이 세트로 전달되는 컨텐츠의 중앙 객체입니다. 따라서 컨텐츠 작성자는 일반적으로 컨텐츠를 추가하거나 수정하기 위해 편집기에서 채널을 엽니다. 채널은 ***cq:Page***&#x200B;이므로 채널에서 구성 요소를 추가하고 변경하는 것과 동일한 기존 UX 패턴을 따릅니다.

그러나 채널 내의 구성 요소는 일반적으로 전체 화면으로 렌더링되므로 단일 구성 요소를 편집하거나 새 주문을 작성할 때 제작 환경이 어려워집니다. 따라서 채널은 구성 요소의 서로 다른 보기를 렌더링하기 위해 선택기에 의존합니다. 제작 환경에서는 편집 선택기를 사용하여 사용자 지정 채널 렌더링을 활성화합니다.

예, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

사용자는 편집하는 동안 URL에 선택기를 추가할 필요가 없습니다. 클라이언트 측 로직은 레이어 전환 이벤트를 수신하고 채널에 전용 리소스 유형이 *screens/core/components/channel인 경우 선택기를 추가합니다.*

## 구성 요소 렌더링 중 {#rendering-components}

적절한 작성을 활성화하려면 구성 요소에 다음 두 개의 렌더링을 제공해야 합니다.

| **구성 요소** | **표현물** |
|---|---|
| *my-component/my-component.html* | 제작 렌더링 |
| *my-component/edit.html* | 더 작은 보기에서 렌더링 편집 |

내장 구성 요소는 다음과 같은 클라이언트 라이브러리 범주를 활용합니다.

| **구성 요소** | **클라이언트 라이브러리** |
|---|---|
| *cq.screens.components.edit* | 제작 중에 로드해야 하는 CSS 및 JS |
| *cq.screens.components.production* | 채널이 실행될 때 로드해야 하는 CSS 및 JS |
| *cq.screens.components* | 공유 CSS 및 JS |

>[!NOTE]
>
>사용자 지정 구성 요소를 개발하려면 ***[AEM Screens 샘플 구성 요소 템플릿](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

