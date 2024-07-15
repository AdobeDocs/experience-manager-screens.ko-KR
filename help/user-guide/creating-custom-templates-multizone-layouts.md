---
title: 다중 영역 레이아웃에서 사용자 지정 템플릿 만들기
description: AEM Screens용 다중 영역 레이아웃에서 사용자 지정 템플릿을 만드는 방법에 대해 알아봅니다.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---

# 다중 영역 레이아웃에 대한 사용자 지정 템플릿 만들기 {#creating-custom-templates-multizone}

이 페이지에서는 다중 영역 레이아웃에 대한 사용자 지정 템플릿을 만드는 방법을 보여 줍니다.

## 중요 고려 사항 {#considerations}

다중 영역 레이아웃에서 사용자 지정 템플릿을 만들기 전에 알아 두어야 할 두 가지 중요한 고려 사항이 있습니다.

1. **고정 픽셀 크기 또는 백분율**:

   사용자 지정 레이아웃에 대해 서로 다른 영역에 대해 고정된 픽셀 크기를 사용할지 또는 백분율을 사용하여 사용자 지정 레이아웃을 만들지 여부를 결정합니다.

   >[!NOTE]
   >백분율을 사용하여 사용자 정의 레이아웃의 영역을 설정할 수 있다는 이점은 다양한 화면 크기에서 템플릿을 재사용할 수 있도록 해줍니다.

1. **명명 규칙**:

   AEM Screens 프로젝트에서 사용할 사용자 지정 다중 영역 템플릿을 만드는 방법을 이해하는 데 도움이 됩니다. 그러나 먼저 만들려는 템플릿의 버전을 이해해야 합니다.

   | **레이아웃 이름** | **설명** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 세 개의 영역을 만들 수 있는 세 개의 영역 가로 레이아웃입니다. <br>* 영역 1은 왼쪽에서 가로 및 세로 화면의 20%입니다.<br>* 영역 2는 가로 화면의 80%이고 세로 화면의 20%는 오른쪽 정렬<br>* 영역 3은 가로 화면의 100%이고 세로 화면의 80%입니다. 종횡비는 16:9입니다. |
   | `Upper20-PortraitHD2Zone` | 16:9의 화면 비율과 함께 맨 위에서 화면의 20%를 차지하는 2영역 세로 템플릿입니다. |
   | `Right20-LandscapeSD3Zone` | 오른쪽에서 화면의 20%를 덮고 종횡비가 4:3인 3영역 템플릿 |

   >[!IMPORTANT]
   >사용자 지정 레이아웃 내에 정의된 영역이 전체 레이아웃의 전체 종횡비와 일치하지 않을 수 있습니다. 이 문서에서 따르는 명명 규칙은 전체적으로 사용자 정의 레이아웃의 종횡비를 지정합니다.

## 사용 사례 `Left20-LandscapeHD3Zone` 레이아웃 예 {#custom-template-one}

다음 구성으로 사용자 지정 템플릿 *`Left20-LandscapeHD3Zone`*&#x200B;을(를) 만들려면 아래 섹션을 따르십시오.

* **`Left20`** - 왼쪽 상단 영역에 가로 및 세로 화면 크기의 20%가 표시됩니다.
* **`Landscape`** - 화면 방향.
* **`HD`** - 종횡비는 16:9입니다.
* **`3Zone`** - 디스플레이의 세 영역.

## 다중 영역 레이아웃의 시각적 표현 {#multi-layout-visual-one}

`Left20-LandscapeHD3Zone` 레이아웃을 사용하면 프로젝트에서 다음 다중 영역 레이아웃을 만들 수 있습니다.

