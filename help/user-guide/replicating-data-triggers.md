---
title: Publish 서버에 데이터 트리거 복제
description: AEM Screens용 게시 서버에 데이터 트리거를 복제하는 방법을 알아봅니다.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# Publish 서버에 데이터 트리거 복제 {#replicating-data-triggers}

ContextHub 및 AEM 타깃팅 엔진을 사용하여 작성자/게시 설정의 데이터 트리거를 기반으로 콘텐츠를 사용자 정의하는 경우 게시할 때 모든 ContextHub 및 Personalization 관련 구성이 채널과 함께 자동으로 복제되지 않습니다.

이 페이지는 이러한 구성을 별도로 게시하는 데 필요한 수동 단계를 학습하는 데 도움이 됩니다.

이 프로세스는 기본적으로 다음을 수동으로 게시합니다.

1. ContextHub 저장소 및 UI 모듈 구성
1. Personalization 대상
1. Personalization 활동

## Publish 서버에 데이터 트리거를 복제하는 단계 {#replicating-data-triggers-publish}

게시 서버에 데이터 트리거를 복제하려면 아래 단계를 따르십시오.

### 1단계: ContextHub 구성 복제 {#replicating-contexthub-configurations}

1. 설정을 구성할 수 있도록 **도구** > **배포** > **배포** > **Publish 에이전트**(으)로 이동하고 게시 에이전트를 클릭합니다.

   ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >또는 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`을(를) 사용하여 화면으로 직접 이동하여 연결을 구성하고 테스트할 수 있습니다.

1. 작업 표시줄에서 **연결 테스트**&#x200B;를 클릭하면 다음과 같이 작성자와 게시 인스턴스의 통신을 확인할 수 있습니다.

   ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >테스트가 실패하면 작성자와 게시 인스턴스 간의 복제 에이전트 구성을 수정하십시오. 자세한 내용은 [테스트 연결 문제 해결](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)을 참조하십시오.

1. **배포 에이전트** 화면 트리에서 **추가**&#x200B;를 클릭하고 프로젝트의 구성 경로(예: `/conf/screens/settings/cloudsettings/configuration`)를 클릭하십시오.

1. **제출**&#x200B;을 클릭합니다.

### 대상자 복제 {#replicating-audiences}

1. AEM 인스턴스 > **Personalization** > **대상**(으)로 이동하거나 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`을(를) 사용하여 직접 이동합니다.

1. 프로젝트 폴더(예: `/conf/screens/`)로 드릴다운합니다.

   ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 사용자 인터페이스에서 모든 대상 및 세그먼트를 클릭합니다.

1. 작업 표시줄에서 **게시 관리**&#x200B;를 클릭합니다.

1. **다음** 및 **Publish**&#x200B;을 클릭합니다.

### 활동 복제 {#replicating-activities}

1. AEM 인스턴스 > **Personalization** > **활동**(으)로 이동하거나 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`을(를) 사용하여 직접 이동합니다.

1. 프로젝트 폴더, 즉 `/content/campaigns/screens/…`(으)로 드릴다운합니다.

1. 사용자 인터페이스에서 모든 활동을 클릭합니다.

1. 작업 표시줄에서 **게시 관리**&#x200B;를 클릭합니다.

1. **다음** 및 **Publish**&#x200B;을 클릭합니다.

>[!IMPORTANT]
>
>ContextHub 구성 및 대상자 복제는 프로젝트 설정 중에 수행되는 반면 활동을 복제합니다. 이는 채널 내에서 타깃팅을 변경할 때마다 필요합니다.

#### 결과 {#result}

복제가 성공하면 게시 인스턴스(또는 프로젝트의 경우 유사)에서 다음 구조를 확인해야 합니다.

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 테스트 연결 문제 해결 {#troubleshoot-test}

ContextHub 구성을 복제하는 동안 테스트 연결에 실패하는 경우 아래 섹션에 문제 해결을 참조하십시오.

1. **도구** > **배포** > **배포** > **Publish 에이전트**&#x200B;로 이동합니다.

1. 작업 표시줄에서 **편집**&#x200B;을 클릭하고 **가져오기 끝점** 필드의 끝점 URL도 배포 에이전트의 게시 서버 URL을 가리키는지 확인하십시오.
   ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 기본 관리자 자격 증명을 사용하지 않는 경우에는 다른 사용자 이름과 암호로 분배 에이전트를 구성해야 합니다.

   아래 단계를 따르십시오.

   1. **Adobe Experience Manager 웹 콘솔 화면**&#x200B;을 열 수 있도록 도구 > **작업** > **웹 콘솔** `http://localhost:4502/system/console/configMgr`로 이동합니다.
   1. **Apache Sling 배포 전송 자격 증명 검색 - 사용자 자격 증명 기반 DistributionTransportSecretProvider**

      ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. **이름**, **사용자 이름** 및 **암호**&#x200B;를 채워 구성을 만듭니다(예: *slingTransportSecretProvider*).

      ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. **저장** 클릭
   1. `Cmd +F`을(를) 사용하여 **Apache Sling Distribution Agent - Forward Agents Factory**&#x200B;를 검색하여 구성을 열고 **전송 비밀 공급자**&#x200B;를 검색합니다.

      ![이미지1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. `(name=default)`을(를) `(name=slingTransportSecretProvider)`(으)로 업데이트합니다.
   1. **저장**&#x200B;을 클릭하고 AEM 인스턴스의 **배포 에이전트** 화면에서 다시 테스트 연결을 실행하십시오.
