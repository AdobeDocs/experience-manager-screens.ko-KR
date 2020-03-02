---
title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
seo-title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 9e3f26e10a5168511b2bf138f8ce36b94778b339

---


# 다중 영역 레이아웃용 사용자 정의 템플릿 만들기 {#creating-custom-templates-multizone}

이 페이지에서는 다중 영역 레이아웃용 사용자 정의 템플릿을 만드는 방법을 보여줍니다.

## 중요 고려 사항 {#considerations}

다중 영역 레이아웃에서 사용자 지정 템플릿을 만들기 전에 알아야 하는 두 가지 중요한 고려 사항이 있습니다.

1. **픽셀 크기 또는 백분율**&#x200B;수정:

   사용자 정의 레이아웃에 대해 서로 다른 영역에 대해 고정 픽셀 크기를 사용할지 또는 백분율을 사용하여 사용자 정의 레이아웃을 만들지 여부를 결정해야 합니다.

   > [!NOTE]
   > 비율을 사용하여 사용자 정의 레이아웃의 영역을 설정할 수 있으므로 다양한 화면 크기에 템플릿을 다시 사용할 수 있습니다.

1. **이름 지정 규칙**:

   AEM Screens 프로젝트에서 사용할 사용자 지정 다중 영역 템플릿을 만드는 방법을 이해하려면 먼저 만들려는 템플릿의 버전을 이해하는 것이 좋습니다.

   | **레이아웃 이름** | **설명** |
   |---|---|
   | Left20-LandscapeHD3Zone | 가로 및 세로 화면의 20%, 영역 2를 가로 및 세로 화면의 80%로, 세로 화면의 20%로, 영역 3을 가로 및 세로 화면의 20%로, 영역 3을 가로 100%로, 세로 화면의 80%로 16:9 비율로 만들 수 있는 3존 가로 레이아웃을 말합니다. |
   | Upper20-PortraitHD2Zone | 16:9의 종횡비를 사용하여 화면의 20%를 맨 위에서 처리하는 2존 세로 템플릿을 나타냅니다. |
   | Right20-LandscapeSD3Zone | 화면상의 20%를 오른쪽에서 차지하는 3영역 템플릿을 나타냅니다(종횡비 4:3). |

   > [!IMPORTANT]
   > 사용자 지정 레이아웃 내에 정의된 영역이 전체 레이아웃의 전체 종횡비와 일치하지 않을 수 있습니다. 이 문서에서 수행한 이름 지정 규칙은 사용자 지정 레이아웃의 종횡비를 전체적으로 지정합니다.

## 사용 사례 Left20-LandscapeHD3영역 레이아웃 예 {#custom-template-one}

아래 섹션에 따라 다음 구성으로 사용자 정의 템플릿 *Left20-LandscapeHD* 3Zone을 만듭니다.

* **Left20은** 가로 및 세로 화면 크기의 20%를 덮는 왼쪽 위 영역을 나타냅니다.
* **가로는** 화면 방향을 나타냅니다.
* **HD는** 종횡비를 16:9로 나타냅니다.
* **3Zone** 은 디스플레이의 세 영역을 나타냅니다.

## 다중 영역 레이아웃의 시각적 표현 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone 레이아웃을 사용하면 프로젝트에 다음과 같은 다중 영역 레이아웃을 만들 수 있습니다.

