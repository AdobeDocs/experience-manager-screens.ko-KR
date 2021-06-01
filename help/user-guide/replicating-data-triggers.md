---
title: 게시 서버에 데이터 트리거 복제
seo-title: 게시 서버에 데이터 트리거 복제
description: 게시 서버에 데이터 트리거를 복제하는 방법을 배우려면 이 페이지를 따르십시오.
seo-description: 게시 서버에 데이터 트리거를 복제합니다.
feature: 화면 관리, 데이터 트리거
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# 게시 서버에 데이터 트리거 복제 {#replicating-data-triggers}

ContextHub 및 AEM 타깃팅 엔진을 사용하여 작성자/게시 설정에서 데이터 트리거를 기반으로 컨텐츠를 사용자 지정하는 경우 게시되면 모든 ContextHub 및 Personalization 관련 구성이 채널로 자동으로 복제되지 않습니다.

이러한 구성을 별도로 게시하는 데 필요한 설명서 단계를 알아보려면 이 페이지를 따르십시오.

기본적으로 수동 게시로 제공됩니다.

1. ContextHub 저장소 및 UI 모듈 구성
1. 개인화 대상
1. 개인화 활동

## 게시 서버에 데이터 트리거를 복제하는 단계 {#replicating-data-triggers-publish}

게시 서버에 데이터 트리거를 복제하려면 아래 단계를 따르십시오.

### 1단계:ContextHub 구성 복제 {#replicating-contexthub-configurations}

1. **도구** > **배포** > **배포** > **게시 에이전트**&#x200B;로 이동한 다음 게시 에이전트를 클릭하여 설정을 구성합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >또는 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 을 사용하여 화면으로 직접 이동하여 연결을 구성하고 테스트할 수 있습니다.

1. 아래 그림과 같이 작업 표시줄에서 **연결 테스트**&#x200B;를 클릭하여 게시 인스턴스와 작성자의 통신을 확인합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >테스트가 실패하면 작성자 및 게시 인스턴스 간의 복제 에이전트 구성을 수정해야 합니다. 자세한 내용은 [테스트 연결 문제 해결](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 을 참조하십시오.

1. **분배 에이전트** 화면 트리에서 **추가**&#x200B;를 선택하고 프로젝트에 대한 구성 경로를 선택합니다(예: `/conf/screens/settings/cloudsettings/configuration`).

1. **제출**&#x200B;을 클릭합니다.

### 대상 복제 {#replicating-audiences}

1. AEM 인스턴스 > **개인화** > **대상**&#x200B;으로 이동하거나 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`를 사용하여 직접 탐색합니다.

1. 프로젝트 폴더로 드릴다운합니다(예: `/conf/screens/`).

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 사용자 인터페이스에서 모든 대상 및 세그먼트를 선택합니다.

1. 작업 표시줄에서 **게시 관리**&#x200B;를 클릭합니다.

1. **다음** 및 **게시**&#x200B;를 클릭합니다.

### 활동 복제 {#replicating-activities}

1. AEM 인스턴스 > **개인화** > **활동**&#x200B;으로 이동하거나 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`를 사용하여 직접 탐색합니다.

1. 프로젝트 폴더(즉, `/content/campaigns/screens/…`)로 드릴다운합니다.

1. 사용자 인터페이스에서 모든 활동을 선택합니다.

1. 작업 표시줄에서 **게시 관리**&#x200B;를 클릭합니다.

1. **다음** 및 **게시**&#x200B;를 클릭합니다.

>[!IMPORTANT]
>
>ContextHub 구성 및 대상자 복제가 프로젝트 설정 중에 수행되는 반면, 채널 내에서 타겟팅이 변경될 때마다 활동을 복제해야 합니다.

#### 결과 {#result}

복제가 성공하면 게시 인스턴스에서 다음 구조를 확인해야 합니다(또는 프로젝트의 비슷한 구조).

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 테스트 연결 문제 해결 {#troubleshoot-test}

ContextHub 구성을 복제하는 동안 테스트 연결이 실패하는 경우 문제 해결을 위해 아래 섹션을 따르십시오.

1. 도구 > **배포** > **배포** > **게시 에이전트**&#x200B;로 이동합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하고 **Importer Endpoints** 필드의 끝점 URL도 배포 에이전트의 게시 서버 URL을 가리키는지 확인합니다.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 기본 관리자 자격 증명을 사용하지 않는 경우 다른 사용자 이름과 암호로 분배 에이전트를 구성해야 합니다.

   아래 단계를 따르십시오.

   1. 도구 > **작업** > **웹 콘솔** `http://localhost:4502/system/console/configMgr`로 이동하여 **Adobe Experience Manager 웹 콘솔 화면**&#x200B;을 엽니다.
   1. **Apache Sling Distribution Transport Credentials - DistributionTransportSecretProvider** 기반 사용자 자격 증명을 검색합니다.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. **Name**, **사용자 이름** 및 **암호**&#x200B;을(를) 만들어 구성을 만듭니다(예: *slingTransportSecretProvider*).

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. **저장**&#x200B;을 클릭합니다
   1. `Cmd +F` 을 사용하여 **Apache Sling Distribution Agent - Forward Agents Factory**&#x200B;를 검색하여 구성을 열고 **전송 암호 공급자**&#x200B;를 검색합니다.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. `(name=default)`을 `(name=slingTransportSecretProvider)`로 업데이트합니다.
   1. **저장**&#x200B;을 클릭하고 AEM 인스턴스의 **분배 에이전트** 화면에서 테스트 연결을 다시 실행합니다.
