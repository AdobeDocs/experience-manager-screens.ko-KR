---
title: 데이터 트리거를 게시서버로 복제
seo-title: 데이터 트리거를 복제하여 서버 게시
description: 데이터 트리거를 복제하여 서버를 게시합니다.
seo-description: 데이터 트리거를 복제하여 서버를 게시합니다.
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 2%

---


# 게시 서버에 데이터 트리거 복제 {#replicating-data-triggers}

ContextHub 및 AEM Targeting 엔진을 사용하여 작성/게시 설정의 데이터 트리거를 기반으로 컨텐츠를 사용자 지정하는 경우, 게시될 때 모든 ContextHub 및 개인화 관련 구성이 채널에서 자동으로 복제되지 않습니다.

이 페이지에서는 이러한 구성을 별도로 게시하는 데 필요한 설명서 단계를 살펴볼 수 있습니다.

기본적으로 수동으로 게시해야 합니다.

1. ContextHub 저장소 및 UI 모듈 구성
1. 개인화 고객
1. 개인화 활동

## 게시 서버에 데이터 트리거를 복제하는 단계 {#replicating-data-triggers-publish}

서버를 게시하기 위해 데이터 트리거를 복제하려면 아래 절차를 따르십시오.

### 1단계: ContextHub 구성 복제 {#replicating-contexthub-configurations}

1. [ **도구** ] > [ **배포** ] **> [배포** ] **> [게시 에이전트]** 로 이동하고 게시 에이전트를 클릭하여 설정을 구성합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >또는 을 사용하여 화면 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 으로 직접 이동하여 연결을 구성하고 테스트할 수 있습니다.

1. 작업 **표시줄에서 연결** 테스트를 클릭하여 아래 그림과 같이 게시 인스턴스와 작성자의 통신을 확인합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >테스트에 실패하는 경우 작성자 및 게시 인스턴스 간 복제 에이전트 구성을 수정해야 합니다. 자세한 내용은 [테스트 연결 문제](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 해결을 참조하십시오.

1. [ **배포 에이전트** ] 화면 트리에서 **추가를** 선택하고 프로젝트의 구성 경로를 선택합니다(예: `/conf/screens/settings/cloudsettings/configuration`).

1. 제출을 **클릭합니다**.

### 대상자 복제 {#replicating-audiences}

1. AEM 인스턴스 > **개인화** > 대상 **으로 이동하거나** 를 사용하여 직접 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 탐색합니다.

1. 프로젝트 폴더로 드릴다운합니다(예: `/conf/screens/`.).

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 사용자 인터페이스에서 모든 대상 및 세그먼트를 선택합니다.

1. 작업 **표시줄에서 [게시** 관리]를 클릭합니다.

1. [ **다음** ]과 [ **게시]를 클릭합니다**.

### 활동 복제  {#replicating-activities}

1. AEM 인스턴스 > **개인화** > 활동 **으로** 이동하거나 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 를 사용하여 직접탐색합니다.

1. 프로젝트 폴더(즉, `/content/campaigns/screens/…`

1. 사용자 인터페이스에서 모든 활동을 선택합니다.

1. 작업 **표시줄에서 [게시** 관리]를 클릭합니다.

1. [ **다음** ]과 [ **게시]를 클릭합니다**.

>[!IMPORTANT]
>
>활동을 복제하는 동안 ContextHub 구성 및 대상 복제가 수행되며 채널 내에서 타깃팅이 변경될 때마다 필요합니다.

#### 결과 {#result}

복제가 성공하면 게시 인스턴스에서 다음 구조를 확인해야 합니다(또는 프로젝트의 유사).

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 테스트 연결 문제 해결 {#troubleshoot-test}

ContextHub 구성을 복제하는 동안 테스트 연결이 실패하는 경우 아래의 섹션에 따라 문제를 해결하십시오.

1. 도구 > **배포** > **배포** > **게시**&#x200B;에이전트로이동합니다.

1. 작업 표시줄에서 **편집을** 클릭하고 **Importer 끝점** 필드의 끝점 URL이 Distribution Agent의 게시 서버 URL을 가리키는지 확인합니다.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 기본 관리자 자격 증명을 사용하지 않는 경우 다른 사용자 이름과 암호로 배포 에이전트를 구성해야 합니다.

   아래 단계를 따르십시오.

   1. 도구 > **작업****>** 웹 콘솔 `http://localhost:4502/system/console/configMgr`으로 이동하여 **Adobe Experience Manager 웹 콘솔 화면**&#x200B;을 엽니다.
   1. Apache **Sling 배포 전송 자격 증명 검색 - DistributionTransportSecretProvider 기반 사용자 자격 증명**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 예를 들어 slingTransportSecretProvider와 같은 **이름**, **사용자 이름****및**&#x200B;암호를 *채워 구성을*&#x200B;만듭니다.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. **저장**&#x200B;을 클릭합니다
   1. Apache Sling `Cmd +F` Distribution Agent - Forward Agents Factory **를 검색하여 구성을 열고** 전송 비밀 공급자를 검색하십시오 ****.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 다음으로 `(name=default)` 업데이트합니다 `(name=slingTransportSecretProvider)`.
   1. 저장 **을** 클릭하고 AEM 인스턴스의 **배포 에이전트** 화면에서 테스트 연결을 다시 실행합니다.
