---
title: 워크플로우를 사용하여 AEM Screens 채널에 대한 자산 업데이트 자동화
description: Adobe Experience Manager에 업로드된 에셋을 자동으로 처리하고 Screens 채널에 동적으로 할당하는 워크플로우를 만드는 방법을 알아봅니다.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# 워크플로우를 사용하여 AEM Screens 채널에 대한 자산 업데이트 자동화 {#automate-channel-updates-workflow}

Adobe Experience Manager에 업로드된 에셋을 자동으로 처리하고 Screens 채널에 동적으로 할당하는 워크플로우를 만드는 방법을 알아봅니다. 이 예제에서 워크플로우는 이미지가 특정 폴더에 추가되면 트리거됩니다. 워크플로는 동적 텍스트 오버레이(워터마크 프로세스)를 적용하고 이미지를 스크린 채널에 지정합니다. 이 예제를 통해 얻은 교훈은 매우 다양한 자동화 시나리오에 적용할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이 자습서를 완료하려면 다음 항목이 필요합니다.

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM 서비스 팩 8 이상](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 이상](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## 빠른 설정 {#quick-setup}

아래 비디오에서는 Adobe Experience Manager에 새 워크플로를 도입한 샘플 코드 패키지를 설치하는 방법을 보여 줍니다. 이 기능을 사용하면 AEM Assets에서 Screens 채널을 가리키도록 폴더의 속성을 업데이트할 수 있습니다. 이미지가 해당 폴더에 추가될 때마다 지정된 AEM Screens 채널에 추가됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 컴파일된 코드 패키지를 다운로드합니다. **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. AEM 패키지 관리자를 사용하여 위의 패키지를 설치합니다.

## 워크플로우 모델 {#workflow-model}

이미지를 추가해야 하는 대상 Screens 채널을 캡처하기 위해 사용자 지정 폴더 메타데이터 스키마를 만들었습니다. 두 개의 워크플로우 모델을 사용하여 에셋 처리를 자동화합니다. 다음 **DAM 자산 업데이트** 대상 Screens 채널을 결정하기 위해 에셋의 포함 폴더를 검사하는 사용자 지정 워크플로 **Screens 데모 에셋 처리)를 호출하도록 워크플로를 편집합니다. 다음 **화면 데모 자산 처리** 워크플로우에서는 이미지에 워터마크를 적용하는 것도 담당합니다.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 사용자 지정 워크플로우 프로세스 단계 {#workflow-process-step}

Inspect 의 일부로 사용되는 두 가지 사용자 지정 워크플로우 프로세스 단계 **화면 데모 자산 처리** 워크플로입니다.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

다음 `AssetProcessingCheck.java` 사용자 지정 워크플로는 워크플로의 페이로드를 확인하는 프로세스입니다. 페이로드가 자산인지, 포함된 폴더가 AEM Screens 채널을 가리키도록 구성되었는지 확인합니다. 요구 사항이 충족되면 프로세스 단계에서 두 가지 속성이 유지됩니다. `screen-channel` 및 `asset-path`을 클릭하여 워크플로의 메타데이터로 만듭니다.

다음 `AddAssetToChannel.java` 사용자 지정 워크플로는 워크플로의 메타데이터를 검사하고 이미지를 참조하도록 AEM Screens 채널을 업데이트하는 프로세스 단계입니다.

1. 소스 코드를 다운로드합니다. **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 즐겨찾는 IDE를 사용하여 코드 압축을 풀고 코드를 봅니다.
