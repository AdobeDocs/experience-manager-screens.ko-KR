---
title: 다중 영역 레이아웃에서 사용자 지정 템플릿 만들기
description: AEM Screens용 다중 영역 레이아웃에서 사용자 지정 템플릿을 만드는 방법에 대해 알아봅니다.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '849'
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

   AEM Screens 프로젝트에서 사용할 사용자 지정 다중 영역 템플릿을 만드는 방법을 이해하려면 먼저 만들려는 템플릿의 용어를 이해하십시오.

   | **레이아웃 이름** | **설명** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 3개의 영역을 만들 수 있는 3개 영역 가로 레이아웃:<br>* 영역 1은 왼쪽에서 가로 및 세로 화면의 20%입니다.<br>* 영역 2를 가로 화면의 80%, 세로 화면의 20%로 오른쪽 정렬<br>* 영역 3은 가로 100%, 세로 80%로 16:9 화면 비율 |
   | `Upper20-PortraitHD2Zone` | 화면 상단에서 화면의 20%를 덮고 종횡비가 16:9인 2영역 세로 템플릿 |
   | `Right20-LandscapeSD3Zone` | 오른쪽에서 화면의 20%를 덮고 종횡비가 4:3인 3영역 템플릿 |

   >[!IMPORTANT]
   >사용자 지정 레이아웃 내에 정의된 영역이 전체 레이아웃의 전체 종횡비와 일치하지 않을 수 있습니다. 이 문서에서 따르는 명명 규칙은 전체적으로 사용자 정의 레이아웃의 종횡비를 지정합니다.

## 예제 사용 사례 `Left20-LandscapeHD3Zone` 레이아웃 {#custom-template-one}

사용자 지정 템플릿을 만들려면 아래 섹션을 따르십시오. *`Left20-LandscapeHD3Zone`* 다음 구성을 사용하여

* **`Left20`** - 왼쪽 상단 영역은 가로 및 세로 화면 크기의 20%입니다.
* **`Landscape`** - 화면 방향.
* **`HD`** - 종횡비는 16:9입니다.
* **`3Zone`** - 디스플레이의 세 영역.

## 다중 영역 레이아웃의 시각적 표현 {#multi-layout-visual-one}

다음 `Left20-LandscapeHD3Zone` 레이아웃을 사용하면 프로젝트에서 다음과 같은 다중 영역 레이아웃을 만들 수 있습니다.

