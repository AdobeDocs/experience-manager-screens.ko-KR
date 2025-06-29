---
title: AEM Screens 알림 서비스
description: AEM Screens의 장치 활동을 모니터링하는 방법에 대해 자세히 알아보십시오.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# AEM Screens 알림 서비스{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens 알림 서비스***&#x200B;에서 모니터 장치 활동을 설명합니다.

이 섹션에서는 다음 주제를 다룹니다.

* **개요**
* **전자 메일 설정 구성**
* **전자 메일 알림**
* **사용 사례** 예

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## 개요 {#overview}

***AEM Screens 알림 서비스***&#x200B;를 사용하면 AEM Screens 플레이어에서 구성 가능한 시간 동안 ping을 수행하지 않는 경우 관리자가 이메일을 받을 수 있습니다.

이 서비스는 OSGi 웹 콘솔에서 구성할 수 있습니다.

## 이메일 설정 구성 {#configuring-email-settings}

이메일 알림 설정을 구성하려면 아래 단계를 따르십시오.

1. **Adobe Experience Manager 웹 콘솔 구성**&#x200B;을 엽니다.
1. **Screens 장치 전자 메일 모니터링 서비스**&#x200B;를 엽니다.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 전자 메일에 대한 설정을 구성할 수 있도록 다음 필드를 정의합니다.

   **장치 경로** - 모니터링할 Screens 프로젝트의 경로를 입력합니다. 경로는 일반적으로 `/home/users/screens/<Name of your project>`입니다.

   예를 들어 프로젝트가 **`We.Retail`**&#x200B;인 경우 프로젝트 경로를 ***/home/users/screens/we-retail***(으)로 사용하십시오.

   >[!NOTE]
   >
   >장치 사용자가 있는 프로젝트 경로를 지정합니다.

   **일정 빈도** - 이 모니터에서 이메일을 보낼 시간(예: 오후 5시 또는 17시) 또는 빈도(예: 1)를 지정합니다.

   **Ping 시간 초과** - 이 필드는 장치가 연결할 수 없는 것으로 간주되는 간격(분)을 지정합니다.

   **SMTP 서버** - 전자 메일 전송에 사용되는 SMTP 서버를 지정합니다.

   **SMTP 포트** - SMTP 포트를 입력합니다.

   **TLS 사용** - TLS(전송 계층 보안)를 사용하면 SMTP 서버와의 보안 통신을 사용할 수 있습니다.

   Adobe에서는 회사 메일 서버와의 보안 연결에 TLS를 사용할 것을 권장합니다. 메일 관리자에게 적절한 값을 문의하십시오.

   **사용자 이름** - 전자 메일을 보낼 사용자 이름을 지정합니다.

   **암호** - 전자 메일을 보낼 암호를 지정합니다.

   **받는 사람** - 받는 사람의 전자 메일 주소를 지정합니다.

   >[!NOTE]
   >
   >이메일 주소는 하나만 입력할 수 있습니다. 벌크 이메일을 보내려면 관련 사용자와 함께 그룹 또는 메일 그룹을 만듭니다.

1. AEM Screens 장치에 대한 전자 메일을 통해 모니터 활동을 구성하려면 **저장**&#x200B;을 클릭하십시오.

## 이메일 알림 {#email-notification}

이메일 알림에 대한 구성을 설정하면 비활성 것으로 보고되는 실제 디바이스에 대한 링크가 포함된 이메일 알림을 받게 됩니다.

해당 링크에 액세스하면 디바이스 대시보드로 바로 이동합니다.

이메일은 다음의 경우에만 전송됩니다.

* 지정된 ping 시간 제한 동안 ping을 수행하지 않은 장치가 하나 이상 있습니다.
* 은(는) 이메일을 생성할 때 여전히 ping을 수행하지 않습니다.

### 예시 사용 사례 {#example-use-cases}

다음 예제에서는 Screens 장치 전자 메일 모니터링 서비스에서 속성을 구성하는 몇 가지 참조 시나리오를 설명합니다.

**시나리오 1**

예약 빈도를 오전 1시로 설정하고 핑 시간 초과를 60으로 설정합니다. 그런 다음 AEM Screens 디바이스가 오후 12:00부터 오후 1:00까지 ping을 수행하지 않으면 디바이스 비활성을 확인하는 이메일 알림을 받게 됩니다.

**시나리오 2**

예약 빈도를 1로 설정하고 ping 시간 초과를 60으로 설정합니다. 그런 다음 AEM Screens 장치가 하루 중 특정 시간에 한 번에 ping을 수행하지 않으면 장치 비활성화를 확인하는 이메일 알림을 받게 됩니다.
