---
title: MDM 또는 EMM을 사용하여 Android Player 벌크 프로비저닝
seo-title: EMM 또는 MDM을 사용하여 Android Player의 벌크 프로비저닝
description: EMM 또는 MDM을 사용하여 Android Player의 벌크 프로비저닝에 대해 알려면 이 페이지를 따르십시오
translation-type: tm+mt
source-git-commit: f94eac66b6372e9f3e4cfc28693c4ba61d1b9ab1
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Enterprise Mobility Management {#bulk-provisioning}을(를) 사용하여 Android Player의 벌크 프로비저닝

Android 플레이어를 일괄 배포할 때 AEM에 모든 단일 플레이어를 수동으로 등록하는 것은 번거롭습니다. VMWare Airwatch, MobileIron 또는 Samsung Knox와 같은 EMM(Enterprise Mobility Management) 솔루션을 사용하여 원격으로 배포를 준비하고 관리하는 것이 좋습니다. AEM Screens Android 플레이어는 업계 표준 EMM Appconfig를 지원하여 원격 프로비저닝을 허용합니다. 플레이어를 대량으로 제공하려면 아래 단계를 따르십시오.

## Enterprise Mobility Management {#implementation}을(를) 사용하여 Android Player의 벌크 프로비저닝 구현

Android Player에서 벌크 프로비저닝을 허용하려면 아래 절차를 따르십시오.

1. Android 장치가 Google Play 서비스를 지원하는지 확인합니다.
1. Appconfig를 지원하는 즐겨 사용하는 EMM 솔루션으로 Android 플레이어 디바이스를 등록합니다.
1. EMM 콘솔에 로그인하고 Google Play에서 AEM Screens Player 애플리케이션을 가져옵니다.
1. 관리 구성(또는 관련 옵션)을 선택합니다.
1. 서버 및 벌크 등록 코드와 같이 구성할 수 있는 플레이어 옵션 목록이 표시됩니다.
1. 이러한 매개 변수를 구성하고 정책을 저장하고 장치에 배포합니다.

   >[!NOTE]
   >장치는 구성과 함께 응용 프로그램을 받고 선택한 구성으로 올바른 AEM 서버를 가리켜야 합니다. 벌크 등록 코드를 구성하여 AEM에 구성된 것과 동일한 상태로 유지한 경우 플레이어를 자동으로 등록할 수 있어야 합니다. 기본 디스플레이를 구성한 경우 일부 기본 컨텐츠를 다운로드하고 표시할 수도 있습니다(나중에 필요에 따라 변경할 수 있음).

또한 AppConfig 지원 시 EMM 공급업체에 문의하십시오. 가장 인기 있는 항목(예: [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [모바일 아이언](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 및 &lt;a11 0/>삼성 녹스](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)는 이 업계 표준을 지원합니다.[


