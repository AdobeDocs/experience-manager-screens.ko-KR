---
title: 플레이어 장치에 대한 하드웨어 선택 지침
description: 플레이어 장치에 대한 하드웨어 선택 지침
translation-type: tm+mt
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 2%

---


# 플레이어 장치 {#hardware-selection}에 대한 하드웨어 선택 지침

다음 섹션에서는 AEM Screens 플레이어에 대한 하드웨어 선택 지침을 제공합니다.

## 중요 고려 사항 {#important-considerations}

* 항상 PC 플레이어 및 디스플레이 패널 또는 프로젝터 모두에 대해 상업용&#x200B;***또는***&#x200B;산업 분야&#x200B;***등급 구성 요소를 소싱하십시오.***

* 디지털 사이니지 시장을 제공하는 벤더와 항상 상호 작용합니다.
* 항상 주위 온도 및 상대 습도와 같은 환경 요인을 고려하십시오.
* 전원 요구 사항과 전원 조절 기능을 항상 검토할 수 있습니다.
* 애플리케이션에 필요한 성능 요구 사항과 입출력 포트를 신중하게 검토하십시오.

## 하드웨어 구성 {#hardware-configurations}

다음 표는 AEM Screens 프로젝트에 대한 일반적인 사용 사례와 함께 하드웨어 구성을 요약해 놓은 것입니다.

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
   <td>듀얼 코어, i3 또는 초급 쿼드 코어 Intel® Atom 프로세서</td>
   <td><p>4GB 메모리</p> <p>2MB의 캐시</p> </td>
   <td><p>・ ChromeOS 32GB</p> <p>・ Windows 128GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> 이더넷/무선,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>표준 전체 화면 반복<br /> </li>
     <li>하루 분할</li>
    </ul> </td>
  </tr>
  <tr>
   <td>표준</td>
   <td>쿼드 코어, Intel® Core i5 프로세서</td>
   <td><p>8GB 메모리</p> <p>4MB의 캐시</p> </td>
   <td>128GB</td>
   <td>OnBoard</td>
   <td>3840x2160(4K)</td>
   <td>DVI, HDMI<br /> 이더넷/무선,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>단일 소스 동적 컨텐츠</li>
     <li>간단한 인터랙티브</li>
     <li>1-3 영역 레이아웃</li>
    </ul> </td>
  </tr>
  <tr>
   <td>고급</td>
   <td>하이퍼스레딩(hyperthreading) 기술이 적용된 쿼드 코어, Intel® Core i7 프로세서</td>
   <td><p>16GB 메모리</p> <p>8MB의 캐시</p> </td>
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
