---
title: 오프라인 채널
seo-title: 오프라인 채널
description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대해 오프라인 지원을 제공합니다. 채널의 업데이트 핸들러와 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
seo-description: 'AEM Screens 플레이어는 ContentSync 기술을 활용하여 채널에 대해 오프라인 지원을 제공합니다. 채널의 업데이트 핸들러와 오프라인 구성 활성화에 대한 자세한 내용을 보려면 이 페이지를 따르십시오.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: 화면 개발
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 4%

---

# 오프라인 채널 {#offline-channels}

Screens 플레이어는 ***ContentSync*** 기술을 활용하여 채널에 대해 오프라인 지원을 제공합니다.

플레이어는 로컬 http 서버를 사용하여 압축 해제된 컨텐츠를 제공합니다.

채널이 *online*&#x200B;을 실행하도록 구성되면 플레이어가 AEM 서버에 액세스하여 채널 리소스를 제공하지만, 채널이 *offline*&#x200B;을 실행하도록 구성되면 플레이어가 로컬 http 서버에서 채널 리소스를 제공합니다.

프로세스에 대한 워크플로우는 다음과 같습니다.

1. 원하는 페이지를 구문 분석합니다
1. 모든 관련 자산 수집
1. 모든 것을 zip 파일로 패키지합니다.
1. zip을 다운로드하고 로컬로 추출합니다
1. 컨텐츠의 로컬 복사본 표시

## 처리기 업데이트 {#update-handlers}

***ContentSync***&#x200B;는 업데이트 처리기를 사용하여 특정 프로젝트에 필요한 모든 페이지와 자산을 구문 분석하고 수집합니다. AEM Screens에서는 다음 업데이트 처리기를 사용합니다.

### 일반 옵션 {#common-options}

* *유형*:사용할 업데이트 처리기 유형
* *경로*:리소스 경로
* *[targetRootDirectory]*:zip 파일의 타겟 폴더

<table>
 <tbody>
  <tr>
   <td><strong>유형</strong></td> 
   <td><strong>설명</strong></td> 
   <td><strong>옵션</strong></td> 
  </tr>
  <tr>
   <td>채널</td> 
   <td>채널을 수집합니다</td> 
   <td>확장:<br /> [pathSuffix="]를 수집할 리소스의 확장입니다.채널 경로<br />에 추가할 접미사 </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>지정된 클라이언트 라이브러리 수집</td> 
   <td>[extension="]:css 또는 js 중 하나를 사용하여 이전 버전만 수집하거나 후자만 수집할 수 있습니다.</td> 
  </tr>
  <tr>
   <td>자산 표현물</td> 
   <td>자산 표현물 수집</td> 
   <td>[표현물=[]]:수집할 표현물 목록. 기본값은 원래 표현물입니다</td> 
  </tr>
  <tr>
   <td>복사</td> 
   <td>경로에서 지정된 구조 복사</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### ContentSync 구성 테스트 {#testing-contentsync-configuration}

아래 절차에 따라 ContentSync 구성을 테스트하십시오.

1. 열기 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 목록에서 구성을 선택합니다
1. 캐시 지우기 를 클릭합니다
1. Update Cache 클릭
1. 전체 다운로드를 클릭합니다
1. zip 파일 추출
1. 추출된 폴더에서 로컬 서버 시작
1. 시작 페이지를 열고 앱 상태를 확인합니다

## 채널 {#enabling-offline-config-for-a-channel}에 대해 오프라인 구성 활성화

채널에 대해 오프라인 구성을 활성화하려면 아래 절차를 따르십시오.

1. Inspect 채널 컨텐츠를 AEM 인스턴스(온라인)에서 요청되었는지 확인합니다.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 채널 대시보드로 이동하고 **..속성을 변경하려면**&#x200B;채널 정보&#x200B;**패널에서** 을 클릭하십시오.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 채널 속성으로 이동하고 **채널** 탭 아래에서 확인란이 비활성화되어 있는지 확인합니다. **저장 후 닫기**&#x200B;를 클릭합니다.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   콘텐츠가 장치에 제대로 배포되기 전에 **오프라인 콘텐츠 업데이트**&#x200B;를 클릭하십시오.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   **PROPERTIES**&#x200B;의 **오프라인** 상태도 그에 따라 업데이트됩니다.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect 채널 콘텐츠를 캡처하고 로컬 Player-Cache에서 요청되었는지 확인합니다.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>사용자 지정 오프라인 리소스 핸들러의 템플릿과 해당 특정 프로젝트에 대한 `pom.xml`의 최소 요구 사항에 대해 자세히 알려면 **AEM Screens용 사용자 지정 구성 요소 개발**&#x200B;에서 [사용자 지정 핸들러용 템플릿](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)을 참조하십시오.
