---
title: AEM Screens에서 Adobe Analytics 구성
seo-title: AEM Screens에서 Adobe Analytics 구성
description: '오프라인 Adobe Analytics를 사용하여 사용자 지정 이벤트를 시퀀스 지정하고 전송하는 방법에 대해 자세히 알아보려면 이 섹션을 따르십시오. '
seo-description: '오프라인 Adobe Analytics를 사용하여 사용자 지정 이벤트를 시퀀스 지정하고 전송하는 방법에 대해 자세히 알아보려면 이 섹션을 따르십시오. '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens에서 Adobe Analytics 구성 {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.4.2 기능 팩 2 및 AEM 6.3.3 기능 팩 4를 설치한 경우에만 사용할 수 있습니다.

>이러한 기능 팩을 이용하려면 Adobe 지원 센터에 문의하여 액세스 권한을 요청해야 합니다. 권한이 있으면 [패키지 공유]에서 다운로드할 수 있습니다.
>
이 섹션에서는 다음과 같은 주제를 다룹니다.

* **AEM Screens를 사용한 Adobe Analytics의 시퀀스**
* **오프라인 Adobe Analytics를 사용하여 사용자 지정 이벤트 보내기**

## AEM Screens를 사용한 Adobe Analytics의 시퀀스 {#sequencing-in-adobe-analytics-with-aem-screens}

순서 ***지정 프로세스는*** Adobe Analytics 서비스를 활성화하는 데이터 저장소 서비스로 시작됩니다. 채널 컨텐츠는 급여와 함께 Adobe Analytics 이벤트, 즉 데이터 테스트 캡처를 Windows I/O로 전송하고 이벤트 유지가 트리거됩니다. 이벤트는 인덱스 DB에 저장되고 객체 저장소에 추가로 저장됩니다. 관리자는 일정을 기반으로 객체 저장소에서 데이터를 잘라내고 청크 저장소에서 데이터를 추가로 전송합니다. 연결 시 최대 데이터 양을 전송합니다.

### 시퀀싱 다이어그램 {#sequencing-diagram}

다음 시퀀싱 다이어그램에서는 AEM Screens와 Adobe Analytics 통합에 대해 설명합니다.

![analytics_chunking](assets/analytics_chunking.png)

## 오프라인 Adobe Analytics를 사용하여 사용자 지정 이벤트 보내기 {#sending-custom-events-using-offline-adobe-analytics}

다음 표에는 이벤트에 대한 표준 데이터 모델이 요약되어 있습니다. Adobe Analytics로 전송된 모든 필드를 나열합니다.

<table>
 <tbody>
  <tr>
   <td><strong>섹션</strong></td> 
   <td><strong>속성 레이블</strong></td> 
   <td><strong>속성 이름/키</strong></td> 
   <td><strong>필수</strong></td> 
   <td><strong>데이터 유형</strong></td> 
   <td><strong>속성 유형</strong><br /> </td> 
   <td><strong>설명</strong></td> 
  </tr>
  <tr>
   <td><strong><em>코어/이벤트</em></strong></td> 
   <td>이벤트 GUID</td> 
   <td>event.guid</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td>UUID</td> 
   <td>이벤트 인스턴스를 식별하는 고유 ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 수집 날짜</td> 
   <td>event.coll_dts</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td>timestamp - UTC</td> 
   <td>컬렉션 날짜 시간</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 날짜 시간(시작)</td> 
   <td>event.dts_start</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td>timestamp - UTC</td> 
   <td>이벤트 시작 날짜 시간. 이 시간을 지정하지 않으면 이벤트 시간은 서버에서 받은 시간으로 가정합니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 날짜 시간(종료)</td> 
   <td>event.dts_end</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td>timestamp - UTC</td> 
   <td>이벤트 완료 날짜 시간</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>워크플로우</td> 
   <td>event.workflow</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>워크플로우 이름(스크린)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>기본 DMe 카테고리</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>기본 카테고리(데스크탑, 모바일, 웹, 프로세스, SDK, 서비스, 에코시스템) - 이벤트 유형 그룹 - <strong>Adobe Send Player</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>하위 카테고리</td> 
   <td>event.subcategory</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>하위 카테고리- 워크플로우 또는 화면 영역 등 (최근 파일, CC 파일, 모바일 제작 등)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트/작업 유형</td> 
   <td>event.type</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 유형(렌더링, 클릭, 핀치, 확대/축소) - 기본 사용자 작업</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>하위 유형</td> 
   <td>event.subtype</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 하위 유형(만들기, 업데이트, 삭제, 게시 등) - 사용자 작업에 대한 자세한 내용</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>오프라인</td> 
   <td>event.offline</td> 
   <td>옵션</td> 
   <td>부울</td> 
   <td> </td> 
   <td>작업이 오프라인/온라인(true/false)인 동안 이벤트가 생성되었습니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>사용자 에이전트</td> 
   <td>event.user_agent</td> 
   <td>권장(웹 속성)</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>사용자 에이전트</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>언어/로케일</td> 
   <td>event.language</td> 
   <td>권장</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>사용자 로케일은 RFC 3066의 언어 태그 지정 규칙(예: en-US, fr-FR 또는 es-ES)을 기반으로 하는 문자열입니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>장치 GUID</td> 
   <td>event.device_guid</td> 
   <td>옵션</td> 
   <td>문자열<br /> </td> 
   <td>UUID</td> 
   <td>장치 GUID(예: 시스템 ID 또는 IP 주소 + 서브넷 마스크 + 네트워크 ID + 사용자 에이전트 해시)를 식별합니다. 여기서 등록 시 생성된 플레이어의 사용자 이름을 전송합니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>횟수</td> 
   <td>event.count</td> 
   <td>옵션</td> 
   <td>개수</td> 
   <td> </td> 
   <td>이벤트가 발생한 횟수 - 비디오 지속 시간을 보냅니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>값</td> 
   <td>event.value</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 값(예: 설정 설정 켜기/끄기)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>페이지 이름</td> 
   <td>event.pagename</td> 
   <td>AA에 필요</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>사용자 지정 페이지 이름에 대한 Adobe Analytics 지원</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>웹 속성 또는 모바일 스키마의 URL - 정규화된 URL을 포함해야 합니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>오류 코드</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>문자열</td> 
   <td> </td> 
   <td>실패 코드</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>오류 유형</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>문자열</td> 
   <td> </td> 
   <td>실패 유형</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>오류 설명</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>문자열</td> 
   <td> </td> 
   <td>실패 설명<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>출처/출처 제품</em></strong></td> 
   <td>이름</td> 
   <td>source.name</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>앱 이름(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>버전</td> 
   <td>source.version</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>펌웨어 버전</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>플랫폼</td> 
   <td>source.platform</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>장치</td> 
   <td>source.device</td> 
   <td>필수 w/execution</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>플레이어 이름</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>OS 버전</td> 
   <td>source.os_version</td> 
   <td>필수 w/execution</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>O/S 버전</td> 
  </tr>
  <tr>
   <td><strong><em>컨텐츠</em></strong></td> 
   <td>작업</td> 
   <td>content.action</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>실제로 재생된 표현물을 포함한 자산의 URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>MIME 유형</td> 
   <td>content.mimetype</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>콘텐츠의 MIME 유형</td> 
  </tr>
  <tr>
   <td><strong><em>트랜잭션</em></strong></td> 
   <td>거래 번호</td> 
   <td>trn.number</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td>UUID</td> 
   <td>UUID v4를 일반적으로 준수하는 고유 ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>제품 설명</td> 
   <td>trn.product</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>자산의 URL(변환 제외)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>수량</td> 
   <td>trn.quantity</td> 
   <td>required</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>재생 시간</td> 
  </tr>
 </tbody>
</table>

