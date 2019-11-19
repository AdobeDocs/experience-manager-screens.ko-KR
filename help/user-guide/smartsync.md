---
title: ContentSync에서 SmartSync로 전환
seo-title: ContentSync에서 SmartSync로 전환
description: 이 페이지에서 SmartSync 기능에 대해 알아보고 ContentSync에서 SmartSync로 전환하는 방법을 알아봅니다.
seo-description: 이 페이지에서 SmartSync 기능에 대해 알아보고 ContentSync에서 SmartSync로 전환하는 방법을 알아봅니다.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# ContentSync에서 SmartSync로 전환{#transitioning-from-contentsync-to-smartsync}

이 섹션에서는 SmartSync 기능에 대한 개요와 서버 로드/스토리지 및 네트워크 트래픽을 최소화하여 비용을 줄이는 방법을 제공합니다.

## 개요 {#overview}

SmartSync는 AEM Screens에서 사용하는 최신 메커니즘입니다. 오프라인 채널을 캐싱하고 플레이어에 전달하는 데 사용되는 현재 방식을 대체하는 역할을 합니다.

서버측 및 클라이언트측에서 모두 실행됩니다.

**서버측**:

* 자산을 포함한 채널의 컨텐츠는 */var/contentsync*&#x200B;에서 캐시됩니다.
* 디스플레이에 사용할 수 있는 컨텐츠를 설명하는 매니페스트를 통해 캐시는 플레이어에 노출됩니다.

**클라이언트측**:

* 플레이어는 위에서 생성된 매니페스트를 기반으로 컨텐츠를 업데이트합니다.

### SmartSync 사용의 이점 {#benefits-of-using-smartsync}

SmartSync 기능은 AEM Screens 프로젝트에 다양한 이점을 제공합니다. Adobe는

* 네트워크 트래픽 및 서버측 스토리지 요구 사항의 급격한 감소
* Player는 에셋이 누락되거나 변경된 경우에만 에셋을 지능적으로 다운로드합니다
* 서버측 및 클라이언트측 스토리지 최적화

>[!NOTE]
>
>AEM Screens 프로젝트에 SmartSync를 사용하는 것이 좋습니다.

## ContentSync에서 SmartSync로 마이그레이션 {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>AEM 6.3 Feature Pack 5 및 AEM 6.4 Feature Pack 3을 이미 설치한 경우 SmartSync를 사용하여 에셋에 대한 기능을 활성화하여 디스크 공간 사용을 향상시킬 수 있습니다. SmartSync를 활성화하려면 아래 섹션에 따라 ContentSync에서 SmartSync로 전환하여 SmartSync를 활성화하십시오.
>
>SmartSync는 지원되는 서버 AEM 6.4.3 FP3가 있는 Screens 플레이어에서 사용할 수 있습니다.
>
>최신 플레이어를 다운로드하려면 [AEM Screens](https://download.macromedia.com/screens/) Player 다운로드를 참조하십시오. 다음 표에서는 각 플랫폼에 필요한 최소 플레이어 버전에 대해 설명합니다.

| **플랫폼** | **지원되는 최소 플레이어 버전** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

ContentSync에서 SmartSync로 전환하려면 아래 절차를 따르십시오.

1. SmartSync를 활성화하기 전에 ContentSync에서 SmartSync로 마이그레이션하려면 ContentSync 캐시를 지우면 됩니다.

   아래 그림과 같이 https://localhost:4502/libs/cq/contentsync/content/console.html 링크를 사용하여 인스턴스에서 ContentSync 콘솔로 ***이동하고*** 캐시 **지우기를**&#x200B;클릭합니다.

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >SmartSync를 처음 사용하기 전에 모든 컨텐츠 캐시를 지워야 합니다.

1. **Adobe Experience Manager 웹 콘솔 구성 **via AEM instance —&gt; 망치 아이콘 —&gt; 작업 **** —&gt; 웹 **콘솔로 이동합니다**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager 웹 콘솔 구성 **이 열립니다. offlinecontentservices *를 검색합니다*.

   **Screens Offline Content Service **속성을 검색하려면 Mac **용** Command+F **를** 누르고 **Windows** 용 Ctrl+F **를**&#x200B;누릅니다.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 저장을 **클릭하여** **Screens 오프라인 콘텐츠 서비스 **** 속성을 활성화하므로 AEM Screens에 SmartSync를 사용합니다.
1. SmartSync를 활성화한 후에는 프로젝트로 이동하고 작업 **표시줄에서** 오프라인 컨텐츠 *업데이트를* 클릭해야 합니다(아래 그림 참조).

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)

