---
title: 채널에 구성 요소 추가
description: AEM Screens 프로젝트의 채널에 구성 요소를 추가하는 방법에 대해 자세히 알아보십시오.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 5%

---

# 채널에 구성 요소 추가{#adding-components-to-a-channel}

구성 요소는 AEM(Adobe Experience Manager) 경험의 기본 요소입니다. 여러 구성 요소를 사용하여 AEM Screens 프로젝트의 채널에 추가할 수 있습니다.

## AEM Screens의 구성 요소 {#components-in-aem-screens}

AEM Screens은 Screens 프로젝트에서 사용할 수 있는 다양한 AEM 구성 요소를 제공합니다.

### AEM Screens 구성 요소 보기 {#viewing-aem-screens-components}

AEM Screens 프로젝트를 만들 때마다 프로젝트에 추가할 수 있는 기본 구성 요소 목록이 표시됩니다.

Screens 프로젝트에 대한 기본 구성 요소를 보려면 아래 단계를 따르십시오.

1. 채널을 클릭합니다. 예를 들어 **`We.Retail In Store`** > **채널** > **유휴 채널**&#x200B;입니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.
1. AEM 편집기의 사이드바에서 **+** 아이콘을 클릭합니다.
1. AEM Screens 프로젝트에 기본적으로 포함되는 모든 구성 요소가 아래 그림과 같이 표시됩니다.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 새 구성 요소 추가 {#adding-a-new-component}

AEM은 몇 가지 다른 구성 요소를 제공합니다. 다른 구성 요소가 AEM Screens과 호환된다고 가정할 때 언제든지 해당 구성 요소를 프로젝트에 추가할 수 있습니다(기본적으로 포함되지 않음).

다음 예는 AEM Screens 프로젝트에 Livefyre 구성 요소를 추가하는 방법을 보여줍니다.

1. 구성 요소를 추가할 채널을 클릭합니다. 예를 들어 **`We.Retail In Store`** > **채널** > **유휴 채널**&#x200B;입니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.
1. **디자인** 모드를 클릭합니다.
1. **Parsys 디자인** 대화 상자를 열 수 있도록 오른쪽의 전체 디자인 편집기를 클릭하고 설정 기호를 클릭합니다.
1. AEM Screens 프로젝트로 가져올 구성 요소를 클릭할 수 있습니다. 다음 예제에서는 AEM Screens 프로젝트에 **Livefyre** 구성 요소를 추가하는 방법을 보여줍니다.

![add_components](assets/adding_components.gif)

>[!NOTE]
>
>마찬가지로 AEM Screens과 호환되는 다른 새 구성 요소를 프로젝트에 추가할 수 있습니다.

## AEM 화면 구성 요소 이해 {#understanding-aem-screen-components}

다음 섹션에서는 프로젝트에서 사용할 수 있는 AEM Screens 구성 요소에 대해 설명합니다.

>[!NOTE]
>
>구성 요소의 등록 정보를 보려면 구성 요소를 클릭하고 망치 아이콘을 클릭하여 등록 정보를 열거나 봅니다.

### 애플리케이션 {#application}

**Application** 구성 요소를 사용하여 채널에 응용 프로그램을 추가할 수 있습니다.

애플리케이션 구성 요소에는 다음과 같은 속성이 있습니다.

| **속성** | **설명** |
|---|---|
| ***응용 프로그램 경로*** | 응용 프로그램이 있는 절대 경로를 클릭합니다. |
| ***기간(밀리초)*** | 응용 프로그램 기간을 클릭합니다. 기본적으로 duration은 -1로 설정되어 있으며, 이는 요소가 영원히(즉, 단일 페이지 애플리케이션) 실행됨을 의미합니다. 지속 시간 값을 0보다 높게 설정하면 지정된 지속 시간에 대한 요소가 표시된 후 다음 값으로 이동합니다. |

다음 예는 속성 미리보기와 함께 애플리케이션 구성 요소를 임베드하는 방법을 보여 줍니다.

![add_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>아래 각 구성 요소의 속성을 보려면 위의 예를 참조하십시오.

### 채널 {#channel}

**채널** 구성 요소를 사용하여 프로젝트에 전체 채널을 추가할 수 있습니다.

채널 구성 요소에는 다음과 같은 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>채널 경로</em></strong></td>
   <td>응용 프로그램이 있는 이 절대 경로를 선택하십시오.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>기간(밀리초)</em></strong></td>
   <td>채널의 전체 지속 시간을 선택합니다. 지속 시간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행함을 나타냅니다.</td>
  </tr>
 </tbody>
</table>

### 임베디드 페이지 {#embedded-page}

**포함된 페이지**&#x200B;를 사용하면 포함된 페이지를 프로젝트에 추가할 수 있습니다. 예를 들어 웹 애플리케이션이나 제품 카탈로그일 수 있습니다.

임베드된 페이지에는 다음 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>페이지 경로<br /> </em></strong></td>
   <td>채널이 있는 이 절대 경로를 선택하십시오.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>기간(밀리초)</em></strong></td>
   <td>채널의 전체 지속 시간을 선택합니다. 지속 시간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행함을 나타냅니다.</td>
  </tr>
 </tbody>
</table>

### 임베디드 시퀀스 {#embedded-sequence}

>[!NOTE]
>
>포함된 시퀀스에 대한 자세한 내용은 Screens 작성 섹션 아래의 [포함된 시퀀스](embedded-sequences.md)를 참조하십시오.

포함된 시퀀스를 사용하면 다른 에셋과 함께 기존 채널 내에 포함된 시퀀스 채널을 추가할 수 있습니다.

포함된 시퀀스에는 다음과 같은 페이지 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>채널 경로</td>
   <td>채널에 포함할 시퀀스의 절대 경로를 선택하십시오.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>기간(밀리초)</em></strong></td>
   <td>채널의 전체 지속 시간을 선택합니다. 지속 시간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행함을 나타냅니다.</td>
  </tr>
  <tr>
   <td><strong><em>전략</em></strong></td>
   <td><strong>원본</strong> 또는 <strong>단일</strong>(으)로 설정하십시오. 값을 <strong>original</strong>(으)로 설정하면 부모 시퀀스의 각 주기마다 하위 시퀀스가 완전히 실행됩니다. 다른 가능한 값은 <strong>single</strong>입니다. 이러한 값은 각 실행 시 하위 시퀀스의 한 항목만 표시합니다. 예를 들어 첫 번째 루프의 첫 번째 항목과 두 번째 루프의 두 번째 항목이 있습니다.</td>
  </tr>
 </tbody>
</table>

### 동적 임베디드 시퀀스 {#dynamic-embedded-sequence}

동적 포함된 시퀀스를 사용하면 채널 역할의 경우를 제외하고 위에서 언급한 것과 유사한 시퀀스를 추가할 수 있습니다.

포함된 시퀀스에 대한 자세한 내용은 Screens 작성 섹션 아래의 [포함된 시퀀스](embedded-sequences.md)를 참조하십시오.

동적 포함 시퀀스에는 다음과 같은 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>채널 할당 역할</em></strong><br /> </td>
   <td>채널 역할을 입력하십시오.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>기간(밀리초)</em></strong></td>
   <td>채널의 전체 지속 시간을 선택합니다. 지속 시간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행함을 나타냅니다.</td>
  </tr>
  <tr>
   <td><strong><em>전략</em></strong></td>
   <td><strong>원본</strong> 또는 <strong>단일</strong>(으)로 설정하십시오. 값을 <strong>original</strong>(으)로 설정하면 부모 시퀀스의 각 주기마다 하위 시퀀스가 완전히 실행됩니다. 다른 가능한 값은 <strong>single</strong>입니다. 이러한 값은 각 실행 시 하위 시퀀스의 한 항목만 표시합니다. 예를 들어 첫 번째 루프의 첫 번째 항목과 두 번째 루프의 두 번째 항목이 있습니다.</td>
  </tr>
 </tbody>
</table>

### 경험 조각 {#experience-fragment}

경험 조각을 사용하면 경험 조각(페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹)을 AEM Screens 채널에 추가할 수 있습니다. 구성 요소를 AEM 편집기로 드래그하여 놓고 경험 조각을 클릭합니다.

경험 조각을 만들어 AEM Screens 프로젝트에 적용하는 방법에 대한 자세한 내용은 [경험 조각 사용](experience-fragments-in-screens.md)을 참조하세요.

![만료](assets/exp.gif)

| **속성** | **설명** |
|---|---|
| **경험 조각** |
| ***경험 조각*** | 경험 조각을 선택합니다. |
| ***기간*** | 채널에서 재생되는 경험 조각의 전체 지속 시간을 선택합니다. |
| **오프라인 구성** |
| ***클라이언트측 라이브러리*** | JavaScript 및 CSS 파일. |
| ***정적 파일*** | 경험 조각에 오프라인 구성으로 추가할 수 있는 정적 파일입니다. |

>[!NOTE]
>
>이 구성 요소에서 추가하는 **클라이언트측 라이브러리** 및 **정적 파일**&#x200B;은(는) 이미 구성된 **클라이언트측 라이브러리** 및 경험 조각의 **속성**&#x200B;에서 추가된 정적 파일에 추가됩니다.

### 이미지 {#image}

이미지 를 사용하면 채널에 이미지를 추가할 수 있습니다.

이미지 에셋에는 **이미지**, **접근성** 및 **시퀀스**&#x200B;와 같은 세 개의 탭이 있습니다.

| **속성** | **설명** |
|---|---|
| **이미지** |
| ***이미지 자산*** | 이미지 자산을 클릭합니다. |
| ***제목*** | 이미지의 제목입니다. |
| ***링크 대상*** | 이미지에 링크를 추가합니다. |
| ***설명*** | 이미지에 대한 간략한 설명. |
| ***크기*** | 이미지 크기입니다. |
| **접근성** |
| ***대체 텍스트*** | 이미지에 대한 대체 텍스트입니다. |
| **시퀀스** |
| ***기간*** | 기본적으로 기간은 *8,000밀리초*(으)로 설정됩니다. 이미지의 재생 시간을 변경하려면 **Duration** 필드를 업데이트하십시오. |

### 전환 {#transition}

전환 구성 요소를 사용하여 Screens 프로젝트에 전환을 추가할 수 있습니다.

다음 이미지는 편집기에 대한 전환 구성 요소(끌어서 놓기 방식으로 추가됨)를 보여 줍니다.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

전환 아이콘을 클릭하고 **구성**(렌치 아이콘)을 클릭하여 **전환** 대화 상자를 엽니다. 이 대화 상자에는 세 개의 탭이 있습니다.

* **전환**
* **시퀀스**
* **활성화**

>[!NOTE]
>
>기본적으로 이 시퀀스는 600밀리초로 설정됩니다. **시퀀스** 탭을 사용하여 전환 시퀀스를 다른 값으로 업데이트할 수 있습니다.

![전환](assets/transition.gif)

전환 구성 요소에는 다음과 같은 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>전환</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>유형</em></strong></td>
   <td><p>이전과 이후 요소 사이의 전환 유형입니다. <strong>Type</strong> 전환에는 다음 옵션이 포함됩니다.</p>
    <ul>
     <li><strong>기본</strong></li>
     <li><strong>페이드</strong></li>
     <li><strong>오른쪽에서 안쪽으로 슬라이드</strong></li>
     <li><strong>왼쪽에서 안쪽으로 슬라이드</strong></li>
     <li><strong>맨 위에서 안쪽으로 슬라이드</strong></li>
     <li><strong>맨 아래에서 안쪽으로 슬라이드</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>시퀀스</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>기간</em></strong></td>
   <td>전환의 전체 기간을 선택합니다. 기본적으로 600밀리초로 설정됩니다.</td>
  </tr>
  <tr>
   <td><strong>활성화</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>활성 시작일</em></strong></td>
   <td>전환이 활성화될 수 있는 시기를 설명하는 타임스탬프입니다.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>활성 종료일</em></strong></td>
   <td>타임스탬프는 전환이 활성화될 때까지를 설명합니다.</td>
  </tr>
  <tr>
   <td><strong><em>일정</em></strong></td>
   <td>사전 정의된 일정을 추가합니다.</td>
  </tr>
 </tbody>
</table>

### 비디오 {#video}

비디오 구성 요소를 사용하여 Screens 프로젝트에 비디오를 추가할 수 있습니다.

비디오 구성 요소에는 다음과 같은 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><em><strong>비디오 자산</strong></em></td>
   <td>비디오 링크를 클릭합니다.</td>
  </tr>
  <tr>
   <td><em><strong>기간</strong></em></td>
   <td>비디오 지속 시간을 선택합니다. 기본적으로 duration은 -1로 설정되어 있으며, 이는 요소가 영원히 실행됨을 의미합니다. duration 값을 0보다 높게 설정하면 지정된 duration에 대한 요소가 표시된 후 다음 값으로 이동합니다.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>렌더링</strong></em></td>
   <td><p>비디오 종횡비가 화면에 맞지 않으면 <strong>contain</strong> 또는 <strong>cover</strong> 중 하나로 렌더링을 조정할 수 있습니다.</p> <p><em>포함</em>은(는) 전체 비디오가 표시되고 누락된 영역이 검정색 테두리로 채워져 있음을 의미합니다.</p> <p><em>Cover</em>은(는) 비디오가 전체 뷰포트를 포함하지만 측면에 오버플로된 일부 부분이 숨겨져 있음을 의미합니다.</p> </td>
  </tr>
  <tr>
   <td><em><strong>크기</strong></em></td>
   <td>비디오 크기입니다.</td>
  </tr>
 </tbody>
</table>
