---
title: 오프라인 채널
seo-title: 오프라인 채널
description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대한 오프라인 지원을 제공합니다. 핸들러 업데이트 및 채널에 대한 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
seo-description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대한 오프라인 지원을 제공합니다. 핸들러 업데이트 및 채널에 대한 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: 스크린 개발
role: 개발자
level: 중간
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 4%

---


# 오프라인 채널 {#offline-channels}

Screens 플레이어는 ***ContentSync*** 기술을 활용하여 채널에 대한 오프라인 지원을 제공합니다.

플레이어는 로컬 http 서버를 사용하여 압축 해제된 컨텐츠를 제공합니다.

채널이 *online*&#x200B;을(를) 실행하도록 구성된 경우 플레이어는 AEM 서버에 액세스하여 채널 리소스를 제공하지만 채널이 *offline*&#x200B;을 실행하도록 구성된 경우, 플레이어는 로컬 http 서버의 채널 리소스를 제공합니다.

프로세스에 대한 워크플로우는 다음과 같습니다.

1. 원하는 페이지를 구문 분석합니다.
1. 모든 관련 자산 수집
1. zip 파일의 모든 항목 패키지
1. zip을 다운로드하여 로컬에 추출합니다.
1. 컨텐츠의 로컬 복사본 표시

## 처리기 업데이트 {#update-handlers}

***ContentSync***&#x200B;는 업데이트 핸들러를 사용하여 특정 프로젝트에 필요한 모든 페이지와 자산을 구문 분석하고 수집합니다. AEM Screens에서는 다음과 같은 업데이트 핸들러를 사용합니다.

### 일반 옵션 {#common-options}

* *유형*:사용할 업데이트 처리기 유형
* *경로*:리소스에 대한 경로
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
   <td>확장:<br /> [pathSuffix="]을(를) 수집할 리소스의 확장:접미사를 추가하여 채널 경로<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>지정된 클라이언트 라이브러리 수집</td> 
   <td>[extension="]:css 또는 js를 사용하여 이전 버전만 수집하고 후자보다</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>자산 표현물 수집</td> 
   <td>[표현물=[]]:수집할 변환 목록. 기본값은 원래 변환입니다.</td> 
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
1. 추출된 폴더에서 로컬 서버 시작
1. 시작 페이지를 열고 앱 상태 확인

## 채널 {#enabling-offline-config-for-a-channel}에 대한 오프라인 구성 활성화

채널에 대한 오프라인 구성을 활성화하려면 아래 절차를 따르십시오.

1. Inspect 채널 컨텐츠를 작성하고 AEM 인스턴스(온라인)에서 요청되었는지 확인합니다.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 채널 대시보드로 이동하고 **...을 클릭합니다.속성을 변경하려면**&#x200B;채널 정보&#x200B;**패널의**.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 채널 속성으로 이동하고 **채널** 탭 아래에서 확인란이 비활성화되었는지 확인합니다. **저장 후 닫기**&#x200B;를 클릭합니다.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   콘텐츠가 장치에 제대로 배포되기 전에 **오프라인 콘텐츠 업데이트**&#x200B;를 클릭합니다.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   **PROPERTIES**&#x200B;의 **오프라인** 상태도 그에 따라 업데이트됩니다.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect에서 채널 내용을 확인하고 로컬 플레이어 캐시에서 요청되었는지 확인합니다.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>사용자 지정 오프라인 리소스 핸들러에 대한 템플릿과 해당 특정 프로젝트에 대한 `pom.xml`의 최소 요구 사항에 대한 자세한 내용은 **AEM Screens**&#x200B;용 사용자 지정 구성 요소 개발](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)의 [사용자 지정 핸들러에 대한 템플릿을 참조하십시오.