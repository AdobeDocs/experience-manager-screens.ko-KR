---
title: AEM Platform 구성
seo-title: AEM Platform 구성
description: 이 페이지에서는 AEM Platform 구성에 대해 설명합니다
seo-description: 이 페이지에서는 AEM Platform 구성에 대해 설명합니다
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# AEM Platform 구성  {#platform-configurations}

>[!NOTE]
>
>이 활동의 일반적인 이해 담당자는 AEM 구현자입니다.

AEM Screens을 시작할 AEM 플랫폼 구성을 설정하려면 아래 섹션을 따르십시오.

## 서버 구성 {#server-configurations}

서버 구성을 설정하려면 [서버 구성](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)을 참조하십시오.

## Author-Publish {#author-publish}

author-publish를 설정하려면 [AEM Screens에서 작성자 및 게시 구성](https://helpx.adobe.com/kr/experience-manager/6-5/screens/using/author-and-publish.html)을 참조하십시오

>[!NOTE]
>
>작성자 및 게시자가 한 명만 있는 경우, **AEM Screens의 작성자 및 게시 구성**&#x200B;에서 [작성자에 대한 복제 에이전트 설정](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) 아래의 단계만 수행하면 됩니다.

## 디스패처 구성 {#dispatcher-configurations}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

AEM Screens 프로젝트에 대한 Dispatcher 구성 지침을 강조 표시하는 **[AEM Screens용 Dispatcher 구성](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**&#x200B;을 참조하십시오.

## FFMpeg 및 비디오 표현물 설치 {#installing-ffmpeg}

적절한 OS(일반적으로 RHEL)에 대해 다음 단계에 따라 FFMpeg를 설치합니다.

1. EPEL 및 RPMFspion을 활성화하여 설치하는 경우 모든 gstreamer 코덱을 설치하여 FFmpeg 전환에 대한 지원을 확장할 수 있습니다
1. AAC 코덱이 실험용으로 표시된 경우 ffmpeg 전환이 실패합니다. 이렇게 하지 않으려면 비디오 프로필(/etc/dam/video in AEM 6.3에서 /libs/settings/dam/video에 -strict -2를 추가하고 AEM 6.4에서 /libs/settings/dam/video로 이동했습니다.)
   >[!NOTE]
   >
   > -strict -2는 매개 변수 목록에서 마지막 매개 변수가 되어야 합니다. 또한 AEM 6.4에서는 [비디오 표현물](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)에 설명된 대로 */libs/settings/dam/video* 아래의 노드를 */conf/global/settings/dam/video*&#x200B;에 복사해야 합니다.
1. 비디오 전환이 발생하고 변환이 만들어졌는지 확인합니다.

## 암호 제한 {#password-restrictions}

AMS 인스턴스에서 AEM의 암호 정책을 사용하지 않도록 설정해야 합니다. Screens 장치 서비스 *com.adobe.cq.screens.device.impl.DeviceService*를 사용하여 웹 콘솔에서 번갈아 구성할 수 있습니다.
[AEM Screens에서 작성자 및 게시 구성](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)에서 **암호 제한** 섹션을 참조하십시오

## 환경 설정 {#setting-up-environments}

사용 중인 Adobe Experience Manager(AEM) 버전에 대해 다음 패키지의 최신 버전을 설치 및 실행합니다.

* AEM Service Pack
* 스크린 기능 팩
* AEM 누적 수정 팩

위의 사항 외에 모든 개발 패키지(예: WCM 코어)를 식별합니다
구성 요소) 또는 필요한 타사 도구 키트(예: SAP Hybris)입니다.
로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다. 클라이언트에 모든 QA, 스테이지 및 프로덕션 서버에서 동일한 구성을 적용하도록 지시합니다. 일치하지 않는 서버 구성이 배포 및 테스트 시 문제를 만듭니다.

>[!NOTE]
>
>AEM Screens용 최신 기능 팩을 설치하려면 [릴리스 노트](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)를 참조하십시오.

## ACL 설정 {#setting-up-acls}

ACL 설정을 통해 개별 또는 팀이 자체 프로젝트를 처리하도록 프로젝트를 분리하는 방법을 설명합니다.

자세한 내용은 [ACL 설정](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html)을 참조하십시오.