![이미지](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## Left20-LandscapeHD3Zone 레이아웃 만들기 {#landscape-layout-one}

아래 절차에 따라 AEM Screens 프로젝트에 대한 Left20-LandscapeHD3Zone 레이아웃을 만드십시오.

1. AEM Screens 프로젝트를 **사용자 지정 템플릿으로**&#x200B;만듭니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. AEM **인스턴스 —> 도구** —> CRXDE Lite로 **이동합니다**.

1. 사용자 **정의 템플릿으로** 제목이 있는 앱 ****&#x200B;아래에 폴더를 만듭니다. 마찬가지로, 아래 그림과 같이 **사용자 지정 템플릿** 아래에 템플릿으로 ****&#x200B;명명된 다른 폴더를 만듭니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > CRXDE Lite **의 작업 표시줄에서 컨텐츠를 작성, 편집 또는 노드에 복사할 때마다 [모두** 저장]을 클릭하는 것이 좋습니다. 그렇지 않으면 업데이트를 커밋할 수 없습니다.

1. 왼쪽 막대 템플릿을 에서 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 로 `/apps/customtemplate/template`복사합니다.

1. 복사한 **왼쪽** (`/apps/customtemplate/template`)의 이름을 **내 사용자 지정 레이아웃으로**변경합니다.
   ![이미지](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Left20- `/apps/customtemplate/template/my-custom-layout` LandscapeHD3Zone에 대한 속성 **jcr:description** to *Template and* jcr:title **** ** toLeft20-LandscapeHD3Zone으로 이동하고 업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 에서 **offline-config** 노드로 이동하고 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` jcr:title **을 Left20-** LandscapeHD3Zone으로 업데이트합니다 **.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 에서 *my-custom-template* 의 **jcr:content** 속성으로 `/apps/customtemplate/template/my-custom-layout/jcr:content` 이동하고 cq:cssClass **속성을 aem-Layout my-custom-layout에** ****&#x200B;업데이트합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. (4) 단계를 참조하여 왼쪽 상단의 템플릿을 복사하면 아래 3개의 응답형 격자를 볼 수 `my-custom-layout/jcr:content`있습니다. 사용자 지정 css 클래스를 cq:cssClass *속성(예:* my-custom-layout *)의 각 응답형* 격자에 *추가합니다(* r1c1노드에 대한 왼쪽 위).

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template7.png)

   마찬가지로 *my-custom-layout—* r1c2의 경우 오른쪽 *맨 위,* my-custom-layout—home *for r2c1* node ** 를 추가합니다.

   >[!NOTE]
   >이러한 사용자 정의 클래스는 css에서 반응형 그리드의 폭/높이를 설정하는 데 사용됩니다.

   >[!NOTE]
   > 원하는 전체 격자 수를 기반으로 응답형 그리드를 추가하거나 제거할 수 있습니다. 이 예에서는 첫 번째 행에 2개의 격자를 표시하고 두 번째 행에 1개의 격자를 표시하므로 총 3개의 응답형 격자(r1c1, r1c2, r2c1)가 있습니다.

1. 복사한 디자인을 `/libs/settings/wcm/designs/screens` 복사하여 `/apps/settings/wcm/designs/` 맞춤형 템플릿 디자인으로 ****&#x200B;이름을 변경합니다.

1. 사용자 정의 템플릿 디자인의 `/apps/settings/wcm/designs/custom-template-designs` jcr:title *속성으로* 이동하여 **사용자 정의 템플릿 디자인을** 업데이트합니다 ****.

1. static.css 파일로 이동하여 `/apps/settings/wcm/designs/custom-template-designs` 만듭니다.

1. 정적.css 파일에 컨텐츠를 복사합니다.

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
   > 사용자 지정 템플릿의 요구 사항에 맞게 비율을 업데이트할 수 있습니다.

1. cq:designPath 속성을 `/apps/<project>/templates/my-custom-layout/jcr:content` 탐색하고 업데이트하여 *static.css* 로 구성된 스타일을 `/apps/settings/wcm/designs/customtemplate-designs` 로드합니다.

   >[!NOTE]
   > 복사 또는 붙여넣기가 아닌 모든 스타일을 입력할 것을 권장합니다. 그러면 공백으로 인해 css 스타일 문제가 발생할 수 있습니다.

## 결과 보기 {#viewing-result}

AEM Screens 프로젝트에서 위의 사용자 지정 템플릿을 사용하려면 아래 절차를 따르십시오.

1. (1) 단계에서 만든 스크린 프로젝트로 이동하고 채널 **폴더를 선택합니다** .

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 작업 **표시줄에서** 만들기를 클릭하고 만들기 **마법사에서 Left20-LandscapeHD3Zone** 템플릿을 **선택합니다** .

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 사용자 지정 템플릿으로 채널을 만든 후에는 편집기에서 채널에 자산을 추가할 수 있습니다. 다음 미리 보기는 사용자 정의 템플릿의 이미지를 보여줍니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 배경 레이어로 이미지 삽입 {#inserting-image}

이미지를 배경 레이어로 레이아웃에 삽입할 수 있습니다.

CSS 규칙을 조정하여 &quot;data-uri&quot;라고 하는 항목을 사용하고 CSS 파일에서 직접 이미지(Base64 인코딩)를 인라인(13단계)하고 *static.css*&#x200B;로 만들 수 있습니다.

이 작업은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 따를 수 있습니다.

1. 이미지가 채널에 대한 오프라인 구성에 어떻게 포함되었는지 확인합니다.
1. 위의 CSS에서 &quot;data-uri&quot; 변형 대신 이미지에 대한 직접 링크 사용


## 배경색 업데이트 {#updating-color}

배경색을 변경하려면 다음 코드를 xml 파일(13단계)에 *static.css*&#x200B;추가합니다.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



