---
title: 기능 팩 202109 릴리스 정보
description: 2021년 9월 23일에 릴리스된 AEM Screens 기능 팩 202109에 대해 알아보십시오.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# 기능 팩 202109 릴리스 정보 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe에서는 최신 버전의 Adobe Experience Manager(AEM)로 업그레이드하는 것이 좋습니다. AEM Screens은 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 9를 출시했습니다.

Adobe ID을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 AEM Screens 6.5.9 릴리스용 최신 기능 팩을 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;을(를) 검색하여 **AEM 6.5 Screens FP9**(으)로 제목이 지정된 최신 기능 팩을 가져옵니다.

## 릴리스 일자 {#release-date}

AEM Screens 기능 팩 202109의 릴리스 날짜는 2021년 9월 23일입니다.

### 새로운 기능 {#what-is-new}

* **비디오에 대한 썸네일 지원**

  이제 AEM Screens에서 비디오에 대한 썸네일 지원이 제공됩니다. 콘텐츠 작성자는 이미지를 자리 표시자로 사용할 수 있도록 비디오의 썸네일을 정의합니다. 또한 적절한 팀이 실제 비디오를 마무리하는 동안 콘텐츠 재생 및 타깃팅을 적절하게 테스트합니다. 비디오 재생이 실패할 경우 이미지를 사용할 수도 있습니다.
자세한 내용은 [비디오에 대한 썸네일 지원](/help/user-guide/thumbnail-support.md)을 참조하십시오.

* **기본 재생 모니터링**

  이제 AEM Screens에서 기본 재생 모니터링을 지원합니다. 이제 플레이어는 각 ping으로 다양한 재생 지표를 보고합니다(기본값은 30초). 지표를 기반으로 다양한 극단적 사례(중단 경험, 빈 화면, 일정 문제 등)를 감지합니다. 이 기능을 통해 팀은 플레이어가 콘텐츠를 제대로 재생하는지 원격으로 모니터링할 수 있으며 필드의 빈 화면이나 깨진 경험에 대한 반응성을 향상시킬 수 있습니다. 또한 최종 사용자에게 손상된 경험이 표시될 위험을 줄여줍니다.
자세한 내용은 [기본 재생 모니터링](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring)을 참조하세요.

* **콘텐츠 할당 보고서에 대한 업데이트**

  이제 콘텐츠 할당 보고서가 최적화되고 사용자 환경이 개선되었습니다. 다운로드 가능한 보고서에는 향상된 플레이어 관련 엔티티가 표시됩니다. 이러한 엔티티는 하나의 스프레드시트 탭에 위치, 디스플레이 및 디바이스를 포함합니다. 또한 기타 탭에 채널 및 에셋과 같은 콘텐츠 공급자 정보가 포함됩니다.
자세한 내용은 [콘텐츠 할당 보고서](/help/user-guide/content-assignment-report.md)를 참조하세요.

* **적응형 표현물**

  적응형 렌디션을 사용하면 고객이 정의한 규칙에 따라 장치에서 자동으로 최상의 렌디션을 클릭할 수 있습니다.

  이제 AEM Screens 개발자로서 모든 콘텐츠 변형을 수동으로 만들지 않고도 장치별 에셋 렌디션을 자동으로 다운로드하고 재생하도록 구성할 수 있습니다. 자세한 내용은 [응용 렌디션: 아키텍처 개요 및 구성](/help/user-guide/adaptive-renditions.md)을 참조하십시오.

  또한 AEM Screens 콘텐츠 작성자는 적응형 렌디션을 사용하도록 에셋을 구성할 수 있습니다. 대규모 네트워크에 대해 장치를 마이그레이션하여 AEM Screens 채널에서 이 기능을 사용할 수도 있습니다. 자세한 내용은 [AEM Screens에서 적응형 표현물 사용](/help/user-guide/using-adaptive-renditions.md)을 참조하십시오.

