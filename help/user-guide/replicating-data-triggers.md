---
title: 데이터 트리거를 복제하여 서버 게시
seo-title: 데이터 트리거를 복제하여 게시 서버
description: 데이터 트리거를 복제하여 서버를 게시합니다.
seo-description: 데이터 트리거를 복제하여 서버를 게시합니다.
translation-type: tm+mt
source-git-commit: 47e0204ea734a1348385ddd3c7108038c88d1933

---


# 게시 서버에 데이터 트리거 복제 {#replicating-data-triggers}

ContextHub 및 AEM 타깃팅 엔진을 사용하여 작성/게시 설정의 데이터 트리거를 기반으로 컨텐츠를 사용자 지정할 때 모든 ContextHub 및 개인화 관련 구성은 게시될 때 채널과 함께 자동으로 복제되지 않습니다.

이 페이지에서는 이러한 구성을 별도로 게시하는 데 필요한 설명서 단계를 살펴볼 수 있습니다.

기본적으로 수동으로 게시해야 합니다.

1. ContextHub 저장소 및 UI 모듈 구성
1. 개인화 고객
1. 개인화 활동

## 게시 서버에 데이터 트리거를 복제하는 절차 {#replicating-data-triggers-publish}

서버를 게시하기 위해 데이터 트리거를 복제하려면 아래 절차를 따르십시오.

### 1단계:ContextHub 구성 복제 {#replicating-contexthub-configurations}

1. [도구] > [ **배포** ] **>** [ **배포** ] > [게시 에이전트 **]** 로 이동하고 게시 에이전트를 클릭하여 설정을 구성합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >또는 [링크를](http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish) 사용하여 화면으로 바로 이동하여 연결을 구성하고 테스트할 수 있습니다.

1. 작업 **표시줄에서 연결** 테스트를 클릭하여 아래 그림과 같이 게시 인스턴스와 작성자의 통신을 확인합니다.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >테스트가 실패할 경우 작성자 및 게시 인스턴스 간 복제 에이전트 구성을 수정해야 합니다. 자세한 내용은 [테스트 연결](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 문제 해결을 참조하십시오.

1. 위의 **화면에서 편집을** 클릭하고 Importer 끝점 필드의 끝점 URL이 **배포 에이전트의** 게시 서버 URL을 가리키는지 확인합니다.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. [ **배포 에이전트** ] **화면 트리에서** [추가]를 선택하고 프로젝트의 구성 경로(즉, 프로젝트에 대한 구성 경로)를 선택합니다 `/conf/screens/settings/cloudsettings/configuration)`.

1. 제출을 **클릭합니다**

### 대상 복제 {#replicating-audiences}

1. 도구 > **개인화** > **대상자** 로 **이동하거나** 링크를 사용하여 직접 [](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html) 탐색합니다.

1. 프로젝트 폴더 즉, 이렇게 드릴다운합니다 `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. 사용자 인터페이스에서 모든 대상과 세그먼트를 선택합니다.

1. 작업 **표시줄에서** 게시 관리를 클릭합니다.

1. 다음 **및 게시를** **클릭합니다**.

### 활동 복제 {#replicating-activities}

1. 도구 > **개인화** > **활동으로** 이동하거나 **링크를 사용하여** 직접 [](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html) 탐색합니다.

1. 프로젝트 폴더 즉, 이렇게 드릴다운합니다 `/content/campaigns/screens/…`.

1. 사용자 인터페이스에서 모든 활동을 선택합니다.

1. 작업 **표시줄에서** 게시 관리를 클릭합니다.

1. 다음 **및 게시를** **클릭합니다**.

   > [!Note]
   >ContextHub 구성 및 대상 복제는 프로젝트 설정 중에 수행되며, 활동을 복제하며 채널 내에서 타깃팅이 변경될 때마다 필요합니다.

#### 결과 {#result}

복제가 성공하면 게시 인스턴스에서 다음 구조를 확인해야 합니다(또는 프로젝트의 유사).

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 테스트 연결 문제 해결 {#troubleshoot-test}

ContextHub 구성을 복제하는 동안 테스트 연결이 실패하는 경우 아래 섹션을 참조하여 문제를 해결하십시오.

1. Importer **끝점** 필드로 이동하고 끝점 URL이 배포 에이전트의 게시 서버 URL을 가리키는지 확인합니다.

1. 기본 자격 증명을 사용하지 않는 경우 다른 관리자 암호로 배포 에이전트를 구성해야 합니다.
아래 단계를 따르십시오.

   1. 도구 > **작업** > 웹 콘솔** `http://localhost:4502/system/console/configMgr`으로 이동하여 Adobe Experience **Manager 웹 콘솔 화면을**&#x200B;엽니다.

   1. Apache Sling **배포 전송 자격 증명 검색 - 사용자 자격 증명 기반 DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 예를 들어 slingTransportSecretProvider와 같은 **Name**, **사용자 이름** 및 **암호를***채워서*&#x200B;구성을 만듭니다..
   1. **저장**&#x200B;을 클릭합니다

   1. 를 사용하여 배포 에이전트의 이름을 `Cmd +F`검색합니다.

   1. 을 클릭하여 배포 에이전트 osgi 구성을 엽니다.

   1. osgi 구성에서 전송 암호 공급자를 찾아 다음으로 업데이트합니다 `"(name=slingTransportSecretProvider)"`.

   1. 저장을 **클릭하고** 테스트 연결을 실행합니다.

