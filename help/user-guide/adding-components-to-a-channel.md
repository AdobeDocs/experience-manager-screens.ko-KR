---
title: 채널에 구성 요소 추가
seo-title: 채널에 구성 요소 추가
description: AEM Screens 프로젝트에서 채널에 구성 요소를 추가하는 방법에 대해 자세히 알려면 이 페이지를 따르십시오.
seo-description: AEM Screens 프로젝트에서 채널에 구성 요소를 추가하는 방법에 대해 자세히 알려면 이 페이지를 따르십시오.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: cec2a2f8b056bf713e56a9fab08d88e29263820b

---


# 채널에 구성 요소 추가{#adding-components-to-a-channel}

구성 요소는 AEM(Adobe Experience Manager) 경험의 기본 요소입니다. 다양한 구성 요소를 사용하여 AEM Screens 프로젝트에서 채널에 구성 요소를 추가할 수 있습니다.

## AEM Screens의 구성 요소 {#components-in-aem-screens}

AEM Screens에서는 스크린 프로젝트에서 사용할 수 있는 다양한 AEM 구성 요소를 제공합니다.

### AEM Screens 구성 요소 보기 {#viewing-aem-screens-components}

AEM Screens 프로젝트를 만들 때마다 프로젝트에 추가할 수 있는 기본 구성 요소 목록이 표시됩니다.

스크린 프로젝트에 추가할 수 있는 기본 구성 요소를 보려면 아래 절차를 따르십시오.

