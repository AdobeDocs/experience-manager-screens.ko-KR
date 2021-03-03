---
title: 플레이어 자동 등록
seo-title: 플레이어 자동 등록
description: AMS/On-Prem Screens에서 플레이어의 자동 등록에 대해 알려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 플레이어 자동 등록 {#auto-registration}

수천 명의 플레이어를 수동으로 등록하면 번거로울 수 있고 시간과 비용을 추가할 수 있습니다. 이 프로세스를 간소화하기 위해 벌크 등록 기능을 사용하면 AEM에서 구성 파일 또는 MDM(Mobile Device Management) 솔루션을 통해 플레이어로 프로비저닝할 수 있는 사전 공유 키를 지정할 수 있습니다.

## 플레이어 {#bulk-registering-implementation} 자동 등록 구현

플레이어에 대한 자동 등록을 구현하려면 아래 절차를 따르십시오.

1. AEM 인스턴스에 로그인하고 AEM 스크린 프로젝트를 선택하고 작업 표시줄에서 **속성**&#x200B;을 클릭합니다.
1. **고급** 탭을 선택하여 **장치 등록** 섹션을 봅니다.

1. **일괄 등록 코드** 필드에 자동 등록 코드를 지정하고 **기본 표시 할당**&#x200B;에 선택적인 기본 표시를 지정하여 자동으로 등록된 플레이어에 할당합니다.
   >[!NOTE]
   >원하는 코드를 입력하고 필요한 경우 기본 표시를 선택합니다.

   ![이미지](/help/user-guide/assets/auto-registration/auto-register1.png)
1. MDM 또는 구성 JSON 파일을 사용하여 해당 서버 URL 및 등록 코드를 플레이어에 제공합니다.

   >[!NOTE]
   >자세한 내용은 운영 체제(OS)의 특정 플레이어에 대한 구현 페이지를 참조하십시오. 관리자 UI를 사용하여 등록 코드를 입력할 수도 있습니다.

1. `registrationKey` 속성이 AEM에 구성된 속성과 일치하면 플레이어는 자동으로 등록되고 기본 표시가 구성된 경우 해당 컨텐츠가 다운로드 및 재생됩니다.

   ![이미지](/help/user-guide/assets/auto-registration/auto-register2.png)

## 보안 우수 사례 {#security-best-practices}

아래 섹션을 따라 보안에 대한 우수 사례 중 일부를 고려하십시오.

* 등록 코드가 손상되지 않도록 하려면 벌크 등록을 시작하기 직전에 AEM에서 코드를 구성하여 완료하면 해당 필드를 지운 후 AEM에 저장하십시오.

* 가능한 경우 알려진 IP 범위에서만 액세스할 수 있도록 `/bin/screens/registration` 경로를 구성할 수 있습니다.

* MDM을 사용하여 해당 구성으로 플레이어를 프로비저닝하는 것을 고려해 보십시오.

* AEM와의 플레이어 통신에는 항상 `HTTP`이 아닌 `HTTPS`을 사용하십시오.

   >[!NOTE]
   >기본 표시 할당은 현재 벌크 등록에만 작동하며 등록 코드가 없는 수동 등록에는 작동하지 않습니다.