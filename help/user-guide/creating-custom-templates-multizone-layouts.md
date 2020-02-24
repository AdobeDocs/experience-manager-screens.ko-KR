---
title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
seo-title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6a0967580d06e749db878d74aad2ffb1fec82f43

---


# 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기 {#creating-custom-templates-multizone}

이 페이지에서는 다중 영역 레이아웃에서 사용자 정의 템플릿을 만드는 방법을 보여줍니다.

## 이름 지정 규칙 {#name-terms}

AEM Screens 프로젝트에서 사용할 사용자 지정 다중 영역 템플릿을 만드는 방법을 이해하려면 먼저 만들려는 템플릿의 버전을 이해하는 것이 좋습니다.

| **레이아웃 이름** | **설명** |
|---|---|
| Left20-LandscapeHD3Zone | 가로 및 세로 화면의 20%, 영역 2를 가로 및 세로 화면의 80%로, 세로 화면의 20%로, 영역 3을 가로 및 세로 화면의 20%로, 영역 3을 가로 100%로, 세로 화면의 80%로 16:9 비율로 만들 수 있는 3존 가로 레이아웃을 말합니다. |
| Upper20-PortraitHD2Zone | 16:9의 종횡비를 사용하여 화면의 20%를 맨 위에서 처리하는 2존 세로 템플릿을 나타냅니다. |
| Right20-LandscapeSD3Zone | 화면상의 20%를 오른쪽에서 차지하는 3영역 템플릿을 나타냅니다(종횡비 4:3). |

## 사용 사례 예 {#example-use-cases}

## Left20-LandscapeHD3영역 레이아웃 {#custom-template-one}

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

1. 복사한 **왼쪽** (`/apps/customtemplate/template`)의 이름을 **내 사용자 지정 레이아웃으로**&#x200B;변경합니다.

1. Left20- `/apps/customtemplate/template/my-custom-layout` LandscapeHD3Zone에 대한 속성 **jcr:description** to *Template and* jcr:title **** ** toLeft20-LandscapeHD3Zone으로 이동하고 업데이트합니다.

1. 에서 **offline-config** 노드로 이동하고 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` jcr:title **을 Left20-** LandscapeHD3Zone으로 업데이트합니다 **.

1. 에서 *my-custom-template* 의 **jcr:content** 속성으로 `/apps/customtemplate/template/my-custom-layout/jcr:content` 이동하고 cq:cssClass **속성을 aem-Layout my-custom-layout에** ****&#x200B;업데이트합니다.

1. (4) 단계를 참조하여 왼쪽 상단의 템플릿을 복사하면 아래 3개의 응답형 격자를 볼 수 `my-custom-layout/jcr:content`있습니다. 사용자 지정 css 클래스를 *cq:cssClass* 속성의 각 응답형 격자에 추가합니다. 예를 들어 *my-custom-custom-layout*—top-left *,* my-custom-layout—top-right *,* my custom-layout—bottom.

   >[!NOTE]
   >이러한 사용자 정의 클래스는 css에서 반응형 그리드의 폭/높이를 설정하는 데 사용됩니다.

   >[!NOTE]
   > 원하는 전체 격자 수를 기반으로 응답형 그리드를 추가하거나 제거할 수 있습니다. 이 예에서는 첫 번째 행에 2개의 격자를 표시하고 두 번째 행에 1개의 격자를 표시하므로 총 3개의 응답형 격자(r1c1, r1c2, r2c1)가 있습니다.

1. `/libs/settings/wcm/designs/screens` 사용자 정의 템플릿 디자인으로 `/apps/settings/wcm/designs/` **복사 및 이름 바꾸기**

1. 사용자 정의 템플릿 디자인의 `/apps/settings/wcm/designs/custom-template-designs` jcr:title *속성으로* 이동하여 **사용자 정의 템플릿 디자인을** 업데이트합니다 ****.

1. 다음과 일치하도록 `/apps/settings/wcm/designs/<project>-designs/static.css` 컨텐츠 업데이트

## 특정 구성으로 사용자 지정 템플릿 만들기 {#basic-flow-setting}

![이미지](assets/custom-template1.png)

아래 절차에 따라 사용자 정의 템플릿을 만듭니다.

1. 템플릿 만들기 `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. 에서 페이지 디자인 만들기를 `/apps/settings/wcm/designs/<project>`참조하십시오.

   >[!NOTE]
   >
   >위의 `cq:designPath` 항목이 패스와 일치하는지 확인합니다.

1. 디자인을 위한 **offline-config** 노드를 업데이트하여 새 경로를 가리키도록 합니다

1. 폴더에 **static.css** `/apps/settings/wcm/designs/<project>` 파일을 추가하고 해당 컨텐츠를

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## 배경 레이어로 이미지 삽입 {#inserting-image}

이미지를 배경 레이어로 레이아웃에 삽입할 수 있습니다.

CSS 규칙을 조정하여 &quot;data-uri&quot;라고 하는 항목을 사용하고 CSS 파일에서 이미지(Base64 인코딩)의 바로 인라인으로 지정할 수 있습니다.

이 작업은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 따를 수 있습니다.

1. 이미지가 채널에 대한 오프라인 구성에 어떻게 포함되었는지 확인합니다.
1. 위의 CSS에서 &quot;data-uri&quot; 변형 대신 이미지에 대한 직접 링크 사용


## 배경색 업데이트 {#updating-color}

배경색을 변경하려면 다음 코드를 xml 파일에 추가합니다.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



