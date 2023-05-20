---
title: AEM Screens 알림 서비스
seo-title: AEM Screens Notifications Service
description: 장치 활동을 모니터링하는 방법에 대한 자세한 내용은 이 페이지를 따르십시오.
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---

# AEM Screens 알림 서비스{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens 알림 서비스***&#x200B;에서는 장치 활동을 모니터링할 수 있는 기능에 대해 설명합니다.

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **이메일 설정 구성**
* **이메일 알림**
* **예제 사용 사례**

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.3.2 기능 팩 3 또는 AEM 6.4.1 Screens 기능 팩 1을 설치한 경우에만 사용할 수 있습니다.
>
>이 기능 팩에 액세스하려면 Adobe 지원에 문의하고 액세스를 요청해야 합니다. 권한이 있으면 패키지 공유에서 다운로드할 수 있습니다.

## 개요 {#overview}

***AEM Screens 알림 서비스***&#x200B;을 사용하면 AEM screens 플레이어가 구성 가능한 기간 동안 ping을 수행하지 않는 경우 관리자가 이메일을 받을 수 있습니다.

이 서비스는 OSGi 웹 콘솔에서 구성할 수 있습니다.

## 이메일 설정 구성 {#configuring-email-settings}

이메일 알림 설정을 구성하려면 아래 단계를 따르십시오.

1. 열기 **Adobe Experience Manager 웹 콘솔 구성**.
1. 열기 **Screens 장치 이메일 모니터링 서비스**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 전자 메일에 대한 설정을 구성하려면 다음 필드를 정의하십시오.

   **장치 경로** 모니터링할 화면 프로젝트의 경로를 입력합니다. 경로는 일반적으로 다음과 같습니다 `/home/users/screens/<Name of your project>`.

   예를 들어 프로젝트가 **We.Retail**, 프로젝트 경로는 다음과 같이 사용됩니다. ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >장치 사용자가 있는 프로젝트 경로를 지정합니다.

   **일정 빈도** 이 모니터가 이메일을 보내야 하는 시간(예: 오후 5시 또는 17시) 또는 빈도(예: 시간(1))를 지정합니다.

   **Ping 시간 초과** 이 옵션은 디바이스에 연결할 수 없는 것으로 간주되는 간격(분)을 지정합니다.

   **SMTP 서버** 전자 메일 전송에 사용되는 SMTP 서버를 지정합니다.

   **SMTP 포트** SMTP 포트를 입력합니다.

   **TLS 사용** TLS(전송 계층 보안)를 사용하면 SMTP 서버와의 보안 통신을 사용할 수 있습니다.

   회사 메일 서버와의 보안 연결에 TLS를 사용하는 것이 좋습니다. 적절한 값이 있는지 메일 관리자에게 문의하십시오.

   **사용자 이름** 이메일을 보낼 사용자 이름을 지정합니다.

   **암호** 전자 메일 전송을 위한 암호를 지정합니다.

   **수신자** 수신자의 이메일 주소를 지정합니다.

   >[!NOTE]
   >
   >이메일 주소는 하나만 입력할 수 있습니다. 벌크 이메일을 보내려면 관련 사용자와 함께 그룹 또는 메일 그룹을 만듭니다.

1. 클릭 **저장** 이메일을 통해 AEM Screens 디바이스에 대한 모니터 활동을 구성합니다.

## 이메일 알림 {#email-notification}

이메일 알림에 대한 구성을 설정하면 비활성 것으로 보고되는 실제 디바이스에 대한 링크가 포함된 이메일 알림을 받게 됩니다.

해당 링크에 액세스하면 디바이스 대시보드로 바로 이동합니다.

지정된 ping 시간 제한 동안 ping하지 않았으며 이메일을 생성할 때 ping하지 않는 장치가 하나 이상 있는 경우에만 이메일이 전송됩니다.

### 예시 사용 사례 {#example-use-cases}

다음 예제에서는 Screens 장치 전자 메일 모니터링 서비스에서 속성을 구성하는 몇 가지 참조 시나리오를 설명합니다.

**시나리오 1**:

예약 빈도를 오전 1시로 설정하고 핑 시간 제한을 60으로 설정한 경우 Screens 장치가 오후 12시 이후부터 오후 1시까지 ping을 수행하지 않으면 장치 비활성화를 확인하는 이메일 알림을 받게 됩니다.

**시나리오 2**:

예약 빈도를 1로 설정하고 핑 시간 초과를 60으로 설정한 경우 Screens 장치가 하루 중 특정 시간에 한 번 핑 하지 않으면 장치 비활성화를 확인하는 이메일 알림을 받게 됩니다.
