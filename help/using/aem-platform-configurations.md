---
title: AEM Platform 구성
seo-title: AEM Platform 구성
description: 이 페이지에서는 AEM 플랫폼 구성에 대해 설명합니다.
seo-description: 이 페이지에서는 AEM 플랫폼 구성에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# AEM Platform 구성  {#platform-configurations}

>[!NOTE]
>
>이 활동의 일반적인 이해 관계자는 AEM 구현자입니다.

AEM Screens을 시작하려면 아래 섹션을 따르십시오.

## 서버 구성 {#server-configurations}

서버 구성을 설정하려면 [서버 구성](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)을 참조하십시오.

## 작성자-게시 {#author-publish}

author-publish를 설정하려면 [AEM Screens에서 작성자 및 게시 구성](https://helpx.adobe.com/kr/experience-manager/6-5/screens/using/author-and-publish.html)을 참조하십시오.

>[!NOTE]
>
>작성자 및 게시자가 한 명만 있는 경우, **AEM Screens의 작성자 및 게시 구성**&#x200B;에서 [작성자에 대한 복제 에이전트 설정](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) 아래의 단계만 수행하면 됩니다.

## 발송자 구성 {#dispatcher-configurations}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

AEM Screens 프로젝트에 대한 디스패처 구성에 대한 지침을 강조 표시하는 AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**에 대한**[&#x200B;디스패처 구성을 참조하십시오.

## FFMpeg 및 비디오 변환 설치 {#installing-ffmpeg}

해당 OS(일반적으로 RHEL)에 대한 단계에 따라 FFMpeg를 설치합니다.

1. EPEL 및 RPMFfusion을 활성화하여 설치하는 경우 모든 gstreamer 코덱을 설치하여 FFmpeg 변환 지원을 확대할 수 있습니다
1. AAC 코덱이 시험형으로 표시된 경우 ffmpeg 변환이 실패합니다. 이 문제를 방지하려면 AEM 6.3의 비디오 프로필(/etc/dam/video에 있는 -strict -2를 추가하고 AEM 6.4의 /libs/settings/dam/video로 이동했습니다.)
   >[!NOTE]
   >
   > -strict -2는 매개 변수 목록의 마지막 매개 변수여야 합니다. 또한 AEM 6.4에서는 [비디오 변환](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)에 언급된 대로 */libs/settings/dam/video* 아래의 노드를 */conf/global/settings/dam/video*&#x200B;에 복사해야 합니다.
1. 비디오 전환이 발생하고 변환이 만들어지고 있는지 확인합니다.

## 암호 제한 사항 {#password-restrictions}

AMS 인스턴스에서 AEM의 암호 정책을 비활성화해야 합니다. 스크린 장치 서비스 *com.adobe.cq.screens.device.impl.DeviceService*를 사용하여 웹 콘솔에서 전환할 수 있습니다.
AEM Screens[에서 작성자 및 게시 구성의 **암호 제한** 섹션을 참조하십시오.](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## 환경 설정 {#setting-up-environments}

사용 중인 Adobe Experience Manager(AEM) 버전에 대해 다음 패키지의 최신 버전을 설치하고 실행합니다.

* AEM 서비스 팩
* 스크린 기능 팩
* AEM Cumulative 수정 팩

위의 내용 이외에 모든 개발 패키지(예: WCM Core) 식별
구성 요소) 또는 필요한 제3자 도구 키트(예: SAP Hybris)입니다.
로컬 개발 환경에 동일한 소프트웨어 패키지를 설치합니다. 클라이언트가 모든 QA, Stage 및 Production 서버에서 동일한 구성을 채택하도록 지시합니다. 서버 구성이 일치하지 않으면 배포 및 테스트 시 문제가 발생합니다.

>[!NOTE]
>
>AEM Screens용 최신 기능 팩을 설치하려면 [릴리스 노트](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)를 참조하십시오.

## ACL 설정 {#setting-up-acls}

ACL 설정에 따라 개별 또는 팀이 자신의 프로젝트를 처리하도록 프로젝트를 분리하는 방법이 설명되어 있습니다.

자세한 내용은 [ACL 설정](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html)을 참조하십시오.
