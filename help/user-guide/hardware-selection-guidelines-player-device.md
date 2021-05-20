---
title: 플레이어 장치에 대한 하드웨어 선택 지침
description: 플레이어 장치에 대한 하드웨어 선택 지침
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 2%

---


# 플레이어 장치에 대한 하드웨어 선택 지침 {#hardware-selection}

다음 섹션에서는 AEM Screens 플레이어에 대한 하드웨어 선택 지침을 제공합니다.

## 중요 고려 사항 {#important-considerations}

* 항상 PC 플레이어와 디스플레이 패널 또는 프로젝터에 대한 ***상용*** 또는 ***산업*** 등급 구성 요소를 공급합니다.

* 디지털 간판 시장을 제공하는 공급업체는 항상 적극적으로 참여하십시오.
* 항상 주위 온도 및 상대 습도와 같은 환경 요소를 고려하십시오.
* 항상 전원 요구 사항 및 전원 상태를 검토합니다.
* 애플리케이션에 필요한 성능 요구 사항 및 입출력 포트를 신중하게 검토합니다.

## 하드웨어 구성 {#hardware-configurations}

다음 표에서는 AEM Screens 프로젝트의 일반적인 사용 사례와 함께 하드웨어 구성을 요약합니다.

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>플레이어 구성</strong></td>
   <td><strong>프로세서</strong></td>
   <td><strong>메모리</strong></td>
   <td><strong>스토리지 SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>표시</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>일반적인 사용 사례</strong></td>
  </tr>
  <tr>
   <td>기본</td>
   <td>듀얼 코어, i3 또는 초급 쿼드 코어 인텔® 아톰 프로세서</td>
   <td><p>4GB 메모리</p> <p>2MB 캐시</p> </td>
   <td><p>・ ChromeOS 32GB</p> <p>・ Windows 128GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> 이더넷/무선,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>표준 전체 화면 루프<br /> </li>
     <li>시간대 지정</li>
    </ul> </td>
  </tr>
  <tr>
   <td>표준</td>
   <td>쿼드 코어, 인텔® 코어 i5 프로세서</td>
   <td><p>8GB 메모리</p> <p>4MB 캐시</p> </td>
   <td>128GBB</td>
   <td>OnBoard</td>
   <td>3840x2160(4K)</td>
   <td>DVI, HDMI<br /> 이더넷/무선,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>단일 소스 다이내믹 컨텐츠</li>
     <li>간단한 대화형</li>
     <li>1-3 영역 레이아웃</li>
    </ul> </td>
  </tr>
  <tr>
   <td>고급</td>
   <td>하이퍼스레딩을 지원하는 쿼드 코어, 인텔® 코어 i7 프로세서</td>
   <td><p>16GB 메모리</p> <p>8MB 캐시</p> </td>
   <td>256GB</td>
   <td>전용 그래픽 GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI, HDMI<br /> 이더넷/무선,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4개 이상의 컨텐츠 영역, 동시 비디오 재생</li>
     <li>다중 페이지 대화형</li>
     <li>다중 소스 데이터 트리거</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
