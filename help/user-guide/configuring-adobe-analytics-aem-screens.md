---
title: AEM Screens을 사용하여 Adobe Analytics 구성
seo-title: Configuring Adobe Analytics with AEM Screens
description: 오프라인 Adobe Analytics을 사용하여 사용자 지정 이벤트를 시퀀싱하고 전송하는 방법에 대한 자세한 내용은 이 섹션을 따르십시오
seo-description: Follow this section to learn more about sequencing and sending custom events using Offline Adobe Analytics
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 9%

---

# AEM Screens을 사용하여 Adobe Analytics 구성 {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>이 AEM Screens 기능은 AEM 6.4.2 기능 팩 2 및 AEM 6.3.3 기능 팩 4를 설치한 경우에만 사용할 수 있습니다.
>
>이러한 기능 팩 중 하나에 액세스하려면 Adobe 지원 센터에 문의하여 액세스를 요청해야 합니다. 권한이 있으면 패키지 공유에서 다운로드할 수 있습니다.

이 섹션에서는 다음 주제를 다룹니다.

* **AEM Screens을 사용한 Adobe Analytics의 시퀀싱**
* **오프라인 Adobe Analytics을 사용하여 사용자 지정 이벤트 보내기**

## AEM Screens을 사용한 Adobe Analytics의 시퀀싱 {#sequencing-in-adobe-analytics-with-aem-screens}

다음 ***순서 결정 과정*** 는 Adobe Analytics 서비스를 활성화하는 데이터 스토리지 서비스로 시작합니다. 채널 콘텐츠는 급여가 포함된 Adobe Analytics 이벤트를 전송합니다. 즉, 데이터 테스트 캡처를 Windows I/O로 전송하고 이벤트가 트리거됩니다. 이벤트는 색인 DB에 저장되고 객체 저장소에 추가로 저장됩니다. 관리자가 설정한 일정에 따라 오브젝트 저장소에서 데이터를 잘라내고 청크 저장소에 추가로 전송합니다. 연결되면 최대 데이터 양을 전송하려고 합니다.

### 시퀀싱 다이어그램 {#sequencing-diagram}

다음 순서 다이어그램은 AEM Screens과 Adobe Analytics 통합에 대해 설명합니다.

![analytics_청킹](assets/analytics_chunking.png)

## 오프라인 Adobe Analytics을 사용하여 사용자 지정 이벤트 보내기 {#sending-custom-events-using-offline-adobe-analytics}

다음 표에는 이벤트에 대한 표준 데이터 모델이 요약되어 있습니다. 이 목록에는 Adobe Analytics에 전송된 모든 필드가 나열됩니다.

<table>
 <tbody>
  <tr>
   <td><strong>섹션</strong></td> 
   <td><strong>속성 레이블</strong></td> 
   <td><strong>속성 이름/키</strong></td> 
   <td><strong>필수</strong></td> 
   <td><strong>데이터 형식</strong></td> 
   <td><strong>속성 유형</strong><br /> </td> 
   <td><strong>설명</strong></td> 
  </tr>
  <tr>
   <td><strong><em>코어/이벤트</em></strong></td> 
   <td>이벤트 GUID</td> 
   <td>event.guid</td> 
   <td>추천</td> 
   <td>문자열</td> 
   <td>UUID</td> 
   <td>이벤트의 인스턴스를 식별하는 고유 ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 컬렉션 날짜/시간</td> 
   <td>event.coll_dts</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td>타임스탬프 - UTC</td> 
   <td>컬렉션 날짜 시간</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 날짜 시간(시작)</td> 
   <td>event.dts_start</td> 
   <td>추천</td> 
   <td>문자열</td> 
   <td>타임스탬프 - UTC</td> 
   <td>이벤트 시작 날짜 시간 을 지정하지 않으면 이벤트 시간은 서버가 수신한 시간으로 간주됩니다</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트 날짜 시간(종료)</td> 
   <td>event.dts_end</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td>타임스탬프 - UTC</td> 
   <td>이벤트 완료 날짜 시간</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>워크플로</td> 
   <td>event.workflow</td> 
   <td>추천</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>워크플로 이름(화면)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>기본 DMe 범주</td> 
   <td>event.category</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>주요 카테고리(데스크탑, 모바일, 웹, 프로세스, SDK, 서비스, 에코시스템) - 이벤트 유형 그룹화 - <strong>플레이어를 보냅니다.</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>하위 범주</td> 
   <td>event.subcategory</td> 
   <td>추천</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>하위 카테고리 - 워크플로 또는 화면 영역 등의 섹션. (최근 파일, CC 파일, 모바일 생성 등)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>이벤트/작업 유형</td> 
   <td>event.type</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 유형(렌더링, 클릭, 핀치, 확대/축소) - 기본 사용자 작업</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>하위 유형</td> 
   <td>event.subtype</td> 
   <td>추천</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 하위 유형(만들기, 업데이트, 삭제, 게시 등) - 사용자 작업에 대한 추가 세부 정보</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>오프라인</td> 
   <td>event.offline</td> 
   <td>옵션</td> 
   <td>부울</td> 
   <td> </td> 
   <td>작업이 오프라인/온라인 상태인 동안 이벤트가 생성되었습니다(true/false).</td> 
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
   <td>언어/로캘</td> 
   <td>event.language</td> 
   <td>추천</td> 
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
   <td>장치 GUID(예: 컴퓨터 ID 또는 IP 주소 + 서브넷 마스크 + 네트워크 ID + 사용자 에이전트 해시) 식별 - 여기서는 등록 시 생성된 플레이어의 사용자 이름을 전송합니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>횟수</td> 
   <td>event.count</td> 
   <td>옵션</td> 
   <td>개수</td> 
   <td> </td> 
   <td>이벤트 발생 횟수 - 여기서는 비디오 지속 시간을 보냅니다.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>값</td> 
   <td>event.value</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>이벤트 값(예: 설정 on/off)</td> 
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
   <td><strong><em>소스/원본 제품</em></strong></td> 
   <td>이름</td> 
   <td>source.name</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>앱 이름(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>버전</td> 
   <td>source.version</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>펌웨어 버전</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>장치</td> 
   <td>source.device</td> 
   <td>예외가 없는 필수 항목</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>플레이어 이름</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>OS 버전</td> 
   <td>source.os_version</td> 
   <td>예외가 없는 필수 항목</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>O/S 버전</td> 
  </tr>
  <tr>
   <td><strong><em>콘텐츠</em></strong></td> 
   <td>작업</td> 
   <td>content.action</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>실제로 재생된 렌디션이 포함된 에셋의 URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Mime 유형</td> 
   <td>content.mimetype</td> 
   <td>옵션</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>콘텐츠의 MIME 유형</td> 
  </tr>
  <tr>
   <td><strong><em>거래</em></strong></td> 
   <td>거래 번호</td> 
   <td>trn.number</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td>UUID</td> 
   <td>UUID v4를 준수하는 것이 좋은 고유 ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>제품 설명</td> 
   <td>trn.product</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>에셋의 URL(렌디션 제외)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>수량</td> 
   <td>trn.quantity</td> 
   <td>필수</td> 
   <td>문자열</td> 
   <td> </td> 
   <td>재생 기간</td> 
  </tr>
 </tbody>
</table>
