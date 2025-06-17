---
title: ACL 설정
description: ACL(액세스 제어 목록)을 사용하여 프로젝트를 분리하여 각 개인 또는 팀이 고유한 프로젝트를 처리하도록 하는 방법에 대해 알아봅니다.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# ACL(액세스 제어 목록) 설정 {#setting-up-acls}

다음 섹션에서는 각 개인 또는 팀이 자체 프로젝트를 처리하도록 ACL(액세스 제어 목록)을 사용하여 프로젝트를 분리하는 방법을 설명합니다.

AEM 관리자는 프로젝트의 팀원이 다른 프로젝트를 방해하지 않도록 해야 합니다. 각 사용자에게는 프로젝트 요구 사항에 따라 특정 역할이 할당됩니다.

## 권한 설정 {#setting-up-permissions}

다음 단계에서는 프로젝트에 대한 ACL 설정 절차를 요약합니다.

1. AEM에 로그인하고 **도구** > **보안**(으)로 이동합니다.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. **그룹**&#x200B;을 클릭하고 ID(예: Acme)를 입력하십시오.

   또는 이 링크 `http://localhost:4502/libs/granite/security/content/groupadmin.html`을(를) 사용합니다.

   그런 다음 **저장**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 목록에서 **기여자**&#x200B;를 클릭하고 두 번 클릭합니다.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. **Acme**(만든 프로젝트)을(를) **그룹에 구성원 추가**&#x200B;에 추가합니다. **저장**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >프로젝트 팀원이 플레이어를 등록하도록 하려면(모든 플레이어에 대한 사용자 생성이 포함됨) 사용자-관리자 그룹을 찾아 사용자-관리자에 ACME 그룹을 추가합니다

1. **Acme** 프로젝트에서 작업 중인 모든 사용자를 **Acme** 그룹에 추가합니다.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 이 `(http://localhost:4502/useradmin)`을(를) 사용하여 **Acme** 그룹에 대한 권한을 설정합니다.

   **Acme** 그룹을 클릭하고 **권한**&#x200B;을 클릭합니다.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 권한 {#permissions}

다음 표에는 프로젝트 수준의 권한이 있는 경로가 요약되어 있습니다.

| **경로** | **권한** | **설명** |
|---|---|---|
| `/apps/<project>` | 읽기 | 해당되는 경우 프로젝트 파일에 대한 액세스 권한을 제공합니다. |
| `/content/dam/<project>` | 모두 | DAM에 이미지 또는 비디오와 같은 프로젝트 자산을 저장할 수 있는 액세스 권한을 제공합니다. |
| `/content/screens/<project>` | 모두 | /content/screens 아래의 다른 모든 프로젝트에 대한 액세스를 제거합니다. |
| `/content/screens/svc` | 읽기 | 등록 서비스에 대한 액세스 권한을 제공합니다. |
| `/libs/screens` | 읽기 | DCC에 대한 액세스 권한을 제공합니다. |
| `/var/contentsync/content/screens/` | 모두 | 프로젝트의 오프라인 콘텐츠를 업데이트하는 데 도움이 됩니다. |

>[!NOTE]
>
>경우에 따라 작성자 기능(예: 에셋 관리 및 채널 만들기)과 관리자 기능(예: 플레이어 등록)을 분리할 수 있습니다. 이러한 시나리오에서는 두 개의 그룹을 만들고 작성자의 그룹을 기여자에게 추가하고 관리자 그룹을 기여자와 사용자 관리자 모두에 추가합니다.

### 그룹 만들기 {#creating-groups}

프로젝트를 만들 때는 기본 사용 권한 집합이 할당된 기본 사용자 그룹도 만들어야 합니다. AEM Screens에 정의된 일반적인 역할로 권한을 확장합니다.

예를 들어 다음과 같은 프로젝트별 그룹을 만들 수 있습니다.

* Screens 프로젝트 관리자
* Screens 프로젝트 운영자(플레이어 등록 및 위치 및 장치 관리)
* Screens 프로젝트 사용자(채널, 일정 및 채널 할당 작업)

다음 표에는 AEM Screens 프로젝트에 대한 설명 및 권한이 있는 그룹이 요약되어 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>그룹 이름</strong></td>
   <td><strong>설명</strong></td>
   <td><strong>권한</strong></td>
  </tr>
  <tr>
   <td>Screens 관리자<br /> <em><code>screens-admins</code></em></td>
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
   <td>Screens 사용자<br /> <em><code>screens-users</code></em></td>
   <td>AEM Screens에서 채널 및 일정을 만들고 업데이트하며 위치를 지정합니다.</td>
   <td>
    <ul>
     <li>기여자 구성원</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens 연산자<br /> <em><code>screens-operators</code></em></td>
   <td>AEM Screens에서 위치 구조 만들기 및 업데이트 및 플레이어 등록</td>
   <td>
    <ul>
     <li>기여자 구성원</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens 플레이어스<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>모든 플레이어 및 모든 플레이어/장치는 자동으로 기여자의 구성원입니다.</td>
   <td><p> 기여자 구성원</p> </td>
  </tr>
 </tbody>
</table>