1. 채널을 선택하십시오. 예: **We.Retail In Store** --&gt; **채널** --&gt; **유휴 채널**.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 AEM 편집기를 엽니다.
1. 사이드바에서 **+** 아이콘을 클릭하여 구성 요소를 엽니다.
1. 아래 그림처럼 AEM Screens 프로젝트에 기본적으로 포함된 모든 구성 요소가 표시됩니다.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 새 구성 요소 추가 {#adding-a-new-component}

AEM에서는 다양한 다른 구성 요소도 제공합니다. AEM Screens와 호환되는 경우 항상 프로젝트에 다른 구성 요소(기본적으로 포함되지는 않음)도 추가할 수 있습니다.

다음 예에서는 AEM Screens 프로젝트에 Livefyre 구성 요소를 추가하는 것을 보여줍니다.

1. 새 구성 요소를 추가할 채널을 선택합니다. 예: **We.Retail In Store** --&gt; **채널** --&gt; **유휴 채널**.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.
1. **디자인** 모드를 선택합니다.
1. 오른쪽에 있는 전체 디자인 편집기를 선택하고 설정 기호를 클릭하여 **ParSys 디자인** 대화 상자를 엽니다.
1. AEM Screens 프로젝트에 가져오려는 구성 요소를 선택할 수 있습니다. 다음 예에서는 AEM Screens 프로젝트에 **Livefyre** 구성 요소를 추가하는 것을 보여줍니다.

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>유사하게, 프로젝트에 AEM Screens와 호환하는 다른 새 구성 요소를 원하는 개수만큼 추가할 수 있습니다.

## AEM Screens 구성 요소 이해 {#understanding-aem-screen-components}

다음 섹션에서는 프로젝트에서 사용할 수 있는 AEM Screens 구성 요소에 대해 설명합니다.

>[!NOTE]
>
>구성 요소의 속성을 보려면 구성 요소를 선택하고 망치 아이콘을 클릭하십시오.

### 애플리케이션 {#application}

**애플리케이션** 구성 요소를 사용하면 채널에 애플리케이션을 추가할 수 있습니다.

애플리케이션 구성 요소에는 다음 속성이 있습니다.

| **속성** | **설명** |
|---|---|
| ***애플리케이션 경로*** | 애플리케이션이 존재하는 절대 경로를 선택합니다. |
| ***지속 시간(ms)*** | 애플리케이션의 지속 기간을 선택합니다. 기본적으로 지속 시간은 -1로 설정되므로 요소는 영구적으로 실행됩니다(즉, 단일 페이지 애플리케이션). 지속 기간 값을 0보다 크게 설정하면 지정된 지속 기간의 요소를 표시한 후 다음 항목으로 이동합니다. |

다음 예에서는 해당 속성의 미리 보기와 함께 애플리케이션 구성 요소를 포함하는 방법을 보여줍니다.

![adding_components응용 프로그램](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>아래의 각 구성 요소에 대한 속성을 보려면 위의 예를 참조하십시오.

### 채널 {#channel}

**채널** 구성 요소를 사용하면 전체 채널을 프로젝트에 추가할 수 있습니다.

채널 구성 요소에는 다음 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>채널 경로</em></strong></td>
   <td>애플리케이션이 존재하는 이 절대 경로를 선택합니다.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>지속 시간(ms)</em></strong></td>
   <td>채널의 전체 지속 기간을 선택합니다. 지속 기간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행하게 됩니다.</td>
  </tr>
 </tbody>
</table>

### 임베딩된 페이지 {#embedded-page}

**포함된 페이지**&#x200B;를 사용하면 포함된 페이지를 프로젝트에 추가할 수 있습니다. 예를 들어, 웹 애플리케이션이나 제품 카탈로그가 될 수 있습니다.

포함된 페이지에는 다음 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>페이지 경로<br /> </em></strong></td>
   <td>채널이 존재하는 이 절대 경로를 선택합니다.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>지속 시간(ms)</em></strong></td>
   <td>채널의 전체 지속 기간을 선택합니다. 지속 기간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행하게 됩니다.</td>
  </tr>
 </tbody>
</table>

### 포함된 시퀀스 {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

포함된 시퀀스를 사용하면 기존 채널 내부의 포함된 시퀀스 채널을 추가할 수 있습니다(기타 자산 포함).

포함된 시퀀스에는 다음 페이지 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>채널 경로</td>
   <td>채널에 포함할 시퀀스의 절대 경로를 선택합니다.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>지속 시간(ms)</em></strong></td>
   <td>채널의 전체 지속 기간을 선택합니다. 지속 기간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행하게 됩니다.</td>
  </tr>
  <tr>
   <td><strong><em>전략</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### 동적 포함된 시퀀스 {#dynamic-embedded-sequence}

동적 포함된 시퀀스를 사용하면 채널 역할에 의한 경우를 제외하고 위에서 언급한 것과 유사한 시퀀스를 추가할 수 있습니다.

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

동적 포함된 시퀀스에는 다음 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong><em>채널 지정 역할</em></strong><br /> </td>
   <td>채널 역할을 입력합니다.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>지속 시간(ms)</em></strong></td>
   <td>채널의 전체 지속 기간을 선택합니다. 지속 기간을 -1로 설정하면 포함된 채널이 특정 채널에서 전체 길이를 실행하게 됩니다.</td>
  </tr>
  <tr>
   <td><strong><em>전략</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### 경험 조각 {#experience-fragment}

경험 조각을 사용하면 경험 조각(페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹)을 AEM Screens 채널에 추가할 수 있습니다. 구성 요소를 AEM 편집기로 드래그하여 놓고 경험 조각을 선택합니다.

경험 조각을 만들어 AEM Screens 프로젝트에 활용하는 방법에 대한 자세한 내용은 경험 조각 [사용을 참조하십시오](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **속성** | **설명** |
|---|---|
| **경험 조각** |
| ***경험 조각*** | 경험 조각을 선택합니다. |
| ***기간*** | 채널에서 재생되는 경험 조각의 전체 지속 기간을 선택합니다. |
| **오프라인 구성** |
| ***클라이언트측 라이브러리*** | Javascript 및 CSS 파일. |
| ***정적 파일*** | 오프라인 구성으로 경험 조각에 추가할 수 있는 정적 파일입니다. |

>[!NOTE]
>
>클라이언트 **측** **** Libaries 및 **이 구성 요소에서 추가하는 Static Files는** 이미 구성된 **클라이언트 측** Libries와 경험의 Properties조각에서 추가된 Static Files구성 요소 이외에도추가됩니다.

### 이미지 {#image}

이미지를 사용하면 채널에 이미지를 추가할 수 있습니다.

이미지 자산에는 세 개의 탭, 다시 말해 **이미지**, **액세스 가능성** 및 **시퀀스** 탭이 있습니다.

| **속성** | **설명** |
|---|---|
| **이미지** |
| ***이미지 자산*** | 이미지 자산을 선택합니다. |
| ***제목*** | 이미지의 제목입니다. |
| ***링크 대상*** | 이미지에 링크를 추가합니다. |
| ***설명*** | 이미지에 대한 간단한 설명입니다. |
| ***크기*** | 이미지의 크기입니다. |
| **액세스 가능성** |
| ***대체 텍스트*** | 이미지의 대체 텍스트입니다. |
| **시퀀스** |
| ***기간*** | 기본적으로 지속 시간은 *8000ms*&#x200B;로 설정됩니다. 이미지의 재생 시간을 변경하려면 지속 시간 **필드를 업데이트합니다** . |

### 전환 {#transition}

전환 구성 요소를 사용하면 스크린 프로젝트에 전환 기능을 추가할 수 있습니다.

다음 이미지는 편집기에 대한 전환 구성 요소(드래그 앤 드롭을 통해 추가)를 보여줍니다.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

전환 아이콘을 선택하고 구성( **스패너** 아이콘)을 클릭하여 전환 **대화 상자를** 엽니다. 이 대화 상자에는 다음과 같은 세 개의 탭이 있습니다.

* **전환**
* **시퀀스**
* **활성화**

>[!NOTE]
>
>기본적으로 시퀀스는 600ms로 설정됩니다. [시퀀스] 탭을 사용하여 전환 시퀀스를 다른 값으로 업데이트할 **수** 있습니다.

![전환](assets/transition.gif)

전환 구성 요소에는 다음 속성이 있습니다.

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
   <td><p>전환 전 요소와 후 요소 간의 전환 유형입니다. 전환 <strong>유형에는</strong> 다음 옵션이 포함됩니다.</p>
    <ul>
     <li><strong>일반</strong></li>
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
   <td>전환의 전체 지속 기간을 선택합니다. 기본적으로 600ms로 설정됩니다.</td>
  </tr>
  <tr>
   <td><strong>활성화</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>활성 위치</em></strong></td>
   <td>전환이 활성 상태일 수 있는 시기를 설명하는 타임스탬프<br /> </td>
  </tr>
  <tr>
   <td><strong><em>활성</em></strong></td>
   <td>전환이 활성화될 때까지 설명하는 타임스탬프</td>
  </tr>
  <tr>
   <td><strong><em>예약</em></strong></td>
   <td>미리 정의된 일정을 추가합니다.</td>
  </tr>
 </tbody>
</table>

### 비디오 {#video}

비디오 구성 요소를 사용하면 스크린 프로젝트에 비디오 기능을 추가할 수 있습니다.

비디오 구성 요소에는 다음 속성이 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><em><strong>비디오 자산</strong></em></td>
   <td>비디오 링크를 선택합니다.</td>
  </tr>
  <tr>
   <td><em><strong>기간</strong></em></td>
   <td>비디오의 지속 기간을 선택합니다. 기본적으로 지속 시간은 -1로 설정되므로 요소는 영구적으로 실행됩니다. 지속 기간 값을 0보다 크게 설정하면 지정된 지속 기간의 요소를 표시한 후 다음 항목으로 이동합니다.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>렌더링</strong></em></td>
   <td><p>비디오 종횡비가 화면에 맞지 않는 경우, 렌더링을 <strong>포함</strong> 또는 <strong>커버</strong>로 조정할 수 있습니다.</p> <p><em>포함</em>은 전체 비디오가 표시되고 비디오가 없는 영역은 검은색 경계로 채워짐을 의미합니다.</p> <p><em>커버</em>는 비디오가 전체 뷰포트를 덮지만, 측면에서 화면을 넘치는 일부 부분은 표시되지 않습니다.</p> </td>
  </tr>
  <tr>
   <td><em><strong>크기</strong></em></td>
   <td>비디오의 크기입니다.</td>
  </tr>
 </tbody>
</table>

