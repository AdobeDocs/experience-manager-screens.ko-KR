---
title: 스크린 복제 에이전트 구성
description: 스크린 복제 에이전트를 구성하는 방법에 대한 정보를 보려면 이 페이지를 따르십시오.
role: Developer
level: Intermediate
source-git-commit: 99d66e5ac4239a6e43c15bb835f1e41ca94d908b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 5%

---


# 스크린 복제 에이전트 구성 {#configuring-screens-replication-agent}

다음 페이지에서는 스크린 복제 에이전트를 구성하는 방법에 대해 설명합니다.

>[!NOTE]
>스크린 복제 에이전트에 대한 자세한 내용은 [화면 복제 에이전트 및 명령](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Screens 복제 에이전트의 구성을 완료하려면 두 섹션을 모두 완료해야 합니다.

1. [사용자 활성화 및 암호 업데이트](#enable-users)
1. [화면 복제 에이전트 업데이트](#replicate-agent)

## 사용자 활성화 및 암호 업데이트 {#enable-users}

아래 단계를 따르십시오.

1. AEM 인스턴스로 이동합니다.

1. 도구 —> 를 클릭합니다. **보안** —> **사용자**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 검색 대상 **screens-receiver-user**.

1. 을(를) 선택합니다 **screens-receiver-user** 을(를) 클릭합니다. **활성화** 작업 표시줄.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 클릭 **확인** 확인합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication3.png)

   사용자를 활성화하면 **screens-receiver-user** 로서의 **활성화됨** 아래에 **상태** 필드.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 을(를) 선택합니다 **screens-receiver-user** 을(를) 클릭합니다. **속성** 작업 표시줄.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 클릭 **암호 변경** 아래에 **계정 설정** 에서 **세부 사항** 탭 을 참조하십시오.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 에 새 암호를 입력합니다. **암호 변경** 대화 상자를 클릭하고 **저장**.

   >[!NOTE]
   >을 입력해야 합니다. **관리** in **암호** 필드.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 클릭 **저장 및 닫기**.

1. 을(를) 선택합니다 **screens-receiver-user** 을(를) 클릭합니다. **활성화** 작업 표시줄.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 클릭 **확인** 확인합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 을(를) 선택합니다 **screens-receiver-user** 을(를) 클릭합니다. **비활성화** 작업 표시줄.

   >[!IMPORTANT]
   > 비활성화 **screens-receiver-user** 작성자 인스턴스에서만 이 사용자를 비활성화하고 게시 인스턴스의 모든 사용자가 여전히 활성 상태로 유지됩니다. 클릭하지 않음 **비활성화** 작업 표시줄에서 비활성화를 사용하면 게시 인스턴스에서도 사용자가 제거됩니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 클릭 **확인** 확인합니다.

## 화면 복제 에이전트 업데이트 {#replicate-agent}

Screens 복제 에이전트의 설정을 업데이트하려면 아래 섹션을 따르십시오.

1. AEM 인스턴스로 이동합니다.

1. 도구 —> 를 클릭합니다. **배포** —> **복제**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 클릭 **작성자의 에이전트**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 문자가 있는 링크를 검색합니다. **S** 아래 그림과 같이 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 클릭 **편집**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 확인 **활성화됨** 에서 **설정** 탭.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 다음으로 이동 **전송** 탭에서 **에이전트 설정** 대화 상자를 열고, [사용자 활성화 및 암호 업데이트](#enable-users). 클릭 **확인**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. 이전 단계를 완료하면 을(를) 클릭합니다 **연결 테스트** 연결을 확인합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   연결 확인이 성공하면 Screens 복제 에이전트 구성을 완료했습니다.