---
title: Chrome OS Player 구현
seo-title: Chrome OS Player 구현
description: Chrome 관리 콘솔을 사용하는 Chrome OS Player 구현에 대해 알려면 이 페이지를 따르십시오.
seo-description: Chrome 관리 콘솔을 사용하는 Chrome OS Player 구현에 대해 알려면 이 페이지를 따르십시오.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Chrome OS 플레이어 구현 {#implementing-chrome-os-player}

이 섹션에서는 Chrome 관리 콘솔을 사용하여 Chrome OS 플레이어를 구현하는 방법에 대해 설명합니다.

## Chrome 관리 콘솔 사용 {#using-chrome-management-console}

아래 절차에 따라 크롬 관리 콘솔을 설정합니다.

1. Chrome 관리 콘솔에 등록합니다. Chrome Management Console용 라이선스를 받아야 합니다. 자세한 내용은 [Google 지원](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)에 문의하십시오.
1. 장치가 Chrome 관리 콘솔과 동기화되기 위해 15분 동안 도메인에 Chrome OS 장치를 등록합니다. 크롬 장치 등록에 대한 자세한 내용을 보려면 [여기](https://support.google.com/chrome/a/answer/1360534?hl=en)를 클릭하십시오.
1. Chrome Player는 Chrome 웹 스토어에서 사용할 수 있습니다.

>[!NOTE]
>
>Chrome OS 장치의 배포 및 관리에는 Chrome Management Console과 같은 장치 관리 솔루션이 권장됩니다. 그러나 이 문서에서는 Chrome Management Console에 대한 구현을 제공하지만 유사한 기능을 제공한다고 주장하는 다른 공급업체도 있습니다. 디바이스 관리 소프트웨어 공급업체에 문의하십시오.

### 키오스크 모드 {#enabling-kiosk-mode} 활성화

아래 절차에 따라 키오스크 모드를 활성화합니다.

1. Chrome 개발자 콘솔에 로그인합니다.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. **장치 관리** > **Chrome 관리** > **장치 설정**&#x200B;으로 이동합니다.
1. **키오스크 설정**&#x200B;으로 스크롤하고 **키오스크 응용 프로그램 관리**&#x200B;를 클릭합니다.

   ![키오스크](assets/kiosk.png)

1. Chrome 웹 스토어에서 AEM Screens 플레이어를 선택합니다.

   >[!NOTE]
   >
   >최근 게시된 앱이 이 목록에 표시되는 데 약 15분이 걸릴 수 있습니다.

1. **자동 실행 키오스크 앱** 드롭다운에서 **AEM Screens 플레이어**&#x200B;를 선택합니다.

   네트워크에 따라 변경 사항이 적용되려면 몇 분 정도 걸릴 수 있습니다. 재부팅하는 것이 좋습니다.

#### 원격 장치 상태 확인 중 {#checking-remote-device-status}

1. Chrome 개발자 콘솔에 로그인합니다.
1. **장치 관리** > **Chrome 장치**&#x200B;로 이동하여 제어할 장치를 선택합니다.
1. **시스템 활동 및 문제 해결**&#x200B;을 클릭합니다.
1. 장치의 **Reboot Device** 및 **화면 캡처** 속성을 확인합니다. 장치 상태 및 상태 정보를 확인할 수도 있습니다.

>[!NOTE]
>
>장치를 등록한 후 몇 분 후에 이러한 설정이 활성화될 수 있습니다. 각 옵션은 시간이 지남에 따라 활성화될 수 있습니다.

### Chrome OS 플레이어의 원격 구성 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens 플레이어는 키오스크 지원 애플리케이션으로, Chrome OS 플레이어용 원격 정책 구성도 활성화합니다.

플레이어의 다양한 옵션을 구성하려면 아래 단계를 따르십시오.

1. Chrome 관리 콘솔에 로그인합니다.
1. **장치 관리** > **Chrome 관리** > **앱 관리**&#x200B;를 클릭합니다. AEM Screens 플레이어가 목록에 표시됩니다.
1. 응용 프로그램 **AEM Screens Player**&#x200B;를 클릭합니다.
1. **키오스크 설정**&#x200B;을 클릭하고 테스트 환경&#x200B;*을 사용하는 경우 조직(*&#x200B;을 선택합니다.
1. **업로드 구성 파일**&#x200B;을 클릭하고 구성 정책(*Json 파일*)을 업로드합니다.
1. **저장**&#x200B;을 클릭합니다. 정책을 동기화하려면 장치를 다시 부팅해야 합니다.

>[!NOTE]
>
>장치를 다시 부팅하여 정책 변경 사항을 동기화합니다.

#### 예 정책 JSON 파일 {#example-policy-json-file}

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

### 정책 특성 및 목적 {#policy-attributes-and-purpose}

다음 표에는 해당 기능이 포함된 정책이 요약되어 있습니다.

| **정책 이름** | **목적** |
|---|---|
| *서버* | Adobe Experience Manager 서버에 대한 URL |
| *해상도* | Chrome OS 장치의 해상도 |
| *rebootSchedule* | Chrome 플레이어를 재부팅하는 일정 |
| *enableAdminUI* | 기술자가 사이트에서 장치를 구성할 수 있도록 관리자 UI를 활성화합니다. 구성 및 제작 시 false로 설정합니다. |
| *enableOSD* | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 설정이 완전히 구성되고 프로덕션에서 false로 설정되도록 고려하십시오. |
| *enableActivityUI* | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있습니다. 문제 해결을 활성화하거나 구성 및 제작 시 비활성화할 수 있습니다. |

>[!NOTE]
>
>정책 구성은 엄격하게 적용되며 플레이어의 관리자 UI에서 수동으로 재정의되지 않습니다. 특정 정책에 대한 수동 플레이어 구성을 허용하려면 ***정책 구성***&#x200B;에서 정책을 지정하지 마십시오. 예를 들어 재부팅 일정에 대한 수동 구성을 허용하려면 정책 구성에 ***rebootSchedule*** 키를 지정하지 마십시오.