* **V3 매니페스트 지원**

  이제 Dispatcher for Manifest 버전 v3을 구성할 수 있습니다. v3 Manifest를 활성화하려면 다음을 수행하십시오.

   * 작성자와 게시자에서 보류 중인 오프라인 콘텐츠 작업을 모두 지웁니다.

      * 작성자 및 게시에서 CRXDE Lite 로 이동합니다.

      * 도구 > 쿼리를 클릭합니다.

      * 쿼리에서 `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`을(를) 사용합니다.

      * 현재 실행 중이거나 큐에서 보류 중인 오프라인 콘텐츠 작업이 모두 나열됩니다.

      * 쿼리에서 오프라인 콘텐츠 작업이 더 이상 반환되지 않을 때까지 기다립니다.

   * `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`에서 ContentSync를 사용하지 않도록 설정합니다.

   * `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`에서 SmartSync를 사용하도록 설정합니다.

   * Dispatcher 업데이트.

   * 사용자 지정 구성 요소를 업데이트합니다.


   * 자세한 내용은 [매니페스트 버전 v3에 대한 Dispatcher 구성](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)을 참조하세요.
   * 사용자 지정 구성 요소를 v3 매니페스트의 일부로 사용하는 경우 [사용자 지정 처리기용 템플릿](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)을 참조하세요.


### 버그 수정 {#bug-fixes}

**플레이어측**

* 에셋을 렌디션으로 대체하여 파일 캐싱 오류를 해결했습니다.

* 이제 렌디션 매핑이 있는 경우 플레이어는 에셋 렌디션만 표시합니다.

* 응답이 유효한 JSON이 아닌 경우 재인증하도록 ping이 개선되었습니다.

* 숫자 채널 이름/역할로 인해 빈 화면이 표시되었습니다.

* SmartSync를 통해 최적화된 렌디션을 다운로드합니다.

* 매핑을 렌디션 키 목록으로 변환했습니다.

* Windows Player에서 `cmd.exe` 및 `reg.exe`에 대한 액세스 권한을 제거했습니다.

* 플레이어는 마지막으로 성공한 재생 이벤트를 보고해야 합니다.

* 플레이어는 재생 상태를 보고해야 합니다.

* `ALL` 캐시가 지워진 경우 플레이어가 Assets을 다시 다운로드하지 않습니다.

* 이제 플레이어 관리자는 플레이어 이름을 선택할 수 있습니다.

* 디스플레이에서 채널 할당을 제거해도 플레이어에 반영되지 않습니다.

* 채널 업데이트를 다운로드하는 동안 플레이어가 다시 로드되면 플레이어는 업데이트를 무시합니다.

* 이제 임베드된 페이지 구성 요소는 터치 이벤트를 준수합니다.

* 이제 Tizen 플레이어의 원격 프로비저닝이 지원됩니다.

**서버측**

* 대상 비디오가 표시되지 않음
* 브로드캐스트의 경합 조건은 데이터를 하위 항목에 표시합니다.

* 비디오가 포함된 채널에 대해서는 채널 미리 보기가 작동하지 않습니다.

* 분할 화면 채널에 대해 공백이 표시되는 미리보기 모드.

* 비디오 썸네일은 활성화된 적응형 렌디션을 사용하여 비어 있습니다.

* 참조된 페이지가 게시되는 경우 채널 매니페스트를 자동으로 업데이트합니다.

* 삭제된 장치는 이제 Screens 복제 큐를 차단하지 않습니다.

* 매니페스트에 타깃팅된 콘텐츠 또는 Sites에 포함된 페이지가 없습니다. 이 버그는 이제 수정되었습니다.

* 이제 새 핵심 이미지 구성 요소가 채널 매니페스트에 추가됩니다.

* 이제 SmartSync를 통해 최적화된 렌디션을 다운로드할 수 있습니다.

* 모든 에셋에 대해 최적화된 렌디션을 재생합니다.

* 여러 콘텐츠 공급자 유형에 대한 지원을 추가했습니다.

* 임베드된 시퀀스 재생 전략이 중단되었으며 이 버그가 이제 수정되었습니다.

* html 항목에 대한 요청 매개 변수 `wcmmode`을(를) 사용하여 오프라인 매니페스트를 캐시할 수 없습니다.

* 빈 동적 포함 시퀀스로 인해 빈 화면이 발생하는 경우가 있습니다.

* 이제 플레이어가 재생 상태를 보고합니다.

* 비디오가 `Tiny mode`에서 재생되고 있으며 장치에서 전체 화면 비디오로 재생되지 않으며 문제가 해결되었습니다.

### 릴리스된 AEM Screens 플레이어

AEM 6.5 기능 팩 9용으로 출시된 AEM Screens 플레이어는 다음과 같습니다.

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens 플레이어 다운로드

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 **[AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
