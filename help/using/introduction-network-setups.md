---
title: 표준 네트워크 설정 소개
seo-title: 표준 네트워크 설정 소개
description: 표준 네트워크 설정에 대해 설명합니다.
seo-description: 표준 네트워크 설정에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: ae7da9c48188c3f7567d05d0e9a5a6b72383d539
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# 네트워크 트래픽 관리 {#managing-network-traffic}

네트워크 설치에는 다양한 구조가 있을 수 있습니다. 이 섹션에서는 환경에 배포된 네트워크 구조에 대한 개요를 제공합니다. 때때로 처음부터 구현되는 다양한 설정이 있습니다.

이 섹션에서는 프록시 서버에 대한 소개와 서로 다른 조직 내에서 설정되는 서로 다른 네트워크 구조를 소개합니다.

>[!NOTE]
>**AEM Screens 네트워크 요구 사항&#x200B;**>AEM Cloud Service과 직접 통신하는 AEM Screens에 따라 두 노드 간에 안정된 연결이 필요합니다. 방화벽은 상업용 인터넷 액세스에 대해 절대적으로 필수적이며, 고객이 방화벽 및 기타 IT-보안 관련 네트워크 구성 요소에서 열어야 하는 통신 포트를 파악해야 합니다.

## 프록시 서버 {#proxy-servers}

프록시 서버는 컴퓨터와 같은 끝점 장치와 사용자 또는 클라이언트가 서비스를 요청하는 다른 서버 사이의 중간 역할을 하는 컴퓨터에서 실행되는 전용 컴퓨터 또는 소프트웨어 시스템입니다. 프록시 서버는 방화벽 서버와 동일한 컴퓨터에 존재하거나 별도의 서버에 있을 수 있으며 이를 통해 방화벽을 통해 요청을 전달합니다.

프록시 서버의 이점은 모든 사용자에게 캐시 역할을 할 수 있다는 것입니다. 하나 이상의 인터넷 사이트가 자주 요청되는 경우 이러한 사이트가 프록시의 캐시에 있을 수 있으므로 사용자 응답 시간이 향상됩니다. 프록시는 상호 작용을 기록할 수도 있으며, 이는 문제 해결에 도움이 될 수 있습니다.

## 표준 네트워크 설정 이해 {#network-setups}

네트워크 설정을 구현하려면 강점과 배포 세부 사항이 있는 다음 시나리오를 참조해야 합니다.

다음 세 가지 주요 유형의 네트워크 설정이 있습니다.

1. [직접 인터넷 액세스](/help/using/direct-internet-access.md)
1. [직접 모바일 네트워크](/help/using/mobile-network-setup.md)
1. [모바일 데이터 라우터 및 활성 네트워크 구성 요소를 사용하는 모바일 네트워크](/help/using/mobile-network-setup-router.md)
1. [동봉된 회사 네트워크](/help/using/enclosed-corporate-network.md)

다음 표에서는 장점과 단점으로 다양한 유형의 네트워크 설정에 대해 설명합니다.

<table>
 <tbody>
  <tr>
   <td><strong>네트워크 설정</strong></td>
   <td><strong>장점</strong></td>
   <td><strong>단점</strong></td>
  </tr>
  <tr>
   <td><strong>직접 인터넷 액세스</strong></td>
   <td>SetUp<br>Good에 대한 쉽고 정밀한 선택중간 규모 또는 대규모 설치<br>전용 네트워크는 캡슐화할<br>수 있습니다. 몇 가지 실패<br>점<br>비교적 저렴한확장성</td>
   <td>적절한 인터넷 데이터 플랜 필수</td>
  </tr>
    <tr>
   <td><strong>직접 모바일 네트워크</strong></td>
   <td>설정<br>을 위한 간편하고 직설적인 옵션 중간 규모 또는 대규모 설치<br>시<br>는 탁월한 확장성EPS(Encapsulated Screens)
</td>
   <td>해당 인터넷 연결 필수</td>
  </tr>
    <tr>
<tr>
   <td><strong>모바일 데이터 라우터 및 활성 네트워크 구성 요소를 사용하는 모바일 네트워크</strong></td>
   <td>SetUp<br>Good에 대한 쉽고 직설적인 옵션 중간 규모 또는 대규모 설치에<br>적합한<br>전용 네트워크는 캡슐화할 수<br>있습니다. 몇 가지 장애<br>포인트비교적 저렴한확장성</br></td>
   <td>적절한 인터넷 데이터 플랜 필수</td>
  </tr>
    <tr>

<td><strong>동봉된 회사 네트워크</strong></td>
   <td>높은 유연성과 확장성<br>다양한 방어<br>캡슐화된 네트워크의<br>라인<br>으로 인한 높은 보안의 모니터링 및 유지용이성</td>
   <td>복잡하고 값비싼<br>네트워크 전문가 또는 시스템 통합자 권장</td>
  </tr>
  </tr>
 </tbody>
</table>


