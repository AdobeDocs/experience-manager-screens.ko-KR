---
title: 오프라인 채널
seo-title: 오프라인 채널
description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대한 오프라인 지원을 제공합니다. 처리기의 업데이트 및 채널에 대한 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
seo-description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대한 오프라인 지원을 제공합니다. 처리기의 업데이트 및 채널에 대한 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: 9da83030c5ad90f446befc7a488fac6c9435ea76

---


# 오프라인 채널 {#offline-channels}

Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대한 오프라인 지원을 ***제공합니다*** .

플레이어는 로컬 http 서버를 사용하여 압축을 푼 컨텐츠를 제공합니다.

채널이 *온라인으로*&#x200B;실행되도록 구성되면 플레이어는 AEM 서버에 액세스하여 채널 리소스를 제공하지만 채널이 *오프라인으로*&#x200B;실행되도록 구성되면 플레이어는 로컬 http 서버의 채널 리소스를 제공합니다.

프로세스에 대한 워크플로우는 다음과 같습니다.

1. 원하는 페이지를 구문 분석합니다.
1. 모든 관련 자산 수집
1. 모든 것을 zip 파일로 패키지화
1. zip을 다운로드하여 로컬에서 추출
1. 컨텐츠의 로컬 복사본 표시

## 처리기 업데이트 {#update-handlers}

ContentSync ***는*** 업데이트 핸들러를 사용하여 특정 프로젝트에 필요한 모든 페이지와 자산을 구문 분석하고 수집합니다. AEM Screens에서는 다음 업데이트 핸들러를 사용합니다.

### 일반 옵션 {#common-options}

* *유형*:사용할 업데이트 처리기 유형
* *경로*:리소스 경로
* *[targetRootDirectory]*:zip 파일의 대상 폴더

<table>
 <tbody>
  <tr>
   <td><strong>유형</strong></td> 
   <td><strong>설명</strong></td> 
   <td><strong>옵션</strong></td> 
  </tr>
  <tr>
   <td>채널</td> 
   <td>채널 수집</td> 
   <td>확장:[pathSuffix="]을(를) 수집할<br /> 리소스의 확장:채널 경로에 추가할 접미사<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>지정된 클라이언트 라이브러리 수집</td> 
   <td>[extension="]:css 또는 js를 사용하여 이전 버전만 수집하거나 후자만 수집할 수 있습니다.</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>자산 표현물 수집</td> 
   <td>[표현물=[]]:수집할 변환 목록. 기본적으로 원본 변환</td> 
  </tr>
  <tr>
   <td>복사</td> 
   <td>경로에서 지정된 구조 복사</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### ContentSync 구성 테스트 {#testing-contentsync-configuration}

아래 절차에 따라 ContentSync 구성을 테스트합니다.

1. 열기 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 목록에서 구성을 선택합니다.
1. 캐시 지우기를 클릭합니다.
1. 캐시 업데이트를 클릭합니다.
1. 전체 다운로드를 클릭합니다.
1. zip 파일 추출
1. 압축을 푼 폴더에서 로컬 서버 시작
1. 시작 페이지를 열고 앱 상태 확인

## 채널에 대한 오프라인 구성 활성화 {#enabling-offline-config-for-a-channel}

아래 절차에 따라 채널에 대한 오프라인 구성을 활성화합니다.

1. 채널 컨텐츠를 검사하고 AEM 인스턴스(온라인)에서 요청되었는지 확인합니다.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 채널 대시보드로 이동하고 **..** 를 **사용하여** 속성을 변경합니다.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 채널 속성으로 이동하고 채널 탭 아래에서 확인란이 비활성화되어 있는지 **확인합니다** . 저장 **및 닫기를 클릭합니다**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   콘텐트가 장치에 제대로 배포되기 전에 [오프라인 콘텐트 업데이트] **를 클릭합니다**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   속성 **아래의 오프라인** 상태도 **그에 따라** 업데이트됩니다.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. 채널 컨텐츠를 검사하고 로컬 플레이어 캐시에서 요청되었는지 확인합니다.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
> 사용자 지정 오프라인 리소스 핸들러에 대한 템플릿과 해당 특정 프로젝트에 대한 최소 요구 사항에 대한 자세한 내용은 AEM Screens용 사용자 `pom.xml` 지정 구성 요소 [개발의](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) 사용자 지정 핸들러에 대한 템플릿을 참조하십시오 ****.