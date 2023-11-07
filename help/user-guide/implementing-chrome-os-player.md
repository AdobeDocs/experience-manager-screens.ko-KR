---
title: Chrome OS Player 구현
seo-title: Implementing Chrome OS Player
description: 이 페이지를 따라 Chrome 관리 콘솔을 사용한 Chrome OS Player의 구현에 대해 알아보십시오.
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 970762bb08f19ab07917dd5a21f67a007ec1143f
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 1%

---

# Chrome OS Player 구현  {#implementing-chrome-os-player}

이 섹션에서는 Chrome 관리 콘솔을 사용하여 Chrome OS 플레이어를 구현하는 방법에 대해 설명합니다.

## Chrome 관리 콘솔 사용 {#using-chrome-management-console}

Chrome 관리 콘솔을 설정하려면 아래 단계를 따르십시오.

1. Chrome 관리 콘솔에 등록합니다. Chrome Management Console에 대한 라이센스를 얻어야 합니다. 연락처 [Google 지원](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) 자세한 내용은 Chrome 장치 설정 관리 를 참조하십시오.
1. Chrome OS 장치를 도메인에 등록하고 장치가 Chrome 관리 콘솔과 동기화되려면 15분이 걸립니다. Chrome 장치 등록에 대한 자세한 내용을 보려면 [여기](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome 플레이어는 Chrome 웹 스토어에서 사용할 수 있습니다.

>[!NOTE]
>
>Chrome Management Console과 같은 장치 관리 솔루션은 Chrome OS 장치의 배포 및 관리에 권장됩니다. 그러나 이 문서에서는 Chrome Management Console에 대한 구현을 제공하지만 유사한 기능을 제공한다고 주장하는 다른 공급업체가 있습니다. 장치 관리 소프트웨어 공급업체에 문의하십시오.

## Chrome OS Player 이름 지정 {#name-chrome}

사용자에게 친숙한 장치 이름을 Chrome 플레이어에 할당하여 할당된 장치 이름을 AEM(Adobe Experience Manager)로 보낼 수 있습니다. 이 기능을 사용하면 Chrome 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 콘텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록하기 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 더 이상 플레이어 이름을 변경할 수 없습니다.

Chrome 플레이어에서 이름을 구성하려면 아래 단계를 수행하십시오.

1. AV 통합업체 또는 IT 관리자가 자산 ID 및 위치를 기업 등록의 일부로 설정하도록 선택적으로 허용할 수 있습니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome1.png)

1. 장치를 등록할 수 있을 때 옵션이 표시됩니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 자산 ID는 Chrome 관리 콘솔과 엔터프라이즈 등록의 일부로 설정할 수 있습니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome 플레이어는 기업 등록에 등록해야 하며 Chrome 플레이어는 Chrome Management Console을 통해 배포되어야 합니다. 그렇지 않으면 자산 ID가 빈 값(예: 확장 기능으로서의 chrome)을 반환합니다. 장치 이름은 등록 시점에만 기록됩니다. 향후 변경 사항은 Adobe Experience Manager(AEM)에서 선택되지 않습니다.

### 키오스크 모드 활성화 {#enabling-kiosk-mode}

키오스크 모드를 활성화하려면 아래 단계를 따르십시오.

1. Chrome 개발자 콘솔에 로그인합니다.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 다음으로 이동 **장치 관리** > **Chrome 관리** > **장치 설정**.
1. 아래로 스크롤하여 **키오스크 설정** 및 클릭 **키오스크 애플리케이션 관리**.

   ![매점](assets/kiosk.png)

1. Chrome 웹 스토어에서 AEM Screens 플레이어 를 선택합니다.

   >[!NOTE]
   >
   >최근에 게시된 앱이 이 목록에 표시되는 데 약 15분이 걸릴 수 있습니다.

1. 선택 **AEM Screens 플레이어** 다음에서 **자동 실행 키오스크 앱** 드롭다운입니다.

   네트워크에 따라 변경 사항이 적용되는 데 몇 분 정도 걸릴 수 있습니다. 재부팅하는 것이 좋습니다.

#### 원격 장치 상태 확인 {#checking-remote-device-status}

1. Chrome 개발자 콘솔에 로그인합니다.
1. 다음으로 이동 **장치 관리** > **Chrome 장치** 제어할 장치를 선택합니다.
1. 클릭 **시스템 활동 및 문제 해결**.
1. 다음 확인: **장치 재부팅** 및 **화면 캡처** 디바이스의 속성입니다. 장치 상태 및 상태 정보도 확인할 수 있습니다.

>[!NOTE]
>
>이러한 설정은 장치가 등록된 후 몇 분 후에 활성화될 수 있습니다. 각 옵션은 시간이 지남에 따라 활성화될 수 있습니다.

### Chrome OS 플레이어의 원격 구성 구성 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player는 Chrome OS 플레이어에 대한 원격 정책 구성도 활성화하는 키오스크 지원 애플리케이션입니다.

플레이어의 다양한 옵션을 구성하려면 아래 단계를 따르십시오.

1. Chrome 관리 콘솔에 로그인합니다.
1. 클릭 **장치 관리** > **Chrome 관리** > **앱 관리**. AEM Screens 플레이어가 목록에 표시됩니다.
1. 응용 프로그램 클릭 **AEM Screens 플레이어**.
1. 클릭 **키오스크 설정** 조직 선택(*테스트 환경을 사용하는 경우*).
1. 클릭 **구성 파일 업로드** 및 구성 정책 업로드(*Json 파일*).
1. **저장**&#x200B;을 클릭합니다. 정책을 동기화하려면 장치를 다시 부팅해야 합니다.

>[!NOTE]
>
>정책 변경 사항을 동기화하려면 장치를 재부팅하십시오.

#### 예제 정책 JSON 파일 {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### 정책 속성 및 목적 {#policy-attributes-and-purpose}

다음 표에는 정책과 해당 기능이 요약되어 있습니다.

| **정책 이름** | **용도** |
|---|---|
| server | Adobe Experience Manager(AEM) 서버의 URL입니다. |
| registrationKey | 미리 공유한 키를 사용하여 장치를 대량으로 등록하는 데 사용됩니다. |
| 해상도 | 장치의 해상도입니다. |
| rebootScheduling | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 관리자 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있습니다. 문제 해결을 위해 활성화하고, 완전히 구성되어 프로덕션에 있는 경우 비활성화합니다. |
| cloudMode | Tizen 플레이어가 Screens에 as a Cloud Service으로 연결되도록 하려면 true로 설정합니다. AMS 또는 온프레미스 AEM에 연결하려면 false로 설정합니다. |
| cloudToken | Screens에 대해 as a Cloud Service으로 등록할 등록 토큰입니다. |

>[!NOTE]
>
>정책 구성은 엄격하게 적용되며 플레이어의 관리 UI에서 수동으로 재정의되지 않습니다. 특정 정책에 대해 수동 플레이어 구성을 허용하려면에 정책을 지정하지 마십시오 ***정책 구성,*** 예를 들어 재부팅 일정에 대해 수동 구성을 허용하려면 키를 지정하지 마십시오 ***rebootScheduling*** 정책 구성에서 사용할 수 있습니다.

### Screens 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대한 자세한 내용은 여기를 참조하십시오. [화면 원격 제어](implementing-remote-control.md)
