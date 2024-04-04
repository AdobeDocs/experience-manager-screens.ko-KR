---
title: 플레이어 자동 등록
description: AMS/On-Prem Screens에 있는 플레이어의 자동 등록에 대해 배울 수 있도록 이 페이지를 따르십시오.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 플레이어 자동 등록 {#auto-registration}

수천 명의 플레이어를 수동으로 일괄 등록하는 것은 번거로울 수 있으며 시간과 비용을 추가할 수 있습니다. 이 프로세스를 단순화하기 위해 벌크 등록 기능을 사용하면 구성 파일 또는 MDM(모바일 장치 관리) 솔루션을 통해 플레이어에 프로비저닝할 수 있는 AEM의 미리 공유된 키를 지정할 수 있습니다.

## 플레이어 자동 등록 구현 {#bulk-registering-implementation}

플레이어의 자동 등록을 구현하려면 아래 단계를 따르십시오.

1. AEM 인스턴스에 로그인하고 AEM Screens 프로젝트를 선택한 다음 를 클릭합니다. **속성** 작업 표시줄에서
1. 다음 항목 선택 **고급** 탭을 사용하여 다음을 볼 수 있습니다. **장치 등록** 섹션.

1. 에서 자동 등록 코드 지정 **일괄 등록 코드** 필드 및 선택적 기본 표시 위치 **기본 디스플레이 할당** 를 입력하여 자동 등록된 플레이어에 할당합니다.

   >[!NOTE]
   >원하는 코드를 입력하고 필요한 경우 기본 디스플레이를 선택합니다.

   ![이미지](/help/user-guide/assets/auto-registration/auto-register1.png)
1. MDM 또는 구성 JSON 파일을 사용하여 플레이어에 적절한 서버 URL 및 등록 코드를 프로비저닝합니다.

   >[!NOTE]
   >자세한 내용은 운영 체제(OS)용 특정 플레이어의 구현 페이지를 참조하십시오. 등록 코드를 입력하는 데 관리자 UI를 사용할 수도 있습니다.

1. 다음과 같은 경우 `registrationKey` 속성이 AEM에 구성된 속성과 일치하면 플레이어가 자동으로 등록되고 기본 디스플레이가 구성된 경우 해당 콘텐츠가 다운로드되고 재생됩니다.

   ![이미지](/help/user-guide/assets/auto-registration/auto-register2.png)

## 보안 모범 사례 {#security-best-practices}

아래 섹션을 따라 수행하여 보안에 대한 몇 가지 모범 사례를 고려하십시오.

* 등록 코드가 손상되지 않았는지 확인 - 일괄 등록을 시작하기 바로 전에 AEM에서 코드를 구성하고 완료되면 해당 필드를 지운 다음 AEM에 저장합니다.

* 경로를 구성할 수 있습니다 `/bin/screens/registration` 가능한 경우 알려진 IP 범위에서만 액세스할 수 있습니다.

* MDM을 사용하여 플레이어에 구성을 프로비저닝하는 것이 좋습니다.

* 항상 사용 `HTTPS` 및 아님 `HTTP` AEM과의 플레이어 커뮤니케이션용.

  >[!NOTE]
  >기본 표시 할당은 현재 일괄 등록에만 작동하며 등록 코드가 없는 수동 등록에는 작동하지 않습니다.
