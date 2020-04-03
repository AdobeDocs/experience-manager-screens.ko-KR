---
title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
seo-title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
description: 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 알려면 이 페이지를 따르십시오.
seo-description: 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 알려면 이 페이지를 따르십시오.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일 {#creating-custom-branding-styling}

텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 적용하는 방법을 알려면 이 페이지를 따르십시오.

## 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일 만들기 {#steps-custom-branding}

아래 단계에 따라 텍스트 오버레이에 대한 사용자 정의 브랜딩 및 스타일링을 만드십시오.

1. 아래 그림과 같이 **맞춤형** 스타일로 제목이 지정된 AEM Screens 프로젝트와 DemoBrand **로**&#x200B;제목이 지정된 채널을 만듭니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 편집기에서 이미지를 드래그하여 놓고 텍스트 오버레이를 자산에 추가합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >채널 편집기에서 자산에 텍스트 오버레이를 추가하는 방법에 대해 알아보려면 텍스트 오버레이를 [참조하십시오](/help/user-guide/text-overlay.md).

1. AEM 인스턴스 —> 도구 —> CRXDE Lite에서 CRXDE **Lite로 이동합니다**.

1. 예를 들어, 이 경우 사용자 정의 디자인을 만들어야 `/apps/settings/wcm/designs/<your-project>/`합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. static.css 파일로 이동하여 다음 css 규칙을 설정합니다. 아래 그림에도 나와 있습니다.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 프로젝트의 경로를 복사합니다. 이 경우 경로가 `/apps/settings/wcm/designs/customstyle`표시됩니다.

1. DemoBrand(1 **단계에서** 제작)로 제목이 지정된 채널로 이동하고 **채널을 선택한 후 작업** 표시줄에서 속성을 클릭합니다.

1. 고급 **탭으로 이동하여** 디자인 **필드를 선택합니다** .
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >기본적으로 디자인 **필드에는 libs** 폴더의 디자인을 가리키는 경로가 표시됩니다.

1. 프로젝트 **폴더의** 경로로 디자인 필드를 업데이트합니다. 이 경우, 그렇게 될 `/apps/settings/wcm/designs/customstyle`것입니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 저장 **및 닫기를** 클릭하여 디자인 경로를 업데이트합니다.


## 결과 보기 {#viewing-the-result}

이전 단계를 완료하면 CRXDE Lite에서 *statis.css* 파일을 업데이트하고 **결과적으로** 자산에 추가된 텍스트 레이아웃에 대한 업데이트를 볼 수 있습니다.

아래 절차에 따라 텍스트 레이아웃에 업데이트된 디자인을 봅니다.

1. AEM Screens 프로젝트( **사용자 지정 스타일** 및 DemoBrand로 제목이 지정된 **채널)** 로 **이동하고 작업** 표시줄에서 편집을 클릭하여편집기를 엽니다.

1. 이제 디자인 필드에 디자인을 추가했으므로 위에 **언급된** 대로 미리 보기를 클릭하여 **텍스트** 오버레이가 있는 이미지의 현재 스타일을 봅니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 예를 들어 CRXDE Lite에서 static.css 파일로 이동하여 글꼴을 추가합니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 변경 내용을 저장하고 미리 보기를 다시 로드하면 아래 그림과 같이 텍스트 오버레이 글꼴이 업데이트됩니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 또한 static.css 파일에서 마지막 두 코드 블록을 제거하여 텍스트 오버레이 주위의 박스 스타일링을 제거할 수 있습니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 아래에 표시된 대로 텍스트 오버레이가 이미지에 추가되는 미리 보기에서 업데이트된 변경 내용을 볼 수 있습니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand11.png)

따라서 이전 섹션의 단계를 따라 자산에 추가된 텍스트 오버레이에 대한 브랜드 및 사용자 정의 스타일을 업데이트할 수 있습니다.