![이미지](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## `Left20-LandscapeHD3Zone` 레이아웃 만들기 {#landscape-layout-one}

AEM Screens 프로젝트에 대한 `Left20-LandscapeHD3Zone` 레이아웃을 만들려면 아래 단계를 따르십시오.

1. 제목이 **`customtemplate`**(으)로 지정된 AEM Screens 프로젝트를 만듭니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. AEM 인스턴스 > 도구 > **CRXDE Lite**&#x200B;에서 **CRXDE Lite**(으)로 이동합니다.

1. **`customtemplate`**(으)로 제목이 **apps**&#x200B;인 폴더를 만드십시오. 마찬가지로 아래 그림과 같이 **`customtemplate`** 아래에 **template**(으)로 제목이 지정된 다른 폴더를 만듭니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >콘텐츠를 만들거나 편집하거나 노드에 복사할 때마다 CRXDE Lite의 작업 표시줄에서 **모두 저장**&#x200B;을 클릭합니다. 그렇지 않으면 업데이트를 커밋할 수 없습니다.

1. 왼쪽 막대 서식 파일을 `/libs/screens/core/templates/splitscreenchannel/lbar-left`에서 `/apps/customtemplate/template`(으)로 복사합니다.

1. 복사된 **lbar-left**(`/apps/customtemplate/template`)의 이름을 **my-custom-layout**(으)로 바꾸십시오.
   ![이미지](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. `/apps/customtemplate/template/my-custom-layout`(으)로 이동하고 `Left20-LandscapeHD3Zone`*및&#x200B;**`jcr:title`**에 대한&#x200B;**`jcr:description`**속성을*&#x200B;템플릿으로 *`Left20-LandscapeHD3Zone`*(으)로 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`에서 **`offline-config`** 노드로 이동하여 **`jcr:title`**&#x200B;을(를) *`Left20-LandscapeHD3Zone`*(으)로 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content`에서 **my-custom-template**&#x200B;의 *`jcr:content`* 속성으로 이동하고 **aem-Layout my-custom-layout**&#x200B;을 사용할 수 있도록 **`cq:cssClass`** 속성을 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 막대 왼쪽 템플릿을 복사한 단계 (4)를 참조하면 `my-custom-layout/jcr:content`에서 3개의 응답형 그리드를 볼 수 있습니다. *`cq:cssClass`* 속성의 각 응답형 격자에 사용자 지정 css 클래스(예: *r1c1* 노드의 *my-custom-layout-top-left*)를 추가하십시오.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template7.png)

   마찬가지로 *r1c2*&#x200B;의 경우 *my-custom-layout-top-right*&#x200B;을, *r2c1* 노드의 경우 *my-custom-layout-bottom*&#x200B;을 추가하십시오.

   >[!NOTE]
   >이러한 사용자 정의 클래스는 css에서 이러한 응답형 그리드의 너비/높이를 설정하는 데 사용됩니다.

   >[!NOTE]
   >원하는 총 격자선 수에 따라 응답형 격자선을 추가하거나 제거할 수 있습니다. 이 예에서는 첫 번째 행의 2개의 격자와 두 번째 행의 1개의 격자가 표시되어 총 3개의 응답형 격자(r1c1, r1c2, r2c1)가 있다.

1. `/libs/settings/wcm/designs/screens`을(를) `/apps/settings/wcm/designs/`에 복사하고 복사된 디자인의 이름을 **사용자 지정-템플릿-디자인**(으)로 바꾸십시오.

1. `/apps/settings/wcm/designs/custom-template-designs`(으)로 이동하여 **사용자 지정 템플릿 디자인**&#x200B;의 속성 *`jcr:title`*&#x200B;을(를) **사용자 지정 템플릿 디자인**(으)로 업데이트합니다.

1. `/apps/settings/wcm/designs/custom-template-designs`(으)로 이동하여 static.css 파일을 만듭니다.

1. `static.css` 파일에 콘텐츠 복사:

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >사용자 지정 템플릿에 대한 요구 사항과 일치하도록 백분율을 업데이트할 수 있습니다.

1. static.css에 구성된 스타일을 로드할 수 있도록 `/apps/<project>/templates/my-custom-layout/jcr:content`(으)로 이동하고 *`cq:designPath`* 속성을 `/apps/settings/wcm/designs/customtemplate-designs`(으)로 업데이트합니다.

   >[!NOTE]
   >복사 또는 붙여넣기가 아닌 모든 스타일을 입력하면 공백이 발생하여 css 스타일 문제가 발생할 수 있습니다.

## 결과 보기 {#viewing-result}

AEM Screens 프로젝트에서 위의 사용자 지정 템플릿을 사용하려면 아래 단계를 따르십시오.

1. (1)단계에서 만든 Screens 프로젝트로 이동하여 **채널** 폴더를 클릭합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭하고 **만들기** 마법사에서 템플릿 **`Left20-LandscapeHD3Zone`**&#x200B;을(를) 클릭합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 맞춤화된 템플릿으로 채널을 만든 후 편집기에서 채널에 에셋을 추가할 수 있습니다. 다음 미리 보기는 사용자 지정 템플릿의 이미지를 보여 줍니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 이미지를 배경 레이어로 삽입 {#inserting-image}

레이아웃에 이미지를 배경 레이어로 삽입할 수 있습니다.

&quot;data-uri&quot;를 사용하도록 CSS 규칙을 조정하고 (13단계), *static.css*&#x200B;에서 만든 CSS 파일에서 이미지(`Base64` 인코딩)를 직접 인라인할 수 있습니다.

이러한 배열은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 따를 수 있습니다.

1. 이미지가 채널의 오프라인 구성에 어떻게든 포함되어 있는지 확인합니다.
1. &quot;data-uri&quot; 변형 대신 위의 CSS에서 이미지에 대한 직접 링크를 사용하십시오.


## 배경색 업데이트 중 {#updating-color}

배경색을 변경하려면 xml 파일(*static.css*)에 다음 코드를 추가하십시오.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
