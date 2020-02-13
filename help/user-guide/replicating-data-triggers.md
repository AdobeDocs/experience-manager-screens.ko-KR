---
title: 데이터 트리거를 복제하여 서버 게시
seo-title: 데이터 트리거를 복제하여 게시 서버
description: 데이터 트리거를 복제하여 서버를 게시합니다.
seo-description: 데이터 트리거를 복제하여 서버를 게시합니다.
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# 게시 서버에 데이터 트리거 복제 {#replicating-data-triggers}

ContextHub 및 AEM 타깃팅 엔진을 사용하여 작성/게시 설정의 데이터 트리거를 기반으로 컨텐츠를 사용자 지정할 때 모든 ContextHub 및 개인화 관련 구성은 게시될 때 채널과 함께 자동으로 복제되지 않습니다.

이 페이지에서는 이러한 구성을 별도로 게시하는 데 필요한 설명서 단계를 살펴볼 수 있습니다.

기본적으로 수동으로 게시해야 합니다.

1. ContextHub 저장소 및 UI 모듈 구성
1. 개인화 고객
1. 개인화 활동

## 게시 서버에 데이터 트리거를 복제하는 절차 {#replicating-data-triggers-publish}

서버 게시를 위한 데이터 트리거를 복제하려면 아래 절차를 따르십시오.

### ContextHub 구성 복제 {#replicating-contexthub-configurations}

1. 도구 **> 배포** > **배포** > **게시** 에이전트 **http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish**&#x200B;으로 이동합니다.
1. [연결 테스트] 단추를 클릭하여 작성자가 게시 인스턴스와 제대로 통신할 수 있는지 확인합니다
1. 테스트에 실패하는 경우 작성자와 게시 사이에 복제 에이전트 구성을 수정해야 합니다
1. 끝점 URL 파섹
1. 편집 > 가져오기 끝점
1. 배포 탭을 클릭합니다.
1. 트리 추가 라디오 단추 선택
1. 경로 브라우저에서 프로젝트의 구성 경로(예:/conf/screens/settings/cloudsettings/configuration)
1. 제출을 클릭합니다

### 대상 복제 {#replicating-audiences}

1. 도구 > 개인화 > 대상으로 이동합니다.http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. 프로젝트 폴더(예:/conf/screens/)
1. UI에서 모든 대상/세그먼트 선택
1. 게시 관리를 클릭합니다
1. 다음을 클릭합니다
1. 게시를 클릭합니다

### 활동 복제 {#replicating-activities}

1. 도구 > 개인화 > 활동으로 이동합니다.http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. 프로젝트 폴더(예:/content/campaigns/screens/...)
1. UI에서 모든 활동 선택
1. 게시 관리를 클릭합니다
1. 다음을 클릭합니다
1. 게시를 클릭합니다

> [!Note]
>ContextHub 구성 및 대상 복제는 프로젝트 설정 중에 수행되며, 활동을 복제하며 채널 내에서 타깃팅이 변경될 때마다 필요합니다.

#### 결과 {#result}

복제가 성공하면 게시 인스턴스에서 다음 구조를 확인해야 합니다(또는 프로젝트의 유사).

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`