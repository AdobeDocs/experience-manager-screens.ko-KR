---
title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
seo-title: 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기
description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: MultiZone 레이아웃에서 사용자 정의 템플릿을 만드는 방법에 대해 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 다중 영역 레이아웃에서 사용자 정의 템플릿 만들기 {#creating-custom-templates-multizone}

다음 예는 다중 영역 레이아웃에서 사용자 정의 템플릿을 만드는 방법을 보여줍니다.

예를 들어 아래 섹션에서는 다음 구성을 사용하여 다중 영역 레이아웃에서 사용자 정의 템플릿을 만드는 방법을 보여 줍니다.

![이미지](assets/custom-template1.png)


## 특정 구성으로 사용자 지정 템플릿 만들기 {#basic-flow-setting}

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

CSS 규칙을 조정하여 "data-uri"라고 하는 항목을 사용하고 CSS 파일에서 이미지(Base64 인코딩)의 바로 인라인으로 지정할 수 있습니다.

이 작업은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 따를 수 있습니다.

1. 이미지가 채널에 대한 오프라인 구성에 어떻게 포함되었는지 확인합니다.
1. 위의 CSS에서 "data-uri" 변형 대신 이미지에 대한 직접 링크 사용


## 배경색 업데이트 {#updating-color}

배경색을 변경하려면 다음 코드를 xml 파일에 추가합니다.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
