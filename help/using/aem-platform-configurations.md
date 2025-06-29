---
title: AEM 플랫폼 구성
description: 이 페이지에서는 AEM 플랫폼 구성에 대해 설명합니다
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# AEM 플랫폼 구성 {#platform-configurations}

>[!NOTE]
>
>이 활동의 일반적인 이해 당사자는 AEM 구현자입니다.

아래 섹션에 따라 AEM Screens 플랫폼 구성을 설정하여 AEM을 시작하십시오.

## 서버 구성 {#server-configurations}

서버 구성을 설정하려면 [서버 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration)을 참조하십시오.

## Author-Publish {#author-publish}

[AEM Screens에서 작성자 및 게시 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)을 참조하십시오.

>[!NOTE]
>
>작성자 및 게시자가 한 명만 있는 경우 [AEM Screens에서 작성자 및 게시 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) 페이지에서 **작성자에 대한 복제 에이전트 설정**&#x200B;의 단계만 따를 수 있습니다.

## Dispatcher 구성 {#dispatcher-configurations}

Dispatcher은 Adobe Experience Manager의 캐싱 및 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 엔터프라이즈급 웹 서버와 함께 Dispatcher을 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

AEM Screens 프로젝트에 대해 Dispatcher을 구성하기 위한 지침을 강조 표시하는 **[AEM Screens용 Dispatcher 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**&#x200B;을 참조하십시오.

## FFMpeg 및 비디오 표현물 설치 {#installing-ffmpeg}

적절한 OS(일반적으로 RHEL)의 단계에 따라 FFMpeg를 설치합니다.

1. EPEL 및 RPMFusion을 활성화하여 설치하는 경우 모든 gstreamer 코덱을 설치하여 FFmpeg 변환에 대한 지원을 확대할 수 있습니다
1. AAC 코덱이 experimental로 표시된 경우 ffmpeg 전환이 실패합니다. 이 문제를 방지하려면 비디오 프로필에 `-strict -2`을(를) 추가하십시오(AEM 6.3의 `/etc/dam/video` 및 `/libs/settings/dam/video in AEM 6.4`(으)로 이동함).

   >[!NOTE]
   >
   >`-strict -2`은(는) 매개 변수 목록의 마지막 매개 변수여야 합니다. 또한 AEM 6.4에서 [비디오 표현물](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions)에 언급된 대로 */libs/settings/dam/video* 아래의 노드를 */conf/global/settings/dam/video*&#x200B;에 복사합니다.
1. 비디오 전환이 발생하고 렌디션이 생성 중인지 확인합니다.

## 암호 제한 {#password-restrictions}

AMS 인스턴스에서 AEM의 암호 정책을 비활성화해야 합니다. 또한 Screens 장치 서비스 *com.adobe.cq.screens.device.impl.DeviceService*를 사용하여 웹 콘솔에서 교대로 구성할 수 있습니다.
[AEM Screens에서 작성자 및 게시 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)의 **암호 제한** 섹션을 참조하십시오.

## 환경 설정 {#setting-up-environments}

사용 중인 Adobe Experience Manager 버전(AEM)에 대해 최신 버전의 다음 패키지를 설치하고 실행합니다.

* AEM 서비스 팩
* Screens 기능 팩
* AEM 누적 수정 팩

위의 항목 외에도 모든 개발 패키지(예: WCM 코어)를 식별합니다
구성 요소) 또는 필요한 타사 툴킷(예: SAP Hybris)
로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다. 모든 QA, 스테이지 및 프로덕션 서버에서 동일한 구성을 채택하도록 클라이언트에 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.

>[!NOTE]
>
>AEM Screens용 최신 기능 팩을 설치하려면 [릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/aem-screens-introduction)를 참조하세요.

## ACL 설정 {#setting-up-acls}

ACL을 설정하면 각 개인 또는 팀이 자체 프로젝트를 처리하도록 프로젝트를 분리하는 방법을 설명합니다.

자세한 내용은 [ACL 설정](https://experienceleague.adobe.com/ko/docs/experience-manager-screens/user-guide/administering/setting-up-acls)을 참조하십시오.
