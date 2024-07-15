---
title: 오프라인 채널
description: ContentSync 기술을 사용하여 AEM Screens Player에서 채널에 대한 오프라인 지원을 제공하는 방법에 대해 자세히 알아보십시오.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# 오프라인 채널 {#offline-channels}

Screens 플레이어는 ***ContentSync*** 기술을 사용하여 채널에 대한 오프라인 지원을 제공합니다.

플레이어는 로컬 http 서버를 사용하여 압축 해제된 콘텐츠를 제공합니다.

채널이 *online*&#x200B;을 실행하도록 구성된 경우 플레이어는 AEM 서버에 액세스하여 채널 리소스를 제공합니다. 그러나 채널이 *offline*&#x200B;을(를) 실행하도록 구성된 경우 플레이어는 로컬 http 서버에서 채널 리소스를 제공합니다.

프로세스의 워크플로우는 다음과 같습니다.

1. 원하는 페이지를 구문 분석합니다.
1. 모든 관련 에셋을 수집합니다.
1. 모든 항목을 zip 파일로 패키징합니다.
1. zip을 다운로드하고 로컬로 추출합니다.
1. 콘텐츠의 로컬 복사본을 표시합니다.

## 핸들러 업데이트 {#update-handlers}

***ContentSync***&#x200B;은(는) 업데이트 처리기를 사용하여 특정 프로젝트에 필요한 모든 페이지와 자산을 구문 분석하고 수집합니다. AEM Screens은 다음 업데이트 핸들러를 사용합니다.

### 일반 옵션 {#common-options}

* *type*: 사용할 업데이트 처리기 형식
* *경로*: 리소스에 대한 경로
* *[targetRootDirectory]*: zip 파일의 대상 폴더

<table>
 <tbody>
  <tr>
   <td><strong>유형</strong></td> 
   <td><strong>설명</strong></td> 
   <td><strong>옵션</strong></td> 
  </tr>
  <tr>
   <td><code>channels</code></td> 
   <td>채널 수집</td> 
   <td>확장: 수집할 리소스의 확장 <br /> [pathSuffix='']: 채널 경로에 추가할 접미사<br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>지정된 클라이언트 라이브러리 수집</td> 
   <td>[extension='']: css 또는 js일 수 있으므로 전자만 수집하거나 후자만 수집할 수 있습니다.</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>에셋 렌디션 수집</td> 
   <td>[renditions=[]]: 수집할 렌디션 목록입니다. 원본 렌디션의 기본값</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>경로에서 지정된 구조 복사</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### ContentSync 구성 테스트 {#testing-contentsync-configuration}

ContentSync 구성을 테스트하려면 아래 단계를 따르십시오.

1. `https://localhost:4502/libs/cq/contentsync/content/console.html` 열기
1. 목록에서 구성을 클릭합니다.
1. **캐시 지우기**&#x200B;를 클릭합니다.
1. **캐시 업데이트**&#x200B;를 클릭합니다.
1. **전체 다운로드**&#x200B;를 클릭합니다.
1. zip 파일을 추출합니다.
1. 추출된 폴더에서 로컬 서버를 시작합니다.
1. 시작 페이지를 열고 앱 상태를 확인합니다.

## 채널에 대한 오프라인 구성 활성화 {#enabling-offline-config-for-a-channel}

채널에 대한 오프라인 구성을 활성화하려면 아래 단계를 따르십시오.

1. Inspect 채널 컨텐츠를 표시하고 AEM 인스턴스(온라인)에서 요청되었는지 확인합니다.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 채널 대시보드로 이동합니다.
1. **채널 정보** 패널에서 **..**&#x200B;을(를) 클릭합니다.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 채널 속성으로 이동합니다.
1. ((채널) 탭에서 확인란이 비활성화되어 있는지 확인한 다음 **저장 및 닫기**&#x200B;를 클릭합니다.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   콘텐츠가 장치에 제대로 배포되기 전에 **오프라인 콘텐츠 업데이트**&#x200B;를 클릭하세요.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   **속성**&#x200B;의 **오프라인** 상태도 그에 따라 업데이트됩니다.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. 채널 콘텐츠를 Inspect으로 설정하고 로컬 플레이어 캐시에서 요청되었는지 확인합니다.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>사용자 지정 오프라인 리소스 핸들러의 템플릿에 대해 알아봅니다. 프로젝트에 대한 `pom.xml`의 최소 요구 사항에 대해 자세히 알아보세요. **AEM Screens용 사용자 지정 구성 요소 개발**&#x200B;에서 [사용자 지정 처리기용 템플릿](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)을 참조하십시오.
