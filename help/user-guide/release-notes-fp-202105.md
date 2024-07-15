---
title: 기능 팩 202105 릴리스 정보
description: 2021년 6월 4일에 릴리스된 AEM Screens 기능 팩 202105에 대해 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 3%

---

# 기능 팩 202105 릴리스 정보 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe 최신 버전의 Adobe Experience Manager(AEM)로 업그레이드하는 것이 좋습니다. AEM Screens은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 8을 출시했습니다.

Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens 6.5.8 릴리스용 최신 기능 팩을 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;을(를) 검색하여 **AEM 6.5 Screens FP8**(으)로 제목이 지정된 최신 기능 팩을 가져옵니다.

>[!IMPORTANT]
>패키지 `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` 및 `screens core bundles`을(를) 설치한 후 AMS 커넥터가 작동하도록 AEM 6.5 기능 팩 8의 최소 버전을 설치하십시오.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 202105의 릴리스 날짜는 2021년 6월 4일입니다.

### 새로운 기능 {#what-is-new}

* **AEM Screens 채널에서 페이지 잠금**

  AEM ScreensAEM Sites 에서 이미 구현한 대로 이제 *페이지 잠금*&#x200B;을 지원합니다. Adobe Experience Manager(AEM)를 사용하면 다른 사람이 컨텐츠를 편집할 수 없도록 페이지를 잠글 수 있습니다. 이 기능은 하나의 특정 페이지를 여러 번 편집하거나 잠시 동안 페이지를 동결해야 할 때 유용합니다.

* **AEM Screens 플레이어 장치 이름 지정**

  이제 AEM Screens 플레이어에 장치 이름을 Adobe Experience Manager(AEM)로 전송하는 기능이 포함됩니다.
기본적으로 일괄 등록을 사용하여 장치를 등록하면 시스템에서 생성한 사용자 이름이 제목 필드에 입력됩니다. 또한 고객은 에셋 태그 또는 기타 친숙한 이름을 사용하여 AEM에서 볼 수 있고 적절한 콘텐츠를 보다 쉽게 할당할 수 있습니다.

  지원되는 각 운영 체제에서 이름을 구성하는 방법에 대한 자세한 내용은 다음 설명서를 참조하십시오.

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **매니페스트 생성**

  서버에서 더 적은 리소스를 할당하는 등 성능이 향상되어 채널 매니페스트를 더 빨리 생성할 수 있습니다.

### 버그 수정 {#bug-fixes}

* 플레이어는 동적 임베디드 시퀀스가 포함된 채널로 전환할 때 검정색 화면을 표시했습니다.
* 이제 Screens 플레이어는 404 오류 또는 오류 메시지가 있는 페이지를 더 이상 피하는 끊어진 채널로의 전환을 차단합니다.

### 릴리스된 AEM Screens 플레이어

AEM 6.5 기능 팩 8용으로 출시된 AEM Screens 플레이어는 다음과 같습니다.

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens 플레이어 다운로드

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 **[AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