![이미지](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 만들기 `Left20-LandscapeHD3Zone` 레이아웃 {#landscape-layout-one}

아래 단계에 따라 `Left20-LandscapeHD3Zone` AEM Screens 프로젝트용 레이아웃입니다.

1. 제목이 인 AEM Screens 프로젝트 만들기 **`customtemplate`**.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 다음으로 이동 **CRXDE Lite** AEM 인스턴스 > 도구 > **CRXDE Lite**.

1. 아래에 폴더 만들기 **앱** 제목이 다음으로 지정됨 **`customtemplate`**. 마찬가지로 이라는 다른 폴더를 만듭니다. **템플릿** 아래에 **`customtemplate`**&#x200B;을 참조하십시오.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >클릭 **모두 저장** 컨텐츠를 만들거나 편집하거나 CRXDE Lite에 복사할 때마다 노드의 작업 표시줄에서 을 클릭합니다. 그렇지 않으면 업데이트를 커밋할 수 없습니다.

1. 에서 왼쪽 막대 템플릿 복사 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 끝 `/apps/customtemplate/template`.

1. 복사된 항목 이름 바꾸기 **lbar-left** (`/apps/customtemplate/template`) 받는 사람 **내 사용자 지정 레이아웃**.
   ![이미지](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 다음으로 이동 `/apps/customtemplate/template/my-custom-layout` 및 속성 업데이트 **`jcr:description`** 끝 *템플릿`Left20-LandscapeHD3Zone`* 및 **`jcr:title`** 끝 *`Left20-LandscapeHD3Zone`*.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 다음 위치로 이동 **`offline-config`** 노드: 부터 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 및 업데이트 **`jcr:title`** 끝 *`Left20-LandscapeHD3Zone`*.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 다음 위치로 이동 *`jcr:content`* 다음의 속성 **my-custom-template** 출처: `/apps/customtemplate/template/my-custom-layout/jcr:content` 및 업데이트 **`cq:cssClass`** 속성을 사용하여 **aem 레이아웃 내 사용자 지정 레이아웃**.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 막대 왼쪽 템플릿을 복사한 단계 (4)를 참조하면 아래에 3개의 응답형 그리드를 볼 수 있습니다 `my-custom-layout/jcr:content`. 사용자 지정 css 클래스를 의 각 응답형 격자에 추가합니다. *`cq:cssClass`* 속성(예: ) *my-custom-layout - 왼쪽 상단* 대상 *r1c1* 노드.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template7.png)

   마찬가지로 를 추가합니다 *my-custom-layout - 오른쪽 위* 대상 *r1c2*  및, *my-custom-layout - bottom* 대상 *r2c1* 노드.

   >[!NOTE]
   >이러한 사용자 정의 클래스는 css에서 이러한 응답형 그리드의 너비/높이를 설정하는 데 사용됩니다.

   >[!NOTE]
   >원하는 총 격자선 수에 따라 응답형 격자선을 추가하거나 제거할 수 있습니다. 이 예에서는 첫 번째 행의 2개의 격자와 두 번째 행의 1개의 격자가 표시되어 총 3개의 응답형 격자(r1c1, r1c2, r2c1)가 있다.

1. 복사 `/libs/settings/wcm/designs/screens` 끝 `/apps/settings/wcm/designs/` 복사된 디자인의 이름을 로 변경합니다. **사용자 지정 템플릿 디자인**.

1. 다음으로 이동 `/apps/settings/wcm/designs/custom-template-designs` 속성 업데이트 *`jcr:title`* / **사용자 지정 템플릿 디자인** 끝 **customtemplate-design**.

1. 다음으로 이동 `/apps/settings/wcm/designs/custom-template-designs` static.css 파일을 만듭니다.

1. 콘텐츠 복사 대상 `static.css` 파일:

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

1. 다음으로 이동 `/apps/<project>/templates/my-custom-layout/jcr:content` 속성 업데이트 *`cq:designPath`* 끝 `/apps/settings/wcm/designs/customtemplate-designs` 따라서 static.css에 구성된 스타일을 로드할 수 있습니다.

   >[!NOTE]
   >복사 또는 붙여넣기가 아닌 모든 스타일을 입력하면 공백이 발생하여 css 스타일 문제가 발생할 수 있습니다.

## 결과 보기 {#viewing-result}

AEM Screens 프로젝트에서 위의 사용자 지정 템플릿을 사용하려면 아래 단계를 따르십시오.

1. (1)단계에서 만든 Screens 프로젝트로 이동한 다음 **채널** 폴더를 삭제합니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 클릭 **만들기** 작업 모음에서 템플릿을 클릭하고 **`Left20-LandscapeHD3Zone`** 다음에서 **만들기** 마법사.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 맞춤화된 템플릿으로 채널을 만든 후 편집기에서 채널에 에셋을 추가할 수 있습니다. 다음 미리 보기는 사용자 지정 템플릿의 이미지를 보여 줍니다.

   ![이미지](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 이미지를 배경 레이어로 삽입  {#inserting-image}

레이아웃에 이미지를 배경 레이어로 삽입할 수 있습니다.

&quot;data-uri&quot;를 사용하도록 CSS 규칙을 조정하고 이미지를 직접 인라인할 수 있습니다(`Base64` 인코딩됨)을 추가하여 (13단계)에서 만든 CSS 파일에서 *static.css*.

이 작업은 다음과 같이 수행됩니다.
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

또는 아래 단계를 따를 수 있습니다.

1. 이미지가 채널의 오프라인 구성에 어떻게든 포함되어 있는지 확인합니다.
1. &quot;data-uri&quot; 변형 대신 위의 CSS에서 이미지에 대한 직접 링크를 사용하십시오.


## 배경색 업데이트 중 {#updating-color}

배경색을 변경하려면 xml 파일에 다음 코드를 추가합니다(13단계). *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
