---
title: ACL 설정
seo-title: Setting up ACLs
description: 이 페이지를 따라 각 개인 또는 팀이 자체 프로젝트를 처리하도록 ACL을 사용하여 프로젝트를 분리하는 방법을 알아봅니다.
seo-description: Follow this page to learn how to segregate projects using ACLs so that each individual or team handles their own project.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 6%

---

# ACL 설정 {#setting-up-acls}

다음 섹션에서는 각 개인 또는 팀이 자체 프로젝트를 처리하도록 ACL을 사용하여 프로젝트를 분리하는 방법을 설명합니다.

AEM 관리자는 프로젝트의 팀원이 다른 프로젝트를 방해하지 않고 프로젝트 요구 사항에 따라 각 사용자에게 특정 역할이 할당되도록 해야 합니다.

## 권한 설정 {#setting-up-permissions}

다음 단계에서는 프로젝트에 대한 ACL 설정 절차를 요약합니다.

1. AEM에 로그인하고 다음으로 이동 **도구** > **보안**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 클릭 **그룹** ID(예: Acme)를 입력합니다.

   또는 이 링크를 사용하여 `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   그런 다음 을 클릭합니다. **저장**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 선택 **참가자** 목록에서 을(를) 클릭하고 을(를) 더블 클릭합니다.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 추가 **Acme** (사용자가 만든 프로젝트) 대상 **그룹에 구성원 추가**. **저장**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >프로젝트 팀원이 플레이어를 등록하도록 하려면(모든 플레이어에 대한 사용자 생성이 포함됨) 사용자-관리자 그룹을 찾아 사용자-관리자에 ACME 그룹을 추가합니다

1. 작업할 모든 사용자 추가 **Acme** 프로젝트 대상: **Acme** 그룹입니다.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 그룹에 대한 권한 설정 **Acme** 사용 `(http://localhost:4502/useradmin)`.

   그룹 선택 **Acme** 을(를) 클릭하고 **권한**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 권한 {#permissions}

다음 표에는 프로젝트 수준의 권한이 있는 경로가 요약되어 있습니다.

| **경로** | **권한** | **설명** |
|---|---|---|
| `/apps/<project>` | 읽기 | 프로젝트 파일에 대한 액세스 권한 제공(해당되는 경우) |
| `/content/dam/<project>` | 모두 | DAM에 이미지 또는 비디오와 같은 프로젝트 자산을 저장할 수 있는 액세스 권한을 제공합니다. |
| `/content/screens/<project>` | 모두 | /content/screens 아래의 다른 모든 프로젝트에 대한 액세스 제거 |
| `/content/screens/svc` | 읽기 | 등록 서비스에 대한 액세스 권한 제공 |
| `/libs/screens` | 읽기 | DCC 액세스 제공 |
| `/var/contentsync/content/screens/` | 모두 | 프로젝트의 오프라인 콘텐츠를 업데이트할 수 있습니다. |

>[!NOTE]
>
>경우에 따라 작성자 기능(예: 에셋 관리 및 채널 만들기)과 관리자 기능(예: 플레이어 등록)을 분리할 수 있습니다. 이러한 시나리오에서는 두 개의 그룹을 만들고 작성자 그룹을 기여자에게, 관리자 그룹을 기여자와 사용자 관리자 모두에 추가합니다.

### 그룹 만들기 {#creating-groups}

새 프로젝트를 만들 때는 기본 사용 권한 집합이 할당된 기본 사용자 그룹도 만들어야 합니다. AEM Screens에 대해 가지고 있는 일반적인 역할로 권한을 확장해야 합니다.

예를 들어 다음과 같은 프로젝트별 그룹을 만들 수 있습니다.

* 화면 프로젝트 관리자
* Screens 프로젝트 운영자(플레이어 등록 및 위치 및 장치 관리)
* 화면 프로젝트 사용자(채널, 일정 및 채널 할당 작업)

다음 표에는 AEM Screens 프로젝트에 대한 설명 및 권한이 있는 그룹이 요약되어 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>그룹 이름</strong></td>
   <td><strong>설명</strong></td>
   <td><strong>권한</strong></td>
  </tr>
  <tr>
   <td>화면 관리자<br /> <em>screens-admin</em></td>
   <td>AEM Screens 기능에 대한 관리자 수준 액세스</td>
   <td>
    <ul>
     <li>기여자 구성원</li>
     <li>사용자-관리자 구성원</li>
     <li>모든 /content/screens</li>
     <li>ALL /content/dam</li>
     <li>모든 /content/experience-fragments</li>
     <li>모든 /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>화면 사용자<br /> <em>screens-users</em></td>
   <td>채널 및 일정을 만들고 업데이트하며 AEM Screens의 위치에 할당</td>
   <td>
    <ul>
     <li>기여자 구성원</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens 연산자<br /> <em>screens-operators</em></td>
   <td>AEM Screens에서 위치 구조 만들기 및 업데이트 및 플레이어 등록</td>
   <td>
    <ul>
     <li>기여자 구성원</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>스크린 플레이어<br /> <em>screens-&lt;project&gt;-디바이스</em></td>
   <td>모든 플레이어 및 모든 플레이어/장치를 그룹화하면 자동으로 기여자의 구성원이 됩니다.</td>
   <td><p> 기여자 구성원</p> </td>
  </tr>
 </tbody>
</table>
