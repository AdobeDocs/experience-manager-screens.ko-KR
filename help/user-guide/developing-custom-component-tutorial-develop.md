---
title: AEM Screens용 사용자 지정 구성 요소 개발
seo-title: AEM Screens용 사용자 지정 구성 요소 개발
description: 다음 자습서에서는 AEM Screens용 사용자 지정 구성 요소를 만드는 단계를 안내합니다. AEM Screens는 다른 AEM 제품의 많은 기존 디자인 패턴과 기술을 재사용합니다. 이 자습서에서는 AEM Screens를 개발할 때 차이점과 특별한 고려 사항을 설명합니다.
seo-description: AEM Screens용 간단한 "Hello World" 구성 요소를 빌드하기 위한 소개 자습서입니다. AEM Screens는 다른 AEM 제품의 많은 기존 디자인 패턴과 기술을 재사용합니다. 다음 자습서에서는 AEM Screens용 개발 시 특정 차이점과 고려 사항을 강조 표시하려고 합니다.
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens용 사용자 지정 구성 요소 개발 {#developing-a-custom-component-for-aem-screens}

다음 자습서에서는 AEM Screens용 사용자 지정 구성 요소를 만드는 단계를 안내합니다. AEM Screens는 다른 AEM 제품의 많은 기존 디자인 패턴과 기술을 재사용합니다. 이 자습서에서는 AEM Screens를 개발할 때 차이점과 특별한 고려 사항을 설명합니다.

## 개요 {#overview}

이 자습서는 AEM Screens를 처음 사용하는 개발자를 위한 것입니다. 이 자습서에서는 간단한 "Hello World" 구성 요소가 AEM Screens의 시퀀스 채널에 맞게 빌드됩니다. 작성자는 대화 상자를 사용하여 표시된 텍스트를 업데이트할 수 있습니다.

![과소](assets/overviewhellow.png)

## 전제 조건 {#prerequisites}

이 자습서를 완료하려면 다음 사항이 필요합니다.

1. [AEM 6.5](https://helpx.adobe.com/experience-manager/6-4/release-notes.html) 또는 [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + 최신 스크린 기능 팩

1. [AEM 스크린 플레이어](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. 로컬 개발 환경

자습서 단계 및 스크린샷은 CRXDE-Lite를 사용하여 **수행됩니다**. IDE를 사용하여 자습서를 완료할 수도 있습니다. IDE를 사용하여 AEM [과 함께 개발하는 방법에 대한 자세한 내용은 여기를 참조하십시오.](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## 프로젝트 설정 {#project-setup}

스크린 프로젝트의 소스 코드는 일반적으로 다중 모듈 Maven 프로젝트로 관리됩니다. 튜토리얼을 신속하게 진행하기 위해 AEM Project Tranype 13을 사용하여 프로젝트를 미리 [생성했습니다](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype). Maven AEM Project Tranype을 사용하여 프로젝트를 [만드는 방법에 대한 자세한 내용은 여기를](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule)참조하십시오.

1. CRX 패키지 관리자를 사용하여 다음 패키지를 [다운로드하고 설치합니다](http://localhost:4502/crx/packmgr/index.jsp).

   [파일 가져오기](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [파일 가져오기](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **선택적으로** Eclipse 또는 다른 IDE를 사용하여 작업하는 경우 아래 소스 패키지를 다운로드하십시오. Maven 명령을 사용하여 프로젝트를 로컬 AEM 인스턴스에 배포합니다.

   **`mvn -PautoInstallPackage clean install`**

   HelloWorld SRC Screens We.Retail 실행 프로젝트 시작

   [파일 가져오기](assets/src-screens-weretail-run.zip)

1. CRX [Package](http://localhost:4502/crx/packmgr/index.jsp) Manager에서 다음 두 패키지가 설치되었는지 확인합니다.

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Screens We.Retail 실행 Ui.Apps 및 Ui.Content 패키지 CRX 패키지 관리자를 통해 설치](assets/crx-packages.png)

   Screens We.Retail 실행 Ui.Apps 및 Ui.Content 패키지 CRX 패키지 관리자를 통해 설치

1. screens-weretail-run.ui.ap **ps** 패키지는 아래 코드를 설치합니다 `/apps/weretail-run`.

   이 패키지에는 프로젝트의 사용자 지정 구성 요소를 렌더링하는 데 책임이 있는 코드가 들어 있습니다. 이 패키지에는 구성 요소 코드와 필요한 모든 JavaScript 또는 CSS가 포함되어 있습니다. 또한 이 패키지에는 프로젝트에 필요한 Java 코드가 들어 있는 **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** 또한 포함됩니다.

   >[!NOTE]
   >
   >이 자습서에서는 Java 코드가 작성되지 않습니다. 더 복잡한 비즈니스 로직이 필요한 경우, 핵심 Java 번들을 사용하여 백엔드 Java를 만들고 배포할 수 있습니다.

   ![CRXDE Lite의 ui.apps 코드 표시](assets/uipps-contents.png)

   CRXDE Lite의 ui.apps 코드 표시

   helloworld **구성** 요소는 현재 자리 표시자에 불과합니다. 자습서 과정에서 작성자가 구성 요소에 표시된 메시지를 업데이트할 수 있는 기능이 추가됩니다.

1. screens-weretail-run.ui.co **컨텐츠** 패키지는 다음 아래에 코드를 설치합니다.

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`
   이 패키지에는 프로젝트에 필요한 시작 내용 및 구성 구조가 들어 있습니다. **`/conf/we-retail-run`** 에 We.Retail Run 프로젝트에 대한 모든 구성이 포함되어 있습니다. **`/content/dam/we-retail-run`** 에는 프로젝트의 디지털 자산 시작을 포함합니다. **`/content/screens/we-retail-run`** 스크린 컨텐츠 구조를 포함합니다. 이러한 모든 경로 아래의 컨텐츠는 주로 AEM에서 업데이트됩니다. 환경(로컬, 개발, 스테이지, 제품) 간의 일관성을 유지하기 위해 기본 컨텐츠 구조가 소스 제어에 저장되는 경우가 많습니다.

1. **AEM Screens &gt; We.Retail 실행 프로젝트로 이동합니다.**

   AEM 시작 메뉴 &gt; 화면 아이콘을 클릭합니다. We.Retail 실행 프로젝트가 표시되는지 확인합니다.

   ![we-real-run-starter](assets/we-retaiul-run-starter.png)

## Hello World 구성 요소 만들기 {#hello-world-cmp}

Hello World 구성 요소는 사용자가 화면에 표시할 메시지를 입력할 수 있는 간단한 구성 요소입니다. 구성 요소는 AEM Screens 구성 [요소 템플릿을 기반으로 합니다.https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens에는 기존 WCM 사이트 구성 요소에 대해 반드시 true가 아닌 몇 가지 흥미로운 제한이 있습니다.

* 대부분의 화면 구성 요소는 대상 디지털 사이니지 장치에서 전체 화면으로 실행해야 합니다.
* 슬라이드쇼를 생성하려면 대부분의 스크린 구성 요소를 시퀀스 채널에 임베드 가능해야 합니다.
* 작성 시 시퀀스 채널에서 개별 구성 요소를 편집할 수 있으므로 전체 화면으로 렌더링하는 것은 문제가 되지 않습니다

1. CRXDE **-Lite** (또는 IDE of `http://localhost:4502/crx/de/index.jsp` choice)에서 `/apps/weretail-run/components/content/helloworld.`

   다음 속성을 구성 요소에 `helloworld` 추가합니다.

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![/apps/weretail-run/components/content/help용 속성](assets/2018-04-28_at_4_23pm.png)

   /apps/weretail-run/components/content/help용 속성

   helloworld **구성** 요소는 **foundation/components/parbase** 구성 요소를 확장하여 시퀀스 채널 내에서 올바르게 사용할 수 있도록 합니다.

1. 다음 `/apps/weretail-run/components/content/helloworld` 이름 아래에 파일 만들기 `helloworld.html.`

   다음 항목으로 파일을 채웁니다.

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   스크린 구성 요소에는 사용되는 [제작 모드에](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes) 따라 두 가지 다른 렌더링이 필요합니다.

   1. **제작**:미리 보기 또는 게시 모드(wcmmode=disabled)
   1. **편집**:편집, 디자인, 스캐폴딩, 개발자 등 기타 모든 제작 모드에 사용됩니다.
   `helloworld.html`는 전환 역할을 하며 현재 어떤 제작 모드가 활성화되어 있는지 확인하고 다른 HTL 스크립트로 리디렉션합니다. 스크린 구성 요소에서 사용되는 일반적인 규칙은 편집 모드에 대한 `edit.html` 스크립트와 프로덕션 모드에 대한 `production.html` 스크립트를 갖는 것입니다.

1. 다음 `/apps/weretail-run/components/content/helloworld` 이름 아래에 파일 만들기 `production.html.`

   다음 항목으로 파일을 채웁니다.

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   위쪽은 Hello World 구성 요소의 제작 마크업입니다. 구성 요소가 시퀀스 채널에서 사용되므로 `data-duration` 속성이 포함됩니다. 이 `data-duration` 속성은 시퀀스 항목이 표시되는 기간을 알 수 있도록 시퀀스 채널에서 사용됩니다.

   구성 요소는 텍스트와 함께 a `div` 및 `h1` 태그를 렌더링합니다. `${properties.message}` 는 HTL 스크립트의 일부로서 이름이 `message`지정된 JCR 속성의 내용을 출력합니다. 나중에 사용자가 `message` 속성 텍스트 값을 입력할 수 있는 대화 상자가 만들어집니다.

   또한 BEM(블록 요소 수정자) 표기법은 구성 요소와 함께 사용됩니다. BEM은 재사용 가능한 구성 요소를 손쉽게 만들 수 있는 CSS 코딩 규칙입니다. BEM은 AEM의 핵심 [구성 요소에서 사용되는 표기법입니다](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). 자세한 내용은 [https://getbem.com/](https://getbem.com/)

1. 다음 `/apps/weretail-run/components/content/helloworld` 이름 아래에 파일 만들기 `edit.html.`

   다음 항목으로 파일을 채웁니다.

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   위쪽은 Hello World 구성 요소의 편집 마크업입니다. 대화 상자 메시지를 채운 경우 첫 번째 블록은 구성 요소의 편집 버전을 표시합니다.

   두 번째 블록은 대화 상자를 입력하지 않은 경우 렌더링됩니다. 그러면 레이블이 Hello World `cq-placeholder` 로 `data-emptytext` ****** 렌더링되고 이 경우 자리 표시자로 렌더링됩니다. 여러 로케일에서 작성을 지원하기 위해 i18n을 사용하여 레이블의 문자열을 국제화할 수 있습니다.

1. **Hello World 구성 요소에 사용할 스크린 이미지 복사 대화 상자.**

   기존 대화 상자에서 시작한 다음 수정하는 것이 가장 쉽습니다.

   1. 다음 위치에서 대화 상자 복사: `/libs/screens/core/components/content/image/cq:dialog`
   1. 아래 대화 상자 붙여넣기 `/apps/weretail-run/components/content/helloworld`
   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **메시지 탭을 포함하도록 Hello World 대화 상자를 업데이트합니다.**

   다음과 일치하도록 대화 상자를 업데이트합니다. JCR 노드 구조는 아래에 XML로 제공됩니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   메시지의 textfield는 명명된 속성에 저장되며, Duration의 number `message` 필드는 이름이 `duration`지정된 속성에 저장됩니다. 이러한 두 속성은 HTL에서 `/apps/weretail-run/components/content/helloworld/production.html` 및 `${properties.message}` 로 모두 참조됩니다 `${properties.duration}`.

   ![Hello World - 완료된 대화](assets/2018-04-29_at_5_21pm.png)

   Hello World - 완료된 대화

## 클라이언트측 라이브러리 만들기 {#clientlibs}

클라이언트측 라이브러리는 AEM 구현에 필요한 CSS 및 JavaScript 파일을 구성하고 관리하는 메커니즘을 제공합니다.

AEM Screens 구성 요소는 편집 모드와 미리 보기/프로덕션 모드에서 다르게 렌더링됩니다. 두 개의 클라이언트 라이브러리가 생성되며, 하나는 편집 모드이고 다른 하나는 미리 보기/프로덕션에 사용됩니다.

1. Hello World 구성 요소에 대한 클라이언트측 라이브러리의 폴더를 만듭니다.

   아래 `/apps/weretail-run/components/content/helloworld`새 폴더를 만듭니다(이름이 `clientlibs`표시됨).

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. 폴더 아래에 `clientlibs` Type `shared` 이라는 새 노드를 만듭니다. `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. 공유 클라이언트 라이브러리에 다음 속성을 추가합니다.

   * `allowProxy` | 부울 | `true`

   * `categories`| 문자열[] | `cq.screens.components`
   ![/apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/shared

   categories 속성은 클라이언트 라이브러리를 식별하는 문자열입니다. cq.screens.componentscatory는 편집 및 미리 보기/프로덕션 모드에서 모두 사용됩니다. 따라서 sharedclientlib에 정의된 모든 CSS/JS는 모든 모드로 로드됩니다.

   프로덕션 환경에서 /apps에 직접 경로를 노출하지 않는 것이 좋습니다. allowProxy 속성은 클라이언트 라이브러리 CSS 및 JS가 접두사 of/etc.clientlibs을 통해 참조되도록 합니다.

1. 공유 폴더 `css.txt` 아래에 명명된 파일을 만듭니다.

   다음 항목으로 파일을 채웁니다.

   ```
   #base=css
   
   styles.less
   ```

1. 폴더 `css` 아래에 명명된 폴더를 `shared` 만듭니다. 폴더 `style.less` 아래에 명명된 파일을 `css` 추가합니다. 이제 클라이언트 라이브러리의 구조는 다음과 같아야 합니다.

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   이 자습서에서는 CSS를 직접 작성하는 대신 LESS를 사용합니다. [LESS는](https://lesscss.org/) CSS 변수, 믹스 및 함수를 지원하는 널리 사용되는 CSS 사전 컴파일러입니다. AEM 클라이언트 라이브러리는 기본적으로 LESS 컴파일을 지원합니다. sass 또는 기타 사전 컴파일러는 사용할 수 있지만 AEM 외부에서 컴파일해야 합니다.

1. 다음 `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` 항목으로 채웁니다.

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. 클라이언트 라이브러리 폴더를 복사하여 붙여 넣어 이름이 `shared` `production`지정된 새 클라이언트 라이브러리를 만듭니다.

   ![공유 클라이언트 라이브러리를 복사하여 새 프로덕션 클라이언트 라이브러리 만들기](assets/copy-clientlib.gif)

   공유 클라이언트 라이브러리를 복사하여 새 프로덕션 클라이언트 라이브러리 만들기

1. 프로덕션 클라이언트 라이브러리의 `categories` 속성을 업데이트합니다. `cq.screens.components.production.`

   이렇게 하면 미리 보기/프로덕션 모드에서만 스타일을 로드할 수 있습니다.

   ![/apps/weretail-run/components/content/helloworld/clientlibs/production 속성](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/production 속성

1. 다음 `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` 항목으로 채웁니다.

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   위 스타일은 화면 중앙에 있는 메시지를 프로덕션 모드에서만 표시합니다.

세 번째 클라이언트 라이브러리 카테고리:구성 요소에 편집 전용 스타일을 추가하는 `cq.screens.components.edit` 데 사용할 수 있습니다.

| Clientlib 범주 | 사용량 |
|---|---|
| `cq.screens.components` | 편집 모드와 제작 모드 간에 공유되는 스타일 및 스크립트 |
| `cq.screens.components.edit` | 편집 모드에서만 사용되는 스타일 및 스크립트 |
| `cq.screens.components.production` | 프로덕션 모드에서만 사용되는 스타일 및 스크립트 |

## 디자인 페이지 만들기 {#design-page}

AEM Screens는 [정적 페이지 템플릿](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/page-templates-static.html) 및 [디자인 구성을](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) 전역 변경 사항에 사용합니다. 디자인 구성은 채널에서 Parsys에 대해 허용되는 구성 요소를 구성하는 데 자주 사용됩니다. 이러한 구성을 앱별 방식으로 저장하는 것이 좋습니다.

We.Retail Run Design 페이지에 We.Retail Run 프로젝트에 관련된 모든 구성을 저장하는 We.Retail 실행 페이지가 생성됩니다.

1. CRXDE **-Lite에서** 다음 `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` 위치로 이동합니다. `/apps/settings/wcm/designs`
1. 디자인 폴더 아래에 유형이 `we-retail-run` 있는 새 노드를 만듭니다 `cq:Page`.
1. 페이지 아래에서, `we-retail-run` 유형의 다른 노드를 `jcr:content` `nt:unstructured`추가합니다. 다음 속성을 `jcr:content` 노드에 추가합니다.

   | 이름 | 유형 | 값 |
   |---|---|---|
   | jcr:title | 문자열 | We.Retail 실행 |
   | sling:resourceType | 문자열 | wcm/core/components/designer |
   | cq:doctype | 문자열 | html_5 |

   ![디자인 페이지(/apps/settings/wcm/designs/we-retail-run)](assets/2018-05-07_at_1219pm.png)

   디자인 페이지(/apps/settings/wcm/designs/we-retail-run)

## 시퀀스 채널 만들기 {#create-sequence-channel}

Hello World 구성 요소는 시퀀스 채널에서 사용됩니다. 구성 요소를 테스트하려면 새 시퀀스 채널이 만들어집니다.

1. AEM 시작 메뉴에서 화면 &gt; **We.** Retail **실행 &gt;**&#x200B;채널로 **이동하여 채널을 선택합니다**.

1. 만들기 **단추** 클릭

   1. 개체 **만들기 선택**
   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. 만들기 마법사에서:

1. 템플릿 단계 - 선택** 시퀀스 채널**

   1. 속성 단계
   * 기본 탭 &gt; 제목 = **유휴 채널**
   * 채널 탭 &gt; **온라인으로 채널 만들기 선택**
   ![유휴 채널](assets/idle-channel.gif)

1. 유휴 채널의 페이지 속성을 엽니다. 디자인 필드를 업데이트하여 이전 `/apps/settings/wcm/designs/we-retail-run,`섹션에서 만든 디자인 페이지를 가리킵니다.

   ![디자인 구성 /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   /apps/settings/wcm/designs/we-retail-run을 가리키는 디자인 구성

1. 새로 만든 유휴 채널을 편집하여 엽니다.

1. 페이지 모드를 디자인 **모드로** 전환

   1. Parsys의 **스패너** 아이콘을 클릭하여 허용된 구성 요소를 구성합니다.

   1. 스크린 **그룹과 We.** Retail **실행 - 컨텐츠 그룹을** 선택합니다.
   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. 페이지 모드를 편집으로 **전환합니다**. 이제 Hello World 구성 요소를 페이지에 추가하고 다른 시퀀스 채널 구성 요소와 결합할 수 있습니다.

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. CRXDE **-Lite에서** 로 `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` 이동합니다 `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. 이제 `components` 속성에 `group:Screens`다음이 포함됩니다 `group:We.Retail Run - Content`.

   ![/apps/settings/wcm/designs/we-retail-run에서 디자인 구성](assets/2018-05-07_at_1_14pm.png)

   /apps/settings/wcm/designs/we-retail-run에서 디자인 구성

## 모든 작업 간소화 {#putting-it-all-together}

아래 비디오에서는 완성된 구성 요소와 시퀀스 채널에 구성 요소를 추가하는 방법을 보여줍니다. 그런 다음 채널이 위치 디스플레이에 추가되고 궁극적으로 스크린 플레이어에 할당됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9&captions=kor)

## 완료된 코드 {#finished-code}

다음은 자습서의 완성된 코드입니다. screens-weretail-run.ui.ap **ps-0.0.1-SNAPSHOT.zip** 및 **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** 은 컴파일된 AEM 패키지입니다. **SRC-screens-weretail-run-0.0.1.zip **은 Maven을 사용하여 배포할 수 있는 컴파일되지 않은 소스 코드입니다.

[파일 가져오기](assets/screens-weretail-runuiapps-001-snapshot.zip)

[파일 가져오기](assets/screens-weretail-runuicontent-001-snapshot.zip)

[파일 가져오기](assets/screens-weretail-run.zip)