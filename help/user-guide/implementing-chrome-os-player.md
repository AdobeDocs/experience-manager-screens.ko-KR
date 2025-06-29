---
title: Chrome OS 플레이어 구현
description: Chrome Management Console을 사용한 Chrome OS 플레이어 구현에 대해 알아봅니다.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# Chrome OS 플레이어 구현 {#implementing-chrome-os-player}

이 섹션에서는 Chrome Management Console을 사용하여 Chrome OS 플레이어를 구현하는 방법에 대해 설명합니다.

## Chrome Management Console 사용 {#using-chrome-management-console}

Chrome 관리 콘솔을 설정하려면 아래 단계를 따르십시오.

1. Chrome 관리 콘솔에 등록합니다. Chrome Management Console에 대한 라이선스를 받아야 합니다. 자세한 내용은 [Google 지원](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995)에 문의하여 Chrome 장치 설정을 관리하세요.
1. Chrome OS 장치를 도메인에 등록하고 장치가 Chrome Management Console과 동기화될 때까지 15분 동안 기다립니다. Chrome 장치 등록에 대한 자세한 내용을 보려면 [여기](https://support.google.com/chrome/a/answer/1360534?hl=en)를 클릭하세요.
1. Chrome 플레이어는 Chrome 웹 스토어에서 사용할 수 있습니다.

>[!NOTE]
>
>Chrome OS 장치의 배포 및 관리에는 Chrome Management Console과 같은 장치 관리 솔루션이 권장됩니다. 이 문서에서는 Chrome Management Console에 대한 구현을 제공하지만 유사한 기능을 제공한다고 주장하는 다른 공급업체가 있습니다. 장치 관리 소프트웨어 공급업체에 문의하십시오.

## Chrome OS 플레이어 이름 지정 {#name-chrome}

사용자에게 친숙한 장치 이름을 Chrome 플레이어에 할당하여 할당된 장치 이름을 Adobe Experience Manager(AEM)에 보낼 수 있습니다. 이 기능을 사용하면 Chrome 플레이어의 이름을 지정할 수 있을 뿐만 아니라 적절한 컨텐츠를 쉽게 할당할 수 있습니다.

>[!NOTE]
>등록하기 전에만 플레이어 이름을 선택할 수 있습니다. 플레이어가 등록되면 더 이상 플레이어 이름을 변경할 수 없습니다.

Chrome 플레이어에서 이름을 구성하려면 아래 단계를 따르십시오.

1. 오디오-비디오 통합자나 IT 관리자가 자산 ID와 위치를 엔터프라이즈 등록의 일부로 설정하도록 선택적으로 허용할 수 있습니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome1.png)

