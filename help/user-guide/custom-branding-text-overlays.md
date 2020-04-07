---
title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
seo-title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
description: 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 알려면 이 페이지를 따르십시오.
seo-description: 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f373ca17738f3018acf6b4cffaf523bb731e7c26

---


# 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일 {#creating-custom-branding-styling}

스크린 채널에서 자산에 적용된 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 살펴보려면 이 페이지를 따르십시오.

## 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일 만들기 {#steps-custom-branding}

아래 단계에 따라 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 만드십시오.

1. AEM Screens 프로젝트를 만듭니다. 이 예에서는 아래 그림과 같이 **customstyle** 프로젝트와 DemoBrand라는 **채널을** 제작하여 기능을 보여줍니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 편집기에서 이미지를 드래그하여 놓고 텍스트 오버레이를 자산에 추가합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >채널 편집기에서 자산에 텍스트 오버레이를 추가하는 방법에 대해 알아보려면 텍스트 오버레이를 [참조하십시오](/help/user-guide/text-overlay.md).

1. AEM 인스턴스 —> 도구 —> CRXDE Lite에서 CRXDE **Lite로 이동합니다**.

1. 사용자 정의 디자인을 만들어야 `/apps/settings/wcm/designs/<your-project>/`합니다. 예를 들어, `/apps/settings/wcm/designs/customstyle/`

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. static.css ** 파일을 만들고 다음 css 규칙을 설정합니다. css 규칙 아래 그림에도 예시로 표시됩니다.

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

1. 프로젝트의 경로를 복사합니다. 이 경우 경로가 `/apps/settings/wcm/designs/customstyle`표시됩니다.

1. DemoBrand( **1단계에서** 제작)라는 채널로 이동하고 **채널을 선택한 후 작업** 표시줄에서 속성을 클릭합니다.

1. 고급 **탭으로 이동하여** 디자인 **필드를 선택합니다** .
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >기본적으로 디자인 **필드에는 libs** 폴더의 디자인을 가리키는 경로가 표시됩니다.

1. 프로젝트 **폴더의** 경로로 디자인 필드를 업데이트합니다. 이 경우, 그렇게 될 `/apps/settings/wcm/designs/customstyle`것입니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 저장 **및 닫기를** 클릭하여 디자인 경로를 업데이트합니다.

>[!IMPORTANT]
> 기존 스크린 템플릿을 오버레이하여 기본적으로 자신의 디자인을 주입하거나 고유한 템플릿을 함께 만들 수 있습니다. 자세한 내용은 아래 단계를 참조하십시오.

1. 기존 스크린 템플릿을 오버레이하여 기본적으로 자신의 디자인을 삽입하려면 다음을 수행하십시오.

   1. 오버레이로 `/libs/screens/core/templates/sequencechannel` 로그인합니다 `/apps/screens/core/templates/sequencechannel`.
   1. 새 디자인을 *가리키도록 cq:designPath* 속성을 `/apps/screens/core/templates/sequencechannel/jcr:content` 수정합니다.

1. 템플릿을 모두 만들려면:
   1. 복사 `/libs/screens/core/templates/sequencechannel` 대상 `/apps/customstyle/templates/styled-sequencechannel`.
   1. 새 디자인을 *가리키도록 cq:designPath* 속성을 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 수정합니다.


### ACL 업데이트 {#updating-acls}

플레이어에서 다운로드할 수 있도록 이러한 디자인의 ACL을 업데이트해야 합니다.

1. useradmin으로 이동한 다음 `screens-<project>-devices group` 을 선택하고 사용자 정의 디자인 경로에 대한 읽기 권한을 부여합니다.

1. 이 경로에 대한 `screens-<project>-administrators` 그룹 읽기 및 수정 권한을 제공합니다.

## 결과 보기 {#viewing-the-result}

이전 단계를 완료하면 CRXDE Lite에서 *statis.css* 파일을 업데이트하여 **해당** 자산에 이미 추가된 텍스트 오버레이에 대한 업데이트를 볼 수 있습니다.

텍스트 오버레이에 대한 업데이트된 디자인을 보려면 아래 절차를 따르십시오.

1. AEM Screens 프로젝트를 **사용자 지정 스타일** —> 채널 **—>** Demo **브랜드로**&#x200B;이동합니다. Select the channel and click **Edit** from the action bar to open the editor.

1. 이제 디자인 필드에 디자인을 추가했으므로 위에 **언급된** 대로 미리 보기를 클릭하여 **텍스트** 오버레이가 있는 이미지의 현재 스타일을 봅니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Lite에서 *static.css* 파일을 찾아 `font-family: "Lucida Console", Courier, monospace;` 아래와 같이 이 파일에 글꼴을 추가합니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 변경 내용을 저장하고 미리 보기를 다시 로드하면 아래 그림과 같이 텍스트 오버레이 글꼴에 대한 업데이트가 표시됩니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 또한 *static.css* 파일에서 마지막 두 블록을 제거하여 텍스트 오버레이 주위의 박스 스타일링을 제거할 수 있습니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 텍스트 오버레이가 이미지에 추가되는 미리 보기에서 업데이트된 변경 내용을 볼 수 있습니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand11.png)

이제 튜토리얼을 참조하여 자산에 추가된 텍스트 오버레이에 대한 브랜드 및 사용자 정의 스타일을 업데이트할 수 있습니다.









