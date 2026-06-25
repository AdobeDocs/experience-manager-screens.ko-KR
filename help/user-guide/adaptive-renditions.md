---
title: 적응형 렌디션 아키텍처 개요 및 구성
description: AEM Screens의 적응형 변환을 위한 CRXDE Lite의 아키텍처 개요 및 구성에 대해 알아봅니다.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
TQID: https://experienceleague.adobe.com/6kL7RJWr-AJQsQdBqE-GI8lI-6QQXTNiRXP4maEdmzA
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 703
ht-degree: 4%

---

# 적응형 표현물: 아키텍처 개요 및 구성 {#adaptive-renditions}

>[!IMPORTANT]
>이 콘텐츠는 AEM On-Premise/AMS(AEM 6.5LTS 및 AEM 6.5)에 유효합니다. AEM as a Cloud Service Screens 콘텐츠의 경우 [AEM as a Cloud Service 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)를 참조하십시오.

## 소개 {#introduction}

>[!CAUTION]
>이 기능은 AEM 온-프레미스(AEM 6.5)에서만 지원됩니다. AEM as a Cloud Service에서는 지원되지 않습니다.

적응형 렌디션을 사용하면 장치가 고객 정의 규칙에 따라 장치에 가장 적합한 렌디션을 자동으로 클릭할 수 있습니다. 장치는 이러한 규칙에 따라 에셋의 가장 적절한 표현물을 자동으로 다운로드하고 재생하므로 고객은 *main* 경험만 디자인하는 데 집중할 수 있습니다.

## 목표 {#objective}

이제 AEM Screens 개발자로서 모든 콘텐츠 변형을 수동으로 만들지 않고도 장치별 에셋 렌디션을 자동으로 다운로드하고 재생하도록 구성할 수 있습니다. 콘텐츠 작성자가 AEM Screens 채널에서 이 기능을 사용하기 전에 적응형 렌디션을 구성합니다.

## 아키텍처 개요 {#architectural-overview}

적응형 렌디션은 특정 명명 규칙에 따라 이름이 지정된 에셋에 대한 여러 렌디션을 갖는 개념을 기반으로 합니다. 특정 렌디션을 재생하려면 예상되는 기능이 있는 장치에서만 확인할 수 있는 미디어 쿼리 식을 평가해야 합니다.

연관된 렌디션 이름 지정 패턴이 있는 기능은 아래 그림과 같이 세로 또는 가로와 같은 렌디션 매핑 규칙을 정의합니다. 사용 가능한 모든 표현식을 계산한 후 Screens 플레이어는 일치하는 규칙에 해당하는 이름 지정 패턴을 수집합니다. 패턴은 렌디션 이름에서 패턴을 찾아 시퀀스 재생 중에 올바른 렌디션을 찾는 데 사용됩니다.

![이미지](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Screens 프로젝트에 렌디션 매핑 속성 추가 {#rendition-mapping-new}

적응형 렌디션 기능을 활성화하려면 다음 매핑 규칙이 있어야 하며 채널 및 디스플레이에 대한 CA(컨텍스트 인식) 구성을 해결해야 합니다.

>[!NOTE]
>콘텐츠 인식 구성에 대한 자세한 내용은 [여기](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)를 참조하세요.

아래 단계에 따라 설정을 구성하십시오.

1. **CRXDE Lite**(으)로 이동합니다. 아래 그림과 같이 `/conf/screens/sling:configs/rendition-mapping`에 **렌디션 매핑** 구성이 있는지 확인합니다.

   >![이미지](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >최신 기능 팩 202109을 설치한 경우 CRXDE Lite의 `/conf/screens/sling:configs/rendition-mapping`에서 미리 채워진 **렌디션 매핑** 노드 구조가 표시됩니다. 최신 기능 팩에 대한 자세한 내용은 [기능 팩 릴리스 정보 202109](/help/user-guide/release-notes-fp-202109.md)를 참조하십시오.
   >기존 프로젝트의 경우 Screens 프로젝트에 **렌디션 매핑** 구성이 연결되어 있는지 확인하십시오. 자세한 내용은 [기존 프로젝트에 렌디션 매핑 추가](#rendition-mapping-existing) 섹션을 참조하십시오.

### 기존 프로젝트에 렌디션 매핑 속성 추가 {#rendition-mapping-existing}

1. **CRXDE Lite**(으)로 이동합니다.

1. 아래 그림과 같이 프로젝트 콘텐츠 노드에 `/conf/screens`을(를) 가리키는 `sling:configRef` 속성을 추가하여 렌디션 매핑 연결을 명시적으로 정의합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 렌디션 매핑 규칙 추가 {#add-rendition-mapping-rules}

렌디션 매핑에 노드를 추가하려면 아래 단계를 따르십시오.

1. **CRXDE Lite**&#x200B;에서 이 경로 `/conf/screens/sling:configs/rendition-mapping`(으)로 이동합니다.
1. **렌디션 매핑** 아래에 노드를 만듭니다. 아래 그림과 같이 **렌디션 매핑**&#x200B;을 마우스 오른쪽 단추로 클릭하고 **만들기** > **노드 만들기**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. **노드 만들기** 대화 상자에서 **규칙1**&#x200B;과(와) 같은 매핑 규칙에 대한 **이름**&#x200B;과(와) **유형**&#x200B;을(를) **`nt:unstructured`**(으)로 입력하십시오. **확인**&#x200B;을 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 쿼리 표현식이 포함된 값으로 표현식 속성을 추가합니다.

   >[!NOTE]
   >자세한 내용은 [미디어 쿼리 구문 사용](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)을 참조하세요.

   만든 **규칙1**&#x200B;을(를) 클릭하고 아래와 같이 **이름**&#x200B;에 **식**&#x200B;을(를), **값**&#x200B;에 **(방향:landscape)**&#x200B;을(를) 입력합니다. **추가**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 렌디션 이름 지정 패턴을 포함하는 값으로 패턴 속성을 추가합니다.

   >[!NOTE]
   >표현식이 true로 평가되는 경우 패턴 속성에 정의된 값이 새 자산 렌디션과 일치하고 선택됩니다.

   패턴 속성을 추가하려면 만든 **rule1**&#x200B;을 클릭하고 아래와 같이 **Name**&#x200B;에 **pattern**&#x200B;을(를) 입력하고 **Value**&#x200B;에 **landscape**&#x200B;을(를) 입력하십시오. **추가**&#x200B;를 클릭합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. **모두 저장**&#x200B;을 클릭하고 **렌디션 매핑**&#x200B;에서 만든 노드 아래의 속성을 확인합니다.

   ![이미지](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 다음 단계 {#next-steps}

콘텐츠 작성자는 렌디션 매핑 속성 및 규칙을 추가한 후 에셋을 구성할 수 있습니다. 적응형 렌디션을 사용하고 대규모 네트워크용으로 디바이스를 마이그레이션하여 AEM Screens 채널에서 이 기능을 사용할 수도 있습니다. 자세한 내용은 [AEM Screens에서 적응형 표현물 사용](/help/user-guide/using-adaptive-renditions.md)을 참조하십시오.
