---
title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
seo-title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---


# 다중 영역 레이아웃용 사용자 정의 템플릿 만들기 {#creating-custom-templates-multizone}

이 페이지에서는 다중 영역 레이아웃에 대한 사용자 정의 템플릿을 만드는 방법을 보여 줍니다.

## 중요 고려 사항 {#considerations}

다중 영역 레이아웃에서 사용자 정의 템플릿을 만들기 전에 알아야 할 중요한 2가지 고려 사항이 있습니다.

1. **픽셀 크기 또는 백분율을 수정했습니다**.

   사용자 정의 레이아웃에 대해 서로 다른 영역에 고정 픽셀 크기를 사용할지 또는 백분율을 사용하여 사용자 정의 레이아웃을 만들지를 결정해야 합니다.

   >[!NOTE]
   >비율을 사용하여 사용자 정의 레이아웃의 영역을 설정할 수 있으므로 다양한 화면 크기에서 템플릿을 다시 사용할 수 있습니다.

1. **이름 지정 규칙**:

   AEM Screens 프로젝트에서 사용할 사용자 정의 다중 영역 템플릿을 만드는 방법을 이해하려면 먼저 만들려는 템플릿의 버전을 이해하는 것이 좋습니다.

   | **레이아웃 이름** | **설명** |
   |---|---|
   | Left20-LandscapeHD3Zone | 가로 및 세로 화면의 20%로 영역 1을 왼쪽에서 가로 및 세로 화면의 20%로, 영역 2를 가로 화면의 80%로, 세로 화면의 오른쪽 정렬의 20%로, 영역 3을 가로 100%로, 세로 화면의 80%로, 세로 비율이 16:9인 세로 화면을 만들 수 있는 3영역 가로 레이아웃을 나타냅니다. |
   | Upper20-PortraitHD2Zone | 16:9의 종횡비로 화면의 20%를 맨 위에서 포함하는 2존 세로 템플릿을 나타냅니다. |
   | Right20-LandscapeSD3Zone | 4:3 종횡비로 화면의 20%를 오른쪽에서 차지하는 3영역 템플릿을 나타냅니다. |

   >[!IMPORTANT]
   >사용자 정의 레이아웃 내에 정의된 영역이 전체 레이아웃의 전체 종횡비와 일치하지 않을 수 있습니다. 이 문서에서 이어지는 이름 지정 규칙은 사용자 정의 레이아웃의 종횡비를 전체적으로 지정합니다.

## 사용 사례 Left20-LandscapeHD3Zone 레이아웃 {#custom-template-one} 예

다음 구성을 사용하여 사용자 지정 템플릿 *Left20-LandscapeHD3Zone*&#x200B;을(를) 만들려면 아래 섹션을 따르십시오.

* **Left20** 은 가로 및 세로 화면 크기의 20%를 포함하는 왼쪽 위의 영역을 나타냅니다.
* **가로** 는 화면 방향을 나타냅니다.
* **HD** 는 종횡비를 16:9로 나타냅니다.
* **3** Zoneyes는 디스플레이의 3개 영역을 나타냅니다.

## 다중 영역 레이아웃의 시각적 표현 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone 레이아웃을 사용하면 프로젝트에 다음과 같은 다중 영역 레이아웃을 만들 수 있습니다.

