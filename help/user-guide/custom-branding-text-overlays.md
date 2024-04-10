---
title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
seo-title: Applying Custom Branding and Styling for Text Overlays
description: 이 페이지를 따라 텍스트 오버레이에 사용자 지정 브랜딩 및 스타일을 적용하는 방법을 알아보십시오.
seo-description: Follow this page to learn how to apply custom branding and styling for Text Overlays.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 1%

---

# 텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일링 {#creating-custom-branding-styling}

이 페이지를 따라 AEM Screens 채널의 에셋에 적용된 텍스트 오버레이에 사용자 지정 브랜딩 및 스타일을 적용하는 방법을 알아보십시오.

## 텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일 만들기 {#steps-custom-branding}

텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일을 만들려면 아래 단계를 따르십시오.

1. AEM Screens 프로젝트를 만듭니다. 이 예제에서는 이라는 프로젝트를 만들어 기능을 보여 줍니다. **사용자 정의 스타일** 및 라는 이름의 채널 **DemoBrand** 을 참조하십시오.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 편집기에서 이미지를 끌어다 놓고 에셋에 텍스트 오버레이를 추가합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >채널 편집기에서 에셋에 텍스트 오버레이를 추가하는 방법은 를 참조하십시오. [텍스트 오버레이](/help/user-guide/text-overlay.md).

1. AEM 인스턴스에서 CRXDE Lite > 도구 > 로 이동합니다. **CRXDE Lite**.

1. 에서 사용자 정의 디자인을 만들어야 합니다. `/apps/settings/wcm/designs/<your-project>/`예를 들어 이 경우 다음으로 이동합니다. `/apps/settings/wcm/designs/customstyle/`

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 만들기 *static.css* 파일을 만들고 다음 css 규칙을 설정합니다. 또한 아래 그림에서 css 규칙 예제로도 제공됩니다.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 프로젝트에 경로를 복사합니다. 이 경우 경로는 다음과 같습니다. `/apps/settings/wcm/designs/customstyle`.

1. 이라는 제목이 있는 채널로 이동합니다. **DemoBrand** (단계 (1)에서 생성) 및 클릭 **속성** 을 클릭합니다.

1. 다음 위치로 이동 **고급** 탭을 클릭하고 다음을 확인합니다. **디자인** 필드.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >기본값으로으로, **디자인** 필드에는 libs 폴더의 디자인을 가리키는 경로가 표시됩니다.

1. 업데이트 **디자인** 프로젝트 폴더 경로가 포함된 필드. 이 경우, 다음과 같습니다. `/apps/settings/wcm/designs/customstyle`.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 클릭 **저장 및 닫기** 를 클릭하여 디자인 경로를 업데이트합니다.

   >[!IMPORTANT]
   >기존 Screens 템플릿을 오버레이하여 기본적으로 자체 디자인을 삽입하거나 자체 템플릿을 모두 만들 수 있는 옵션이 있습니다. 자세한 내용은 아래 단계를 참조하십시오.

1. 기존 Screens 템플릿을 오버레이하여 자신의 디자인을 기본적으로 삽입하려면 다음을 수행하십시오.

   1. 오버레이 `/libs/screens/core/templates/sequencechannel` 위치: `/apps/screens/core/templates/sequencechannel`.
   1. 수정 *cq:designPath* 의 속성 `/apps/screens/core/templates/sequencechannel/jcr:content` 을 클릭하여 새 디자인을 지정합니다.

1. 나만의 템플릿을 모두 만들려면 다음 작업을 수행하십시오.
   1. 복사 `/libs/screens/core/templates/sequencechannel` 끝 `/apps/customstyle/templates/styled-sequencechannel`.
   1. 수정 *cq:designPath* 의 속성 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 을 클릭하여 새 디자인을 지정합니다.


### ACL 업데이트 {#updating-acls}

플레이어에서 다운로드할 수 있도록 이러한 디자인에 대한 ACL을 업데이트해야 합니다.

1. 사용자 관리자로 이동하여 다음을 선택합니다. `screens-<project>-devices group` 사용자 지정 디자인 경로에 대한 읽기 권한을 부여합니다.

1. 제공 `screens-<project>-administrators` 이 경로에 대한 그룹 읽기 및 수정 권한.

## 결과 보기 {#viewing-the-result}

이전 단계를 완료하면 을 업데이트할 수 있습니다. *statis.css* 파일 출처: **CRXDE Lite** 결과적으로 에셋에 이미 추가된 텍스트 오버레이에 대한 업데이트를 봅니다.

텍스트 오버레이에 업데이트된 디자인을 보려면 아래 단계를 따르십시오.

1. 이라는 AEM Screens 프로젝트로 이동합니다. **사용자 정의 스타일** > **채널** > **DemoBrand**. 채널을 선택하고 **편집** 작업 표시줄에서 을 클릭하여 편집기를 엽니다.

1. 이제 디자인에 디자인을 추가했습니다. **디자인** 위에서 언급했듯이 **미리 보기** 를 클릭하여 텍스트 오버레이로 이미지의 현재 스타일을 봅니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 다음으로 이동 *static.css* CRXDE Lite의 파일을 참조하고, 다음과 같은 글꼴을 추가합니다. `font-family: "Lucida Console", Courier, monospace;` 아래 표시된 대로 이 파일을 복사합니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 변경 사항을 저장하고 미리보기를 다시 로드하면 아래 그림과 같이 텍스트 오버레이 글꼴이 업데이트됩니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 또한 의 마지막 두 코드 블록을 제거할 수 있습니다 *static.css* 텍스트 오버레이 주변의 박스형 스타일을 제거하는 파일입니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 텍스트 오버레이가 이미지에 추가된 미리보기에서 업데이트된 변경 사항을 보게 됩니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand11.png)

   이제 자산에 추가된 텍스트 오버레이에 대한 브랜드 및 사용자 지정 스타일을 업데이트할 준비가 되었습니다.
