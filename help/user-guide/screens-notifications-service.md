---
title: AEM Screens 알림 서비스
seo-title: AEM Screens 알림 서비스
description: 장치 활동을 모니터하는 방법에 대한 자세한 내용을 살펴보려면 이 페이지를 따르십시오.
seo-description: 장치 활동을 모니터하는 방법에 대한 자세한 내용을 살펴보려면 이 페이지를 따르십시오.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens 알림 서비스{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens 알림***&#x200B;서비스에서 장치 활동을 모니터링할 수 있는 기능에 대해 설명합니다.

이 섹션에서는 다음과 같은 주제를 다룹니다.

* **개요**
* **이메일 설정 구성**
* **이메일 알림**
* **사용 사례 예**

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.3.2 기능 팩 3 또는 AEM 6.4.1 스크린 기능 팩 1을 설치한 경우에만 사용할 수 있습니다.
>
>이 Feature Pack에 액세스하려면 Adobe 지원 센터에 연락하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.

## 개요 {#overview}

***AEM Screens Notifications*** Service를 통해 관리자는 AEM Screens 플레이어가 구성 가능한 기간 동안 ping을 수행하지 않는 경우 이메일을 수신할 수 있습니다.

이 서비스는 OSGi 웹 콘솔에서 구성할 수 있습니다.

## 이메일 설정 구성 {#configuring-email-settings}

아래 절차에 따라 이메일 알림 설정을 구성합니다.

1. Adobe **Experience Manager 웹 콘솔 구성을 엽니다**.
1. Open **Screens Device Email Monitoring Service**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 다음 필드를 정의하여 이메일에 대한 설정을 구성합니다.

   **장치** 경로 모니터링할 스크린 프로젝트의 경로를 입력합니다. 경로는 일반적으로 `/home/users/screens/<Name of your project>`사용됩니다.

   예를 들어 프로젝트가 We. **Retail인**&#x200B;경우 프로젝트 경로를 ***/home/users/screens/we-retail***&#x200B;로 사용합니다.

   >[!NOTE]
   >
   >장치 사용자가 있는 프로젝트 경로를 지정합니다.

   **예약 빈도** 이 모니터에서 이메일을 보낼 시간(예: 오후 5:00 또는 17:00)이나 빈도(예: 1)를 지정합니다.

   **Ping 시간 초과** 이것은 장치에 연결할 수 없는 것으로 간주되는 간격(분)을 지정합니다.

   **SMTP 서버** 이메일 전송에 사용되는 SMTP 서버를 지정합니다.

   **SMTP 포트** SMTP 포트를 입력합니다.

   **TLS** TLS(전송 계층 보안)를 사용하여 SMTP 서버와 보안 통신을 사용할 수 있습니다.

   회사 메일 서버에 대한 보안 연결을 위해 TLS를 사용하는 것이 좋습니다. 메일 관리자에게 적절한 값을 확인하십시오.

   **사용자** 이름 이메일을 보낼 사용자 이름을 지정합니다.

   **암호** 이메일 전송을 위한 암호를 지정합니다.

   **받는** 사람 받는 사람의 이메일 주소를 지정합니다.

   >[!NOTE]
   >
   >하나의 이메일 주소만 입력할 수 있습니다. 일괄 이메일을 보내려면 관련 사용자와 그룹 또는 배포 목록을 만듭니다.

1. 저장을 **클릭하여** AEM Screens 장치의 이메일을 통해 모니터 활동을 구성합니다.

## Email Notification {#email-notification}

이메일 알림에 대한 구성을 설정하면 활동이 없는 것으로 보고된 실제 장치에 대한 링크가 포함된 이메일 알림을 받게 됩니다.

해당 링크에 액세스하면 장치 대시보드로 바로 이동합니다.

지정된 핑 시간 초과에 대해 ping을 수행하지 않고 이메일을 생성할 때 여전히 ping을 실행하는 장치가 하나 이상 있는 경우에만 이메일이 전송됩니다.

### 사용 사례 예 {#example-use-cases}

다음 예에서는 스크린 장치 이메일 모니터링 서비스에서 속성을 구성하기 위해 참조에 대한 몇 가지 시나리오를 설명합니다.

**시나리오 1**:

예약 빈도를 오전 1:00으로 설정하고 핑 시간 초과를 60으로 설정한 경우 화면 장치가 오후 12:00까지 ping하지 않는 경우 장치 비활성화를 확인하는 이메일 알림을 받게 됩니다.

**시나리오 2**:

예약 빈도를 1로 설정하고 핑 시간 초과를 60으로 설정하면, 스크린 장치가 특정 시간에 한 번씩 ping하지 않는 경우, 장치 비활동을 확인하는 이메일 알림을 받게 됩니다.