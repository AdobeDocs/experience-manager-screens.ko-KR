---
title: 원격 제어 구현
seo-title: Impementing the Remote Control
description: 화면 원격 제어 기능에 대해 알아보려면 이 페이지를 따르십시오.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: ff59c3748ea69a37ca68e81e5bf753881e8464b0
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 화면 원격 제어 사용  {#implementing-remote-control}

원격 제어 기능을 사용하면 관리자 UI, 채널 전환기 또는 Clear Cache 및 다시 로드와 같은 기능에 쉽게 액세스할 수 있습니다. 또한 플레이어에 대한 로컬 펌웨어 버전 및 시스템 정보를 보는 방법을 제공합니다. 이 기능은 마우스와 AEM의 연결이 끊겼을 경우 마우스를 연결하고 손이 닿지 않은 프로덕션 장치에서 작업하는 것이 어려울 수 있으므로 특히 유용합니다. 이 기능은 Samsung RMS를 사용할 때도 유용합니다. 해상도 차이로 마우스를 사용하여 관리자 UI를 찾아 여는 것이 매우 어려울 수 있기 때문입니다.

## 일반적인 원격 제어 키 조합 {#using-common-remote-control}

모든 플레이어에서 화면 원격 제어에서 다음 키 조합을 사용할 수 있습니다.

1. 관리자 UI 전환 - CTRL + 1
1. 채널 전환기 전환 - CTRL + 2
1. 캐시 지우기 - CTRL + ALT + 3
1. 플레이어 다시 로드 - CTRL + 4

## 특정 원격 제어 키 조합 조정 {#using-tizen-remote-control}

타이젠 플레이어에만 Samsung RMS에서 사용할 수 있는 하드웨어 원격 또는 소프트웨어 원격 중 하나를 사용하여 다음 기능에 액세스할 수 있습니다.

1. A - 관리자 UI 전환
1. B - 채널 전환기 전환
1. C - 캐시 지우기
1. D - 플레이어 다시 로드

## 추가 사용 노트 {#using-additional-remote-control}

1. Admin UI를 열면 위쪽 및 아래쪽 화살표를 사용하여 탭을 탐색하여 탭 간에 정보를 볼 수 있습니다.
1. 채널 전환기를 연 상태에서 위쪽 및 아래쪽 화살표 키를 사용하여 채널을 탐색하고 Enter 키(또는 원격 화살표의 중심에 있는 버튼)를 눌러 채널을 전환할 수 있습니다.

다음 다이어그램은 Samsung Remote의 키 사용을 보여 줍니다.
![이미지](assets/tizen/remote.png)

>[!NOTE]
>enableAdminUI의 장치 구성 값을 false로 설정하거나 enableOSD를 false로 설정하면 원격에서 관리자 UI 및 채널 전환기를 전환하지 않습니다. 또한 화살표 키를 사용하여 관리 UI 또는 채널을 탐색할 수도 없습니다. 그러나 여전히 캐시를 지우고 플레이어를 다시 로드할 수 있습니다. 다음 코드를 사용하여 키보드 조합이 대화형 콘텐츠와 충돌하는 경우 원격 제어 기능을 비활성화할 수 있습니다.

```javascript require(/['util/ScreensDisplay'/], function() /{window.ScreensDisplay.ignoreRemoteControl = true;/}); ```