1. 장치를 등록할 수 있는 옵션이 표시됩니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 자산 ID는 Chrome Management Console에서 엔터프라이즈 등록의 일부로 설정할 수 있습니다.

   ![이미지](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome 플레이어는 기업 등록에 등록해야 하며 Chrome 플레이어는 Chrome Management Console을 통해 배포되어야 합니다. 그렇지 않으면 에셋 ID가 비어 있습니다(예: Chrome as a extension). 장치 이름은 등록 시점에만 기록됩니다. 향후 변경 사항은 Adobe Experience Manager(AEM)에서 선택되지 않습니다.

### 키오스크 모드 활성화 {#enabling-kiosk-mode}

키오스크 모드를 활성화하려면 아래 단계를 따르십시오.

1. Chrome Developer Console에 로그인합니다.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. **장치 관리** > **Chrome 관리** > **장치 설정**&#x200B;으로 이동합니다.
1. **키오스크 설정**(으)로 스크롤한 다음 **키오스크 응용 프로그램 관리**&#x200B;를 클릭합니다.

   ![키오스크](assets/kiosk.png)

1. Chrome 웹 스토어에서 AEM Screens 플레이어 를 클릭합니다.

   >[!NOTE]
   >
   >최근에 게시된 앱이 이 목록에 표시되는 데 약 15분이 걸릴 수 있습니다.

1. **자동 실행 키오스크 앱** 드롭다운에서 **AEM Screens 플레이어**&#x200B;를 클릭합니다.

   네트워크에 따라 변경 사항이 적용되는 데 몇 분 정도 걸릴 수 있습니다. 재부팅하는 것이 좋습니다.

#### 원격 장치 상태 확인 {#checking-remote-device-status}

1. Chrome Developer Console에 로그인합니다.
1. **장치 관리** > **Chrome 장치**(으)로 이동하여 제어할 장치를 클릭합니다.
1. **시스템 활동 및 문제 해결**&#x200B;을 클릭합니다.
1. 장치의 **장치 다시 부팅** 및 **화면 캡처** 속성을 확인하십시오. 장치 상태 및 상태 정보도 확인할 수 있습니다.

>[!NOTE]
>
>이러한 설정은 장치가 등록된 후 몇 분 후에 활성화할 수 있습니다. 각 옵션은 시간이 지남에 따라 활성화할 수 있습니다.

### Chrome OS 플레이어의 원격 구성 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player는 Chrome OS 플레이어에 대한 원격 정책 구성도 활성화하는 키오스크 지원 애플리케이션입니다.

플레이어의 다양한 옵션을 구성하려면 아래 단계를 따르십시오.

1. Chrome 관리 콘솔에 로그인합니다.
1. **장치 관리** > **Chrome 관리** > **앱 관리**&#x200B;를 클릭합니다. AEM Screens 플레이어가 목록에 표시됩니다.
1. 응용 프로그램 **AEM Screens 플레이어**&#x200B;를 클릭합니다.
1. **키오스크 설정**&#x200B;을 클릭하고 조직(*테스트 환경을 사용하는 경우*)을 클릭합니다.
1. **구성 파일 업로드**&#x200B;를 클릭하고 구성 정책(*JSon 파일*)을 업로드하십시오.
1. **저장**&#x200B;을 클릭합니다. 정책을 동기화할 수 있도록 장치를 다시 부팅합니다.

>[!NOTE]
>
>정책 변경 사항을 동기화할 수 있도록 장치를 재부팅합니다.

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
| 서버 | Adobe Experience Manager(AEM) 서버의 URL입니다. |
| registrationKey | 미리 공유한 키를 사용하여 장치를 대량으로 등록하는 데 사용됩니다. |
| 해상도 | 장치의 해상도입니다. |
| rebootScheduling | 플레이어를 재부팅하는 일정입니다. |
| enableAdminUI | 관리자 UI를 활성화하여 사이트에서 장치를 구성합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정합니다. |
| enableOSD | 사용자가 장치에서 채널을 전환할 수 있도록 채널 전환기 UI를 활성화합니다. 완전히 구성되고 프로덕션에 있는 경우 false 로 설정하는 것이 좋습니다. |
| enableActivityUI | 다운로드 및 동기화와 같은 활동의 진행 상황을 표시할 수 있도록 활성화합니다. 문제 해결을 위해 활성화하고, 완전히 구성되어 프로덕션에 있는 경우 비활성화합니다. |
| cloudMode | Chrome 플레이어를 Screens as a Cloud Service에 연결하려면 true로 설정합니다. AMS 또는 온프레미스 AEM에 연결하려면 false로 설정합니다. |
| cloudToken | Screens as a Cloud Service에 대해 등록할 등록 토큰입니다. |

>[!NOTE]
>
>정책 구성은 엄격하게 적용되며 플레이어의 관리 UI는 수동으로 재정의되지 않습니다. 특정 정책에 대해 수동 플레이어 구성을 허용하려면 ***정책 구성***&#x200B;에서 정책을 지정하지 마십시오. 예를 들어 재부팅 일정에 대해 수동 구성을 허용하려면 정책 구성에 ***rebootSchedule*** 키를 지정하지 마십시오.

### Screens 원격 제어 사용 {#using-remote-control}

AEM Screens은 원격 제어 기능을 제공합니다. 이 기능에 대해 자세히 알아보세요. [Screens 원격 제어](implementing-remote-control.md)
