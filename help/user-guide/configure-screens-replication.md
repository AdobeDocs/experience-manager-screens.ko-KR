---
title: Screens 복제 에이전트 구성
description: Screens 복제 에이전트를 구성하는 방법에 대해 알아봅니다.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 5%

---

# Screens 복제 에이전트 구성 {#configuring-screens-replication-agent}

이 다음 페이지에서는 Screens 복제 에이전트를 구성하는 방법을 설명합니다.

## 목표 {#objective}

Screens 복제 에이전트는 *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* 및 더 많은 이러한 값과 같은 명령 데이터를 게시에서 작성자로 가져오는 역할을 합니다. 작성자가 장치 ping을 표시할 수 있도록 이 에이전트를 구성해야 합니다.

>[!NOTE]
>Screens 복제 에이전트에 대한 자세한 내용은 [Screens 복제 에이전트 및 명령](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands)을 참조하세요.

Screens 복제 에이전트에 대한 구성을 완료하려면 다음 두 섹션을 모두 완료하십시오.

1. [사용자 활성화 및 암호 업데이트](#enable-users)
1. [Screens 복제 에이전트에 대한 설정 업데이트](#replicate-agent)

## 사용자 활성화 및 암호 업데이트 {#enable-users}

사용자를 활성화하고 `screens-receiver-user`의 암호를 업데이트하려면 아래 단계를 따르십시오.

>[!NOTE]
>보안상의 이유로 `screens-receiver-user`의 관리자 암호를 사용하지 않는 것이 좋습니다.

1. AEM 작성자 인스턴스로 이동합니다.

1. 도구 > **보안** > **사용자**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. **`screens-receiver-user`** 검색

1. **`screens-receiver-user`**&#x200B;을(를) 클릭하고 작업 표시줄에서 **사용**&#x200B;을(를) 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 확인하려면 **확인**&#x200B;을 클릭하세요.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication3.png)

   사용자를 활성화하면 **상태** 필드 아래에 **`screens-receiver-user`**&#x200B;이(가) **활성화됨**(으)로 표시됩니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. **`screens-receiver-user`**&#x200B;을(를) 클릭하고 작업 표시줄에서 **속성**&#x200B;을(를) 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 아래 그림과 같이 **세부 정보** 탭에서 **계정 설정** 아래의 **암호 변경**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. **암호 변경** 대화 상자에 새 암호를 입력하고 **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >**암호** 필드에 기존 관리자 암호를 입력하십시오.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. **저장 및 닫기**&#x200B;를 클릭합니다.

1. **`screens-receiver-user`**&#x200B;을(를) 클릭하고 작업 표시줄에서 **활성화**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 확인하려면 **확인**&#x200B;을 클릭하세요.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. **`screens-receiver-user`**&#x200B;을(를) 클릭하고 작업 표시줄에서 **비활성화**&#x200B;를 클릭합니다.

   >[!IMPORTANT]
   > **`screens-receiver-user`**&#x200B;을(를) 사용하지 않도록 설정하면 이 사용자가 작성 인스턴스에서만 사용할 수 없게 되며 게시 인스턴스의 모든 사용자는 활성 상태로 유지됩니다. 비활성화하면 게시 인스턴스에서도 사용자가 제거되므로 작업 표시줄에서 **비활성화**&#x200B;를 클릭하지 마십시오.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 확인하려면 **확인**&#x200B;을 클릭하세요.

## Screens 복제 에이전트에 대한 설정 업데이트 {#replicate-agent}

아래 섹션을 따라 수행하여 AEM Screens 복제 에이전트의 설정을 업데이트합니다.

>[!IMPORTANT]
>기존의 모든 AEM Screens 복제 에이전트에서 다음 단계를 완료합니다.

1. AEM 인스턴스로 이동합니다.
1. 도구 > **배포** > **복제**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. **작성자의 에이전트**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 작성자의 모든 AEM Screens 복제 에이전트를 검색하고 아래 그림과 같이 링크를 클릭합니다.

   >[!NOTE]
   >모든 AEM Screens 복제 에이전트를 검색합니다. Screens 복제 에이전트 이름에는 제목에 **S** 문자가 포함되어 있습니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. **편집**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. **설정** 탭에서 **사용**&#x200B;을 확인하세요.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. **에이전트 설정** 대화 상자에서 **전송** 탭으로 이동하여 **사용자**&#x200B;를 **`screens-receiver-user`**(으)로 업데이트하고 [사용자 사용 및 암호 업데이트](#enable-users)의 (8) 단계에서 이전에 설정한 동일한 암호를 입력합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. **확인**&#x200B;을 클릭합니다.

1. 이전 단계를 완료한 후 **연결 테스트**&#x200B;를 클릭하여 연결을 확인합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   연결 확인에 성공하면 Screens 복제 에이전트 구성을 완료했습니다.
