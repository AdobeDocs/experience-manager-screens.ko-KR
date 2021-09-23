---
title: 기능 팩 202109 릴리스 노트
description: 2021년 9월 23일에 릴리스된 AEM Screens 기능 팩 202105에 대한 정보를 보려면 이 페이지를 따르십시오.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# 기능 팩 202109 릴리스 노트 {#release-notes-for-feature-pack}

>[!CAUTION]
>최신 버전의 Adobe Experience Manager(AEM)으로 업그레이드하는 것이 좋습니다. Screens에서는 AEM 6.3 Screens 플랫폼에 대한 유지 관리 지원을 제공합니다.

## 사용 가능 {#availability}

AEM Screens은 AEM 6.5 기능 팩 9를 출시했습니다.

AEM Screens 6.5.9 릴리스의 최신 기능 팩은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)에서 Adobe ID을 사용하여 다운로드할 수 있습니다. **Adobe Experience Manager** 탭으로 이동하여 **Screens**&#x200B;에서 **AEM 6.5 Screens FP9**&#x200B;라는 최신 기능 팩을 가져옵니다.

## 릴리스 날짜 {#release-date}

AEM Screens 기능 팩 202109의 릴리스 날짜는 2021년 9월 23일입니다.

### 새로운 기능 {#what-is-new}

* **비디오에 대한 축소판 지원**

   의 비디오에 대한 축소판 지원은 이제 AEM Screens에서 지원됩니다. 컨텐츠 작성자는 해당 팀이 실제 비디오를 마무리하는 동안 이미지를 자리 표시자로 사용하고 컨텐츠 재생 및 타깃팅을 적절히 테스트할 수 있도록 비디오의 축소판을 정의할 수 있습니다. 비디오를 재생하지 못할 경우에 이미지를 사용할 수도 있습니다.
자세한 내용은 [비디오에 대한 축소판 지원](/help/user-guide/thumbnail-support.md)을 참조하십시오.

* **기본 재생 모니터링**

   이제 AEM Screens에서 기본 재생 모니터링을 지원합니다. 이제 플레이어는 각 ping을 사용하여 다양한 재생 지표를 보고합니다(기본값 30초). 지표를 기반으로 다양한 에지 사례(멈춤 경험, 빈 화면, 예약 문제 등)를 탐지하는 기능을 제공합니다. 이 기능을 사용하면 팀이 플레이어가 제대로 컨텐츠를 재생하는지 원격으로 모니터링할 수 있고, 필드의 빈 화면이나 손상된 경험에 대한 반응성을 개선하며, 최종 사용자에게 손상된 경험을 표시할 위험을 줄일 수 있습니다.
자세한 내용은 [기본 재생 모니터링](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring)을 참조하십시오.

* **컨텐츠 지정 보고서 업데이트**

   이제 컨텐츠 지정 보고서가 최적화되었으며 사용자 경험이 향상되어 개선되었습니다. 다운로드 가능한 보고서에는 한 스프레드시트 탭과 다른 탭의 채널 및 자산과 같은 컨텐츠 공급자 정보에 위치, 표시 및 장치와 같은 향상된 플레이어 관련 엔티티가 표시됩니다.
자세한 내용은 [컨텐츠 지정 보고서](/help/user-guide/content-assignment-report.md)를 참조하십시오.

* **응용 표현물**

   응용 변환을 사용하여 장치는 고객이 정의한 규칙에 따라 장치에 대해 가장 적합한 변환을 자동으로 선택할 수 있습니다.

   이제 AEM Screens 개발자로서, 모든 컨텐츠 변형을 수동으로 만들지 않고도 자동으로 다운로드 및 재생되도록 장치별 자산 변환을 구성할 수 있습니다.

   또한 AEM Screens 컨텐츠 작성자는 이제 AEM Screens 프로젝트에서 적응형 표현물을 사용하고 대규모 네트워크에 대한 마이그레이션 전략을 적용할 수 있습니다.

* **V3 매니페스트 지원**

   이제 매니페스트 버전 v3에 대한 Dispatcher를 구성할 수 있습니다. 자세한 내용은 [매니페스트 버전에 대한 Dispatcher 구성 v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3)을 참조하십시오.
