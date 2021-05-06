---
title: 워크플로우를 사용하여 AEM Screens 채널의 에셋 업데이트 자동화
seo-title: 워크플로우를 사용하여 AEM Screens 채널의 에셋 업데이트 자동화
description: Adobe Experience Manager에 업로드된 자산을 자동으로 처리하고 스크린 채널에 동적으로 할당하는 워크플로우를 만드는 방법을 알아봅니다. 이 예에서는 특정 폴더에 이미지가 추가되면 동적 워터마크를 적용하고 스크린 채널에 이미지를 할당하는 워크플로우가 트리거됩니다. 이 예제를 통해 얻은 교훈을 다양한 자동화 시나리오에 적용할 수 있습니다.
seo-description: Adobe Experience Manager에 업로드된 자산을 자동으로 처리하고 스크린 채널에 동적으로 할당하는 워크플로우를 만드는 방법을 알아봅니다. 이 예에서는 특정 폴더에 이미지가 추가되면 동적 워터마크를 적용하고 스크린 채널에 이미지를 할당하는 워크플로우가 트리거됩니다. 이 예제를 통해 얻은 교훈을 다양한 자동화 시나리오에 적용할 수 있습니다.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: 스크린 개발
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---


# 워크플로우를 사용하여 AEM Screens 채널 {#automate-channel-updates-workflow}에 대한 자산 업데이트 자동화

Adobe Experience Manager에 업로드된 자산을 자동으로 처리하고 스크린 채널에 동적으로 할당하는 워크플로우를 만드는 방법을 알아봅니다. 이 예에서는 특정 폴더에 이미지가 추가되면 동적 워터마크를 적용하고 스크린 채널에 이미지를 할당하는 워크플로우가 트리거됩니다. 이 예제를 통해 얻은 교훈을 다양한 자동화 시나리오에 적용할 수 있습니다.

## 전제 조건 {#prerequisites}

이 자습서를 완료하려면 다음 사항이 필요합니다.

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=ko-KR)
1. [AEM 서비스 팩 8 이상](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=ko-KR)
1. [AEM 6.5 Screens FP7 이상](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 빠른 설정 {#quick-setup}

아래 비디오에서는 Adobe Experience Manager에 새로운 워크플로우를 소개하는 샘플 코드 패키지를 설치하는 방법을 설명합니다. 이 기능을 사용하면 AEM Assets에서 폴더 속성을 업데이트하여 스크린 채널을 가리킬 수 있습니다. 이미지가 해당 폴더에 추가될 때마다 지정된 스크린 채널에 추가됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 컴파일된 코드 패키지를 다운로드합니다.**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. AEM Package Manager를 사용하여 위의 패키지를 설치합니다.

## 워크플로우 모델 {#workflow-model}

이미지를 추가해야 하는 대상 스크린 채널을 캡처하기 위해 사용자 지정 폴더 메타데이터 스키마를 만들었습니다. 자산 처리를 자동화하는 데 두 개의 워크플로우 모델이 사용됩니다. 대상 스크린 채널을 결정하기 위해 자산의 포함 폴더를 검사하는 **Screens 데모 자산 처리**&#x200B;의 사용자 지정 작업 과정을 호출하도록 **DAM 자산 업데이트** 작업 과정이 수정되었습니다. **스크린 데모 자산 처리** 워크플로우도 이미지에 워터마크를 적용합니다.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 사용자 정의 워크플로우 프로세스 단계 {#workflow-process-step}

Inspect **스크린 데모 에셋 처리** 워크플로우의 일부로 사용되는 2개의 사용자 지정 워크플로우 프로세스 단계

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 페이로드가 자산인지 여부 및 포함 폴더가 스크린 채널을 가리키도록 구성되어 있는지 여부를 확인하기 위해 워크플로의 페이로드를 확인하는 사용자 지정 워크플로우 프로세스입니다. 요구 사항이 충족되면 프로세스 단계는 워크플로우의 메타데이터에 대해 `screen-channel` 및 `asset-path` 두 개의 속성을 유지합니다.

`AddAssetToChannel.java` 은 워크플로우의 메타데이터를 검사하고 이미지를 참조하도록 스크린 채널을 업데이트하는 사용자 정의 워크플로우 프로세스 단계입니다.

1. 소스 코드를 다운로드합니다.**[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 즐겨 사용하는 IDE를 사용하여 코드의 압축을 풀고 코드를 봅니다.
