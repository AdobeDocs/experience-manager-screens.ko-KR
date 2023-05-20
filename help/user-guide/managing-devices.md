---
title: 장치 관리
seo-title: Managing Devices
description: 이 페이지에서는 장치 지정에 대해 설명합니다.
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 4%

---

# 장치 관리 {#managing-devices}

이 페이지에서는 장치 지정에 대해 설명합니다.

장치 콘솔에서 장치 관리자에 액세스하여 장치를 디스플레이에 할당할 수 있습니다.

>[!CAUTION]
>
>장치를 할당하기 전에 등록해야 합니다. 자세한 내용은 [장치 등록](device-registration.md).

## 장치 지정 {#device-assignment}

장치를 디스플레이에 할당하려면 아래 단계를 따르십시오.

1. 예를 들어 프로젝트의 Devices 폴더로 이동합니다.

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 다음 항목 선택 **장치** 폴더 및 탭/클릭 **장치 관리자** 작업 표시줄에서 을 참조하십시오. 할당된 장치와 할당되지 않은 장치가 표시됩니다.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 목록에서 미할당 장치를 선택하고 **장치 지정** 작업 표시줄에서 을 참조하십시오.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 목록에서 장치를 할당할 디스플레이를 선택하고 **할당**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 탭/클릭 **완료** 할당 프로세스를 완료합니다.


   디스플레이 대시보드는에 지정된 디바이스를 표시합니다. **장치** 패널.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   (**...**)을 클릭하여 제품에서 사용할 수 있습니다 **장치** 패널 을 클릭하여 장치 구성을 추가하거나 장치를 업데이트합니다.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>첫 번째 장치가 새 Screens 프로젝트에 추가될 때마다 사용자 그룹이 생성됩니다.
>예를 들어 프로젝트 노드 이름이 인 경우 *we-retail*, 사용자 그룹 이름: *screens-we-retail-devices*.
>이 그룹은 의 멤버로 추가됩니다. **참가자** 아래 그림과 같이 그룹화합니다.

![chlimage_1-39](assets/chlimage_1-39.png)

### 다음 단계 {#the-next-steps}

디스플레이에 채널 할당에 익숙해지면 다음 리소스를 참조하십시오.

* [모니터링 및 문제 해결](monitoring-screens.md)
