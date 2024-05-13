---
title: 구성 요소 만들기
description: AEM 구성 요소를 사용하여 웹 페이지에서 사용할 수 있는 콘텐츠를 유지하고, 형식을 지정하며, 렌더링하는 방법에 대해 알아봅니다.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 3%

---

# 구성 요소 만들기 {#creating-components}

AEM 구성 요소는 웹 페이지에서 사용할 수 있는 콘텐츠를 유지하고, 형식을 지정하며, 렌더링하는 데 사용됩니다.

>[!NOTE]
>
>AEM 구성 요소 만들기에 대한 자세한 내용은 AEM 구성 요소 개발을 참조하십시오.

## 채널 작성 {#authoring-channels}

채널은 디스플레이 집합에 전달되는 컨텐츠의 중앙 개체입니다. 따라서 콘텐츠 작성자는 일반적으로 편집기에서 채널을 열어 콘텐츠를 추가하거나 수정합니다. 채널이 ***`cq:Page`***, 그것은 채널에 구성 요소를 추가하고 변경하는 동일한 전통적인 UX 패턴을 따릅니다.

하지만 채널 내의 구성 요소는 일반적으로 전체 화면으로 렌더링되므로 작성 환경에서 단일 구성 요소를 편집하거나 새 주문을 작성하려고 할 때 문제가 발생합니다. 따라서 채널은 선택기에 의존하여 구성 요소의 다른 보기를 렌더링합니다. 작성 환경에서는 편집 선택기를 사용하여 사용자 지정 채널 렌더링을 활성화합니다.

예, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

사용자가 편집하는 동안 선택기를 URL에 추가할 필요는 없습니다. 클라이언트측 논리는 레이어 전환 이벤트를 수신하고, 채널에 전용 리소스 유형이 있는 경우 선택기를 추가합니다 *screens/core/components/channel*.

## 렌더링 구성 요소 {#rendering-components}

적절한 작성을 활성화하려면 구성 요소에서 다음 두 가지 렌더링을 제공해야 합니다.

| **구성 요소** | **렌디션** |
|---|---|
| *my-component/my-component.html* | 프로덕션 렌더링 |
| *my-component/edit.html* | 더 작은 보기에서 렌더링 편집 |

기본 제공 구성 요소는 다음 클라이언트 라이브러리 범주를 사용합니다.

| **구성 요소** | **클라이언트 라이브러리** |
|---|---|
| *cq.screens.components.edit* | 작성 중에 로드해야 하는 CSS 및 JS |
| *cq.screens.components.프로덕션* | 채널이 실행될 때 로드해야 하는 CSS 및 JS |
| *cq.screens.components* | 공유 CSS 및 JS |

>[!NOTE]
>
>사용자 지정 구성 요소를 개발하려면 다음을 사용하십시오***[AEM Screens 샘플 구성 요소 템플릿](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
