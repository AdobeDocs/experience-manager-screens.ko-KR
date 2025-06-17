---
title: 원격 제어 구현
description: AEM Screens의 Screens 원격 제어 기능에 대해 알아봅니다.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Screens 원격 제어 사용 {#implementing-remote-control}

원격 제어 기능을 사용하면 관리 UI, 채널 전환기 또는 캐시 지우기, 다시 로드와 같은 기능에 더 쉽게 액세스할 수 있습니다. 또한 플레이어에서 로컬 펌웨어 버전 및 시스템 정보를 볼 수 있는 방법을 제공합니다. 이 기능은 마우스 연결이 어려울 수 있으므로 특히 유용합니다. 또는 플레이어가 AEM과 연결이 끊긴 경우 손이 닿지 않는 프로덕션 디바이스에서 작동하며 그 이상도 마찬가지입니다. 해상도 차이로 인해 마우스로 관리 UI를 찾아 열기 어려울 수 있으므로 Samsung RMS를 사용할 때도 유용합니다.

## 일반적인 원격 제어 키 조합 {#using-common-remote-control}

모든 플레이어에서 Screens 리모컨에서 다음 키 조합을 사용할 수 있습니다.

1. 관리자 UI 전환 - CTRL + 1
1. 채널 전환기 전환 - CTRL + 2
1. 캐시 지우기 - CTRL + ALT + 3
1. 플레이어 다시 로드 - CTRL + 4

## 특정 원격 제어 키 조합 초기화 {#using-tizen-remote-control}

Tizen 플레이어에 따라 Samsung RMS에서 사용할 수 있는 하드웨어 원격 또는 소프트웨어 원격 중 하나를 사용하여 다음 기능에 액세스할 수 있습니다.

1. A - 관리자 UI 전환
1. B - 채널 전환기 전환
1. C - 캐시 지우기
1. D - 플레이어 다시 로드

## 추가 사용 정보 {#using-additional-remote-control}

1. 관리 UI가 열려 있는 상태에서 위쪽 및 아래쪽 화살표를 사용하여 탭을 탐색하여 탭 간 정보를 볼 수 있습니다.
1. 채널 전환기를 연 상태에서 위쪽 및 아래쪽 화살표 키를 사용하여 채널을 탐색할 수 있습니다. 채널을 전환하려면 `Enter` 키(또는 리모컨의 화살표 중앙에 있는 단추)를 누를 수도 있습니다.

다음 다이어그램은 Samsung 리모컨의 키 사용을 보여 줍니다.
![이미지](assets/tizen/remote.png)

>[!NOTE]
>enableAdminUI 및/또는 enableOSD의 장치 구성 값을 false로 설정하면 리모콘에서 관리 UI 및 채널 전환기를 전환하지 않습니다. 화살표 키를 사용하여 관리자 UI 또는 채널을 탐색할 수 없습니다. 그러나 여전히 캐시를 지우고 플레이어를 다시 로드할 수 있습니다. 다음 코드를 사용하여 키보드 조합이 대화형 콘텐츠와 충돌하는 경우 원격 제어 기능을 비활성화할 수 있습니다.

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