![이미지](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Left20-LandscapeHD3Zone 레이아웃 만들기 {#landscape-layout-one}

AEM Screens 프로젝트에 대한 Left20-LandscapeHD3Zone 레이아웃을 만들려면 아래 절차를 따르십시오.

1. **customtemplate**&#x200B;이라는 이름의 AEM Screens 프로젝트를 만듭니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. AEM 인스턴스 —> 도구 —> **CRXDE Lite**&#x200B;에서 **CRXDE Lite**&#x200B;으로 이동합니다.

1. **customtemplate**&#x200B;이라는 제목의 **apps** 아래에 폴더를 만듭니다. 마찬가지로, 아래 그림과 같이 **customtemplate** 아래에 **template**&#x200B;이라는 이름의 다른 폴더를 만드십시오.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >노드를 만들거나, 편집하거나, 복사할 때마다 CRXDE Lite의 작업 표시줄에서 **모두 저장**&#x200B;을 클릭하는 것이 좋습니다. 그렇지 않으면 업데이트를 커밋할 수 없습니다.

1. 왼쪽 막대 템플릿을 `/libs/screens/core/templates/splitscreenchannel/lbar-left`에서 `/apps/customtemplate/template`(으)로 복사합니다.

1. 복사한 **lbar-left**(`/apps/customtemplate/template`)의 이름을 **my-custom-layout**로 바꿉니다.
   ![이미지](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. `/apps/customtemplate/template/my-custom-layout`으로 이동하여 속성 **jcr:description**&#x200B;을 *Template for Left20-LandscapeHD3Zone* 및 **jcr:title**&#x200B;을 *Left20-LandscapeHD3Zone*&#x200B;으로 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`에서 **offline-config** 노드로 이동하고 **jcr:title** Left20-LandscapeHD3Zone *으로 업데이트합니다.*

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. `/apps/customtemplate/template/my-custom-layout/jcr:content`에서 **my-custom-template**&#x200B;의 *jcr:content* 속성으로 이동하고 **cq:cssClass** 속성을 **aem-Layout my-custom-layout**&#x200B;으로 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 왼쪽 막대 템플릿을 복사한 단계(4)를 참조하면 `my-custom-layout/jcr:content` 아래에 3개의 응답형 그리드를 볼 수 있습니다. *r1c1* 노드의 *cq:cssClass* 속성에 있는 각 응답형 격자에 사용자 지정 css 클래스를 추가합니다. 예를 들어 *my-custom-layout—top-left* for &lt;a4/> node.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template7.png)

   마찬가지로 *r1c2*&#x200B;에 대해 *my-custom-layout—top-right*, *my-custom-layout—bottom*&#x200B;을 *r2c1* 노드에 추가합니다.

   >[!NOTE]
   >이러한 사용자 정의 클래스는 css에서 이러한 응답형 그리드의 폭/높이를 설정하는 데 사용됩니다.

   >[!NOTE]
   >원하는 전체 격자 수에 따라 반응형 그리드를 추가하거나 제거할 수 있습니다. 이 예에서는 첫 번째 행에 2개의 격자를 표시하고 두 번째 행에 1개의 격자를 표시하므로 총 3개의 응답형 격자(r1c1, r1c2, r2c1)가 있습니다.

1. `/libs/settings/wcm/designs/screens`을(를) `/apps/settings/wcm/designs/`에 복사하고 복사한 디자인의 이름을 **custom-template-designs**&#x200B;으로 바꿉니다.

1. `/apps/settings/wcm/designs/custom-template-designs`으로 이동하여 **custom-template-designs**&#x200B;의 *jcr:title* 속성을 **customtemplate-design**&#x200B;으로 업데이트합니다.

1. `/apps/settings/wcm/designs/custom-template-designs`으로 이동하여 static.css 파일을 만듭니다.

1. 내용을 `static.css` 파일에 복사합니다.

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
   >사용자 지정 템플릿의 요구 사항에 맞게 비율을 업데이트할 수 있습니다.

1. `/apps/<project>/templates/my-custom-layout/jcr:content`으로 이동하고 *cq:designPath* 속성을 `/apps/settings/wcm/designs/customtemplate-designs`으로 업데이트하여 static.css에 구성된 스타일을 로드합니다.

   >[!NOTE]
   >복사 또는 붙여넣기가 아니라 모든 스타일을 입력하는 것이 좋습니다. 이렇게 하면 공백에 css 스타일 문제가 발생할 수 있습니다.

## 결과 보기 {#viewing-result}

AEM Screens 프로젝트에서 위의 사용자 정의된 템플릿을 사용하려면 아래 절차를 따르십시오.

1. (1) 단계에서 만든 스크린 프로젝트로 이동하고 **채널** 폴더를 선택합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 작업 표시줄에서 **만들기**&#x200B;를 클릭하고 **만들기** 마법사에서 **Left20-LandscapeHD3Zone** 템플릿을 선택합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 사용자 정의된 템플릿으로 채널을 만든 후에는 편집기에서 채널에 자산을 추가할 수 있습니다. 다음 미리 보기는 사용자 정의 템플릿의 이미지를 보여 줍니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 배경 레이어 {#inserting-image}으로 이미지 삽입

이미지를 레이아웃에 배경 레이어로 삽입할 수 있습니다.

CSS 규칙을 조정하여 CSS 파일에서 &quot;data-uri&quot;라고 하는 항목을 사용하고 이미지(Base64 인코딩됨)를 바로 인라인(13단계), *static.css*&#x200B;에 만들 수 있습니다.

이 작업은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 수행할 수 있습니다.

1. 이미지가 채널에 대한 오프라인 구성에 어떻게든 포함되어 있는지 확인합니다.
1. 위의 CSS에서 &quot;data-uri&quot; 변형 대신 이미지에 대한 직접 링크를 사용합니다.


## 배경색 {#updating-color} 업데이트

배경색을 변경하려면 다음 코드를 xml 파일(13단계)인 *static.css*&#x200B;에 추가합니다.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



