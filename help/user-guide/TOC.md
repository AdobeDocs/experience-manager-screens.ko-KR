---
cloud: Experience Cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 도움말
breadcrumb-title: AEM Screens 안내서
user-guide-description: 동적 및 대화형 디지털 경험과 상호 작용을 게시할 수 있는 디지털 서명 솔루션을 사용하는 방법을 알아봅니다.
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: 1bd79ed3a0a610efb12f9ff1030a33978ccccf1e
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 11%

---


# AEM Screens 사용 안내서 {#user-guide}

+ [Screens 소개](aem-screens-introduction.md)
+ 개요 및 킥스타트 안내서 {#overview}
   + [킥스타트 안내서](kickstart-for-aem-screens.md)
   + [Screens 모범 사례 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-screens/using/about-guide)
   + [주요 용어](screens-glossary.md)
+ 디지털 간판 네트워크 기본 사항 {#digital-signage-network}
   + [1부: 프로젝트 역할 및 책임](project-roles-responsibilities.md)
   + [2부: 프로젝트 범위 지정 시 고려 사항](project-considerations.md)
   + [3부: 테스트, POC, 파일럿 및 롤아웃](testing-pocs-pilots-rollouts.md)
   + [4부: 프로젝트 관리 및 배포](project-management-and-deployment.md)
   + [5부: 지원 고려 사항](support-considerations.md)
+ 구성 및 관리 {#administering}
   + [Screens 서버 구성](configuring-screens-introduction.md)
   + [Dispatcher 구성 설정](dispatcher-configurations-aem-screens.md)
   + [Screens 플레이어 설치](installing-screens-player.md)
   + [스크린 플레이어 연결 중](working-with-screens-player.md)
   + [장치 등록](device-registration.md)
   + [ACL 설정](setting-up-acls.md)
   + [AEM Screens 보안 검사 목록](security-checklist.md)
   + [ContentSync에서 SmartSync로 전환](smartsync.md)
   + [파일의 새 프로젝트 가져오기](project-importer.md)
   + [게시 서버에 데이터 트리거 복제](replicating-data-triggers.md)
   + [화면에 복제 에이전트 구성](configure-screens-replication.md)
   + 클라이언트별 고려 사항 {#installing-client}
      + [크롬 OS 플레이어](implementing-chrome-os-player.md)
      + [Chrome Player를 문제 해결을 위한 확장 프로그램으로 사용](using-chrome-player-as-an-extension.md)
      + [Android](implementing-android-player.md)
      + [Windows 플레이어](implementing-windows-player.md)
      + [플레이어 티즌](tizen-player.md)
      + [Cloud Player](implementing-cloud-player.md)
      + [플레이어 자동 등록](auto-registration-players.md)
      + [원격 제어 사용](implementing-remote-control.md)
   + Author 게시 {#author-publish}
      + [Author-Publish 아키텍처 개요](author-publish-architecture-overview.md)
      + [작성자 및 게시 구성](author-and-publish.md)
   + AEM Screens과 Analytics 통합 {#analytics-integration}
      + [Adobe Analytics 통합](adobe-analytics-integration-aem-screens.md)
      + [AEM Screens을 사용하여 Adobe Analytics 구성](configuring-adobe-analytics-aem-screens.md)
+ 작성 및 사용 사례 예 {#authoring}
   + Screens 프로젝트 설정 {#setting-up-projects}
      + [프로젝트 생성 및 관리](creating-a-screens-project.md)
      + [채널 만들기 및 관리](managing-channels.md)
      + [디스플레이 만들기 및 관리](managing-displays.md)
      + [위치 생성 및 관리](managing-locations.md)
      + [스케줄 생성 및 관리](managing-schedules.md)
      + [장치 관리](managing-devices.md)
      + 채널 할당 {#assigning-channels}
         + [채널 지정](channel-assignment-latest-fp.md)
         + [채널 할당: 이전 AEM Screens 기능 팩](channel-assignment.md)
   + 핵심 제품 기능 사용 {#product-features}
      + [텍스트 오버레이](text-overlay.md)
      + [벌크 오프라인 업데이트](bulk-offline-update.md)
      + [AEM Screens 알림 서비스](screens-notifications-service.md)
      + [경험 조각 사용](experience-fragments-in-screens.md)
      + [자산 수준 활성화](asset-level-scheduling.md)
      + [채널 수준 활성화](channel-level-activation.md)
      + [라이브 카피 만들기 및 관리](managing-livecopy.md)
      + [비디오 패딩 워크플로우 만들기](creating-a-video-padding-workflow.md)
      + [채널에 구성 요소 추가](adding-components-to-a-channel.md)
      + [포함된 시퀀스](embedded-sequences.md)
      + [다중 영역 레이아웃](multi-zone-layout-aem-screens.md)
      + [비디오 표현물](generating-renditions.md)
      + [동적 포함된 시퀀스](dynamic-embedded-sequences.md)
      + [채널 레벨 벌크 이미지 재생 기간](channel-level-image-playback.md)
      + [명령 동기화](using-command-sync.md)
      + [데이터 트리거를 사용하여 작성](authoring-data-triggers.md)
      + [태그 사용](tagging.md)
      + [음성 인식](voice-recognition.md)
      + [컨텐츠 할당 보고서](content-assignment-report.md)
      + [비디오에 대한 썸네일 지원](thumbnail-support.md)
      + [AEM Screens에서 적응형 표현물 사용](using-adaptive-renditions.md)
   + 컨텐츠 업데이트 관리 {#content-updates}
      + [온디맨드 콘텐츠 업데이트](on-demand-content.md)
      + [Content as-a-service 업데이트](content-update-as-a-service.md)
      + [Screens Launch를 사용한 콘텐츠 업데이트](launches.md)
   + 사용 사례 예 {#use-case-examples}
      + [긴급 채널](emergency-channel.md)
      + [여행 센터 온도 활성화](local-temperature-activation.md)
      + [숙박 예약 활성화](hospitality-reservation-activation.md)
      + [소매 재고 타깃팅 활성화](retail-inventory-activation.md)
      + [전환 적용](applying-transitions.md)
      + [다중 영역에서 단일 영역으로 전환](multizone-to-singlezone.md)
      + [단일 사용 전환 채널](single-use-takeover-channel.md)
      + [TakeOver Channel의 지속적인 사용](perpetual-takeover-channel.md)
+ 개발자 및 API 리소스 {#developing}
   + [REST API](rest-api.md)
   + [AEM Screens용 맞춤형 구성 요소 개발](developing-custom-component-tutorial-develop.md)
   + [오프라인 채널](offline-channels.md)
   + [AEM Screens 구성 요소 확장](extending-component-tutorial-develop.md)
   + [구성 요소 만들기](creating-components.md)
   + [AEM SPA Editor를 사용하여 REACT 애플리케이션 임베드 및 AEM Screens Analytics와 통합](embedding-react-app.md)
   + [AEM Screens에서 ContextHub 구성](configuring-context-hub.md)
   + [다중 영역 레이아웃에 대한 사용자 지정 템플릿 만들기](creating-custom-templates-multizone-layouts.md)
   + [텍스트 오버레이에 사용자 정의 브랜딩 및 스타일 적용](custom-branding-text-overlays.md)
   + [적응형 표현물: 아키텍처 개요 및 구성](/help/user-guide/adaptive-renditions.md)
+ 문제 해결 및 FAQ {#troubleshooting}
   + [AEM SCREENS FAQ](aem-screens-faqs.md)
   + [장치 제어 센터 문제 해결](monitoring-screens.md)
   + [비디오 재생 구성](troubleshoot-videos.md)
+ 릴리스 정보 {#release-notes}
   + [기능 팩 202401 릴리스 정보](release-notes-fp-202401.md)
   + [기능 팩 20240116 릴리스 정보](release-notes-fp-20240116.md)
   + [기능 팩 20240215 릴리스 정보](release-notes-fp-20240215.md)
   + [기능 팩 202204 릴리스 정보](release-notes-fp-202204.md)
   + [기능 팩 202203 릴리스 정보](release-notes-fp-202203.md)
   + [기능 팩 202112 릴리스 정보](release-notes-fp-202112.md)
   + [기능 팩 202109 릴리스 정보](release-notes-fp-202109.md)
   + [기능 팩 202105 릴리스 정보](release-notes-fp-202105.md)
   + [기능 팩 202103 릴리스 정보](release-notes-fp-202103.md)
   + [기능 팩 202011 릴리스 정보](release-notes-fp-202011.md)
   + [기능 팩 202008 릴리스 정보](release-notes-fp-202008.md)
   + [기능 팩 202004 릴리스 정보](release-notes-fp-202004.md)
   + [기능 팩 202001 릴리스 정보](release-notes-fp-202001.md)
   + [기능 팩 201909 릴리스 정보](release-notes-fp-201909.md)
   + [기능 팩 201907 릴리스 정보](release-notes-fp-201907.md)
   + [기능 팩 201905 릴리스 정보](screens-release-notes-fp-201905.md)
   + [기능 팩 201812 릴리스 정보](release-notes-fp-201812.md)
   + [기능 팩 201809 릴리스 정보](screens-release-notes.md)
