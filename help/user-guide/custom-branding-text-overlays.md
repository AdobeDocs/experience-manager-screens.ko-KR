---
title: 텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용
description: AEM Screens 채널의 에셋에 적용된 텍스트 오버레이에 사용자 지정 브랜딩 및 스타일을 적용하는 방법에 대해 알아봅니다.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# 텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일링 {#creating-custom-branding-styling}

AEM Screens 채널에서 에셋에 적용된 텍스트 오버레이에 사용자 지정 브랜딩 및 스타일을 적용하는 방법을 알아봅니다.

## 텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일 만들기 {#steps-custom-branding}

텍스트 오버레이에 대한 사용자 지정 브랜딩 및 스타일을 만들려면 아래 단계를 따르십시오.

1. AEM Screens 프로젝트를 만듭니다. 이 예제에서는 아래 그림과 같이 이름이 **`customstyle`**&#x200B;인 프로젝트와 제목이 **DemoBrand**&#x200B;인 채널을 만들어 기능을 보여 줍니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 편집기에서 이미지를 드래그 앤 드롭한 후 에셋에 텍스트 오버레이를 추가합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >채널 편집기에서 자산에 텍스트 오버레이를 추가하는 방법에 대해 알아보려면 [텍스트 오버레이](/help/user-guide/text-overlay.md)를 참조하십시오.

1. AEM 인스턴스 > 도구 > **CRXDE Lite**&#x200B;에서 CRXDE Lite으로 이동합니다.

1. `/apps/settings/wcm/designs/<your-project>/`에서 사용자 지정 디자인을 만듭니다. 예를 들어 이 경우 `/apps/settings/wcm/designs/customstyle/`(으)로 이동합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. *static.css* 파일을 만들고 다음 css 규칙을 설정합니다. 또한 아래 그림에서 css 규칙 예제로도 제공됩니다.

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

1. 프로젝트에 경로를 복사합니다. 이 경우 경로는 `/apps/settings/wcm/designs/customstyle`입니다.

1. **DemoBrand**(단계(1)에서 생성됨)라는 채널로 이동하고, 채널을 선택한 후 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.

1. **고급** 탭으로 이동하여 **디자인** 필드를 확인합니다.
   ![이미지](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >기본적으로 **디자인** 필드에는 libs 폴더의 디자인을 가리키는 경로가 표시됩니다.

1. 프로젝트 폴더의 경로로 **디자인** 필드를 업데이트합니다. 이 경우 `/apps/settings/wcm/designs/customstyle`입니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 디자인 경로를 업데이트하려면 **저장 및 닫기**&#x200B;를 클릭하십시오.

   >[!IMPORTANT]
   >선택적으로 기존 Screens 템플릿을 오버레이하여 기본적으로 자체 디자인을 삽입하거나 자체 템플릿을 모두 만들 수 있습니다. 자세한 내용은 아래 단계를 참조하십시오.

1. 기존 Screens 템플릿을 오버레이하여 기본적으로 고유한 디자인을 주입하려면 다음을 수행하십시오.

   1. `/apps/screens/core/templates/sequencechannel`의 `/libs/screens/core/templates/sequencechannel` 오버레이
   1. 새 디자인을 가리키도록 `/apps/screens/core/templates/sequencechannel/jcr:content`에서 *`cq:designPath`* 속성을 수정하십시오.

1. 나만의 템플릿을 모두 만들려면 다음 작업을 수행하십시오.
   1. `/libs/screens/core/templates/sequencechannel`을(를) `/apps/customstyle/templates/styled-sequencechannel`에 복사합니다.
   1. 새 디자인을 가리키도록 `/apps/customstyle/templates/styled-sequencechannel/jcr:content`에서 *`cq:designPath`* 속성을 수정하십시오.


### ACL 업데이트 {#updating-acls}

플레이어에서 다운로드할 수 있도록 이러한 디자인에 대한 ACL을 업데이트합니다.

1. 사용자 관리자로 이동하여 `screens-<project>-devices group`을(를) 선택하고 사용자 지정 디자인 경로에 대한 읽기 권한을 부여합니다.

1. `screens-<project>-administrators` 그룹에 이 경로에 대한 읽기 및 수정 권한을 제공하십시오.

## 결과 보기 {#viewing-the-result}

이전 단계를 완료하면 **CRXDE Lite**&#x200B;에서 *statis.css* 파일을 업데이트하여 에셋에 이미 추가된 텍스트 오버레이에 대한 업데이트를 볼 수 있습니다.

텍스트 오버레이에 업데이트된 디자인을 보려면 아래 단계를 따르십시오.

1. 제목이 **`customstyle`** > **채널** > **데모 브랜드**&#x200B;인 AEM Screens 프로젝트로 이동합니다. 채널을 클릭하고 작업 표시줄에서 **편집**&#x200B;을 클릭합니다.

1. 위에서 언급한 대로 **디자인** 필드에 디자인을 추가했으므로 **미리 보기**&#x200B;를 클릭하여 텍스트 오버레이로 이미지의 현재 스타일을 표시합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. CRXDE Lite에서 *static.css* 파일로 이동한 다음 아래와 같이 `font-family: "Lucida Console", Courier, monospace;`과(와) 같은 글꼴을 이 파일에 추가합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 변경 사항을 저장하고 미리보기를 다시 로드하면 아래 그림과 같이 텍스트 오버레이 글꼴이 업데이트됩니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 또한 *static.css* 파일에서 마지막 두 개의 코드 블록을 제거하여 텍스트 오버레이 주변의 박스형 스타일을 제거할 수 있습니다.

![이미지](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 텍스트 오버레이가 이미지에 추가되는 업데이트된 변경 사항을 미리보기에서 확인합니다.

   ![이미지](/help/user-guide/assets/custom-brand/custom-brand11.png)

   이제 에셋에 추가된 텍스트 오버레이에 대한 브랜드 및 사용자 지정 스타일을 업데이트할 준비가 되었습니다.
