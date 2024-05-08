---
title: 플레이어 장치에 대한 하드웨어 선택 지침
description: AEM Screens Player 장치에 대한 하드웨어 선택 지침에 대해 알아봅니다.
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 3%

---


# 플레이어 장치에 대한 하드웨어 선택 지침 {#hardware-selection}

다음 섹션에서는 AEM Screens 플레이어에 대한 하드웨어 선택 지침을 제공합니다.

## 중요 고려 사항 {#important-considerations}

* 항상 소스 ***커머셜*** 또는 ***산업*** PC 플레이어와 디스플레이 패널 또는 프로젝터 모두에 대해 구성 요소를 등급화합니다.

* 항상 디지털 간판 시장을 제공하는 공급업체와 협력하십시오.
* 주변 온도, 상대 습도 등 환경 요인을 항상 고려한다.
* 항상 전원 요구 사항 및 전원 조절 상태를 검토하십시오.
* 애플리케이션에 필요한 성능 요구 사항과 I/O 포트를 주의 깊게 검토하십시오.

## 하드웨어 구성 {#hardware-configurations}

다음 표에는 AEM Screens 프로젝트에 대한 일반적인 사용 사례와 함께 하드웨어 구성이 요약되어 있습니다.

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>플레이어 구성</strong></td>
   <td><strong>프로세서</strong></td>
   <td><strong>메모리</strong></td>
   <td><strong>스토리지 SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>디스플레이</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>일반적인 사용 사례</strong></td>
  </tr>
  <tr>
   <td>기본</td>
   <td>듀얼 코어, i3 또는 엔트리급 쿼드 코어 Intel® Atom 프로세서</td>
   <td><p>4GB 메모리</p> <p>2MB 캐시</p> </td>
   <td><p>*ChromeOS 32GB</p> <p>*Windows 128GB</p> </td>
   <td>온보드</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> 이더넷 / 무선,<br /> USB 2개</td>
   <td>
    <ul>
     <li>표준 전체 화면 루프<br /> </li>
     <li>시간대 지정</li>
    </ul> </td>
  </tr>
  <tr>
   <td>표준</td>
   <td>쿼드 코어, Intel® Core™ i5 프로세서</td>
   <td><p>8GB 메모리</p> <p>4MB 캐시</p> </td>
   <td>128GB</td>
   <td>온보드</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> 이더넷 / 무선,<br /> USB 2개</td>
   <td>
    <ul>
     <li>단일 소스 다이내믹 콘텐츠</li>
     <li>단순 대화형</li>
     <li>1-3 영역 레이아웃</li>
    </ul> </td>
  </tr>
  <tr>
   <td>고급</td>
   <td>쿼드 코어, 하이퍼스레딩, 인텔® 코어™ i7 프로세서</td>
   <td><p>16GB 메모리</p> <p>8MB 캐시</p> </td>
   <td>256GB</td>
   <td>전용 그래픽 GPU</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> 이더넷 / 무선,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4개 이상의 콘텐츠 영역, 동시 비디오 재생</li>
     <li>다중 페이지 인터랙티브</li>
     <li>다중 소스 데이터 트리거</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
