---
title: Screens 복제 에이전트 구성
description: Screens 복제 에이전트를 구성하는 방법에 대해 알아봅니다.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Screens 복제 에이전트 구성 {#configuring-screens-replication-agent}

이 다음 페이지에서는 Screens 복제 에이전트를 구성하는 방법을 설명합니다.

## 목표 {#objective}

Screens 복제 에이전트는 다음과 같은 명령 데이터를 가져옵니다. *사용자*, *암호*, *rebootScheduling*, *maxNumberOfLogfilesToKeep*, 게시에서 작성자에 이르기까지 이러한 다양한 값. 작성자가 장치 ping을 표시할 수 있도록 이를 구성하는 것이 필수적이다.

>[!NOTE]
>Screens 복제 에이전트에 대한 자세한 내용은 [화면 복제 에이전트 및 명령](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Screens 복제 에이전트에 대한 구성을 완료하려면 다음 두 섹션을 모두 완료하십시오.

1. [사용자 활성화 및 암호 업데이트](#enable-users)
1. [Screens 복제 에이전트에 대한 설정 업데이트 중](#replicate-agent)

## 사용자 활성화 및 암호 업데이트 {#enable-users}

사용자를 활성화하고 의 암호를 업데이트하려면 아래 단계를 따르십시오. `screens-receiver-user`:

>[!NOTE]
>보안상의 이유로 의 관리자 암호를 사용하지 않는 것이 좋습니다. `screens-receiver-user`.

1. AEM 작성자 인스턴스로 이동합니다.

1. 도구 > 를 클릭합니다 **보안** > **사용자**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 검색 대상 **`screens-receiver-user`**.

1. 다음 항목 선택 **`screens-receiver-user`** 및 클릭 **사용** 작업 표시줄에서

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 클릭 **확인** 확인할 수 있습니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication3.png)

   사용자를 활성화하면 **`screens-receiver-user`** 다음으로: **활성화됨** 다음 아래에 **상태** 필드.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 다음 항목 선택 **`screens-receiver-user`** 및 클릭 **속성** 작업 표시줄에서

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 클릭 **암호 변경** 아래에 **계정 설정** 다음에서 **세부 사항** 아래 그림과 같이 탭으로 이동합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 에 새 암호 입력 **암호 변경** 대화 상자 및 클릭 **저장**.

   >[!NOTE]
   >에 기존 관리자 암호를 입력하십시오. **내 암호** 필드.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. **저장 및 닫기**&#x200B;를 클릭합니다.

1. 다음 항목 선택 **`screens-receiver-user`** 및 클릭 **활성화** 작업 표시줄에서

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 클릭 **확인** 확인할 수 있습니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 다음 항목 선택 **`screens-receiver-user`** 및 클릭 **사용 안 함** 작업 표시줄에서

   >[!IMPORTANT]
   > 비활성화 중 **`screens-receiver-user`** 은(는) 작성 인스턴스에서 이 사용자만 비활성화하고 게시 인스턴스의 모든 사용자는 활성 상태로 유지됩니다. 클릭 안 함 **비활성화** 비활성화로 작업 표시줄에서 사용자를 게시 인스턴스에서도 제거합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 클릭 **확인** 확인할 수 있습니다.

## Screens 복제 에이전트에 대한 설정 업데이트 중 {#replicate-agent}

아래 섹션을 따라 수행하여 AEM Screens 복제 에이전트의 설정을 업데이트합니다.

>[!IMPORTANT]
>모든 기존 AEM Screens 복제 에이전트에서 다음 단계를 완료합니다.

1. AEM 인스턴스로 이동합니다.
1. 도구 > 를 클릭합니다 **배포** > **복제**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. **작성자의 에이전트**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 작성자의 모든 AEM Screens 복제 에이전트를 검색하고 아래 그림과 같이 링크를 클릭합니다.

   >[!NOTE]
   >모든 AEM Screens 복제 에이전트를 검색합니다. Screens 복제 에이전트 이름에 문자가 포함되어 있습니다. **S** 제목에서.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 클릭 **편집**.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 확인 **활성화됨** 다음에서 **설정** 탭.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 다음으로 이동 **전송** 의 탭 **에이전트 설정** 대화 상자 및 업데이트 **사용자** 끝 **`screens-receiver-user`** 및 의 (8)단계에서 이전에 설정한 동일한 암호를 입력합니다. [사용자 활성화 및 암호 업데이트](#enable-users).

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. **확인**&#x200B;을 클릭합니다.

1. 이전 단계를 완료한 후 **연결 테스트** 연결을 확인합니다.

   ![이미지](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   연결 확인에 성공하면 Screens 복제 에이전트 구성을 완료했습니다.