또한 사용자 지정 구성 요소를 v3 매니페스트의 일부로 사용하는 경우 [사용자 지정 핸들러용 템플릿](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)을 참조하십시오.


### 버그 수정 {#bug-fixes}

**플레이어 측**

* 자산을 변환으로 대체하여 파일 캐싱 오류가 해결되었습니다.

* 이제 플레이어에는 표현물 매핑이 있는 경우에만 자산 표현물이 표시됩니다.

* 이제 splunk 로그를 기준으로 slack 경고를 설정할 수 있습니다.

* 응답이 잘못된 JSON인 경우 다시 인증하도록 Ping이 개선되었습니다.

* 숫자 채널 이름/역할이 빈 화면으로 인해 발생했습니다.

* SmartSync를 통해 최적화된 변환을 다운로드합니다.

* 매핑을 변환 키 목록으로 변환했습니다.

* Windows 플레이어에서 `cmd.exe` 및 `reg.exe`에 대한 액세스가 제거되었습니다.

* 플레이어는 마지막으로 성공한 재생 이벤트를 보고해야 합니다.

* 플레이어는 재생 상태를 보고해야 합니다.

* `ALL` 캐시가 지워지면 플레이어가 자산을 다시 다운로드하지 않습니다.

* 이제 플레이어 관리자로 플레이어 이름을 선택할 수 있습니다.

* 디스플레이에서 채널 할당을 제거하면 플레이어에 반영되지 않습니다.

* 채널 업데이트를 다운로드하는 동안 플레이어가 다시 로드되면 플레이어에서 업데이트를 무시합니다.

* 이제 포함된 페이지 구성 요소가 터치 이벤트를 준수합니다.

* 이제 타이젠 플레이어의 원격 프로비저닝이 지원됩니다.

**서버 측**

* Target 비디오가 표시되지 않음
* 디스플레이 데이터를 시퀀스로 브로드캐스트하는 경합 조건입니다.

* 비디오가 포함된 채널에 대해 채널 미리 보기가 작동하지 않습니다.

* 분할 화면 채널에 대해 공백으로 표시된 미리 보기 모드

* 활성화된 응용 표현물과 함께 비디오 축소판이 공백으로 렌더링됩니다.

* 참조된 페이지가 게시되면 채널 매니페스트를 자동으로 업데이트합니다.

* 삭제된 장치는 이제 스크린 복제 큐를 차단하지 않습니다.

* 매니페스트에 타깃팅된 콘텐츠 또는 사이트 포함 페이지가 없습니다. 이 문제가 해결되었습니다.

* 이제 새 코어 이미지 구성 요소가 채널 매니페스트에 추가됩니다.

* 이제 SmartSync를 통해 최적화된 변환을 다운로드할 수 있습니다.

* 모든 자산에 대해 최적화된 렌디션을 재생합니다.

* 여러 콘텐츠 공급자 유형에 대한 지원이 추가되었습니다.

* 포함된 시퀀스 재생 전략이 중단되었으며 이제 수정되었습니다.

* html 항목에 대한 요청 매개 변수 `wcmmode`을 사용하여 오프라인 매니페스트를 사용하여 비활성화할 수 있습니다.

* 동적 포함된 시퀀스가 비어 있으면 화면이 비어 있는 경우가 있습니다.

* 이제 플레이어가 재생 상태를 보고합니다.

* 비디오가 `Tiny mode`에서 재생되고 장치에서 전체 화면 비디오로 재생되지 않았으며 문제가 해결되었습니다.

### 릴리스된 AEM Screens 플레이어 {#released-aem-screens-players}

다음 AEM Screens Players가 AEM 6.5 기능 팩 9용으로 출시되었습니다.

* ChromeOS
* Windows
* 타이젠
* Android
* Linux

#### AEM Screens Player 다운로드  {#aem-screens-player-downloads}

최신 AEM Screens 플레이어를 다운로드하고 버그 수정에 대해 자세히 알아보려면 **[AEM Screens Player 다운로드](https://download.macromedia.com/screens/index.html)**&#x200B;를 참조하십시오.
