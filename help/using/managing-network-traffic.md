---
title: 네트워크 트래픽 관리
description: 이 페이지에서는 표준 네트워크 설정과 네트워크 트래픽을 관리하는 방법에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: 173ce977549ed64e3750bb751a8fe1b27e277aa2
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# 네트워크 트래픽 관리 {#managing-network-traffic}

네트워크 설치에는 다양한 구조가 있을 수 있습니다. 이 섹션에서는 조직 내에서 이루어지는 가장 일반적인 네트워크 설정 및 일반화된 접근 방식에 대해 설명합니다.

이 안내서에서는 프록시 서버에 대한 도입 후 서로 다른 조직 내에서 설정되는 다양한 네트워크 구조를 소개합니다.

>[!NOTE]
>
>**AEM Screens 네트워크 요구 사항**
>
>AEM Screens은 AEM과 Cloud Service으로 직접 통신하므로 두 노드 간에 안정된 연결을 설정해야 합니다. 방화벽은 상업적인 인터넷 액세스에 있어 절대적으로 필수적이며, 고객인 경우 이러한 방화벽 및 기타 IT-보안 관련 네트워크 구성 요소에서 열어야 하는 통신 포트를 이해해야 합니다.

## 프록시 서버 개요 {#proxy-servers}

인터넷 연결은 프록시 서버의 사용에 의존합니다. 프록시 서버는 컴퓨터와 같은 끝점 장치와 사용자 또는 클라이언트가 서비스를 요청하는 다른 서버 사이의 중간 역할을 하는 컴퓨터에서 실행되는 전용 컴퓨터 또는 소프트웨어 시스템입니다. 프록시 서버는 방화벽 서버와 동일한 컴퓨터에 존재하거나 별도의 서버에 존재할 수 있으며 이러한 서버는 방화벽을 통해 요청을 전달합니다.

프록시 서버의 이점은 해당 캐시가 모든 사용자에게 제공된다는 것입니다. 하나 이상의 인터넷 사이트가 자주 요청되는 경우 이러한 사이트가 프록시의 캐시에 있을 수 있으며, 이로 인해 사용자 응답 시간이 더욱 향상됩니다. 프록시는 상호 작용을 기록할 수도 있으며, 이는 문제 해결에 사용할 수 있습니다.

프록시 서버가 인터넷 리소스(예: 웹 페이지 또는 AEM 게시자에 연결하는 동안)에 대한 요청을 받으면 이전에 호출된 url의 로컬 캐시를 검색합니다. 페이지를 찾으면, 요청을 인터넷에 전달하지 않고 사용자에게 돌아갑니다. 페이지가 캐시에 없으면 프록시 서버(클라이언트 역할)가 사용자를 대신하며 인터넷의 서버에서 페이지를 요청합니다. 컨텐츠가 반환되면 프록시 서버는 이 컨텐츠를 원래 요청과 연관시키고 사용자에게 전달합니다.

## 표준 네트워크 설정 이해 {#network-setups}

네트워크 설정을 구현하려면, 다음 시나리오를 자신의 장점 및 배포 세부 사항과 함께 참조해야 합니다.

본 가이드에서는 조직 내의 4가지 서로 다른 네트워크 설정을 다룹니다.

* **[직접 인터넷 네트워크(유선/무선)](/help/using/direct-internet-network.md)**
* **[직접 모바일 네트워크](/help/using/mobile-network.md)**
* **[모바일 데이터 라우터 및 활성 네트워크 구성 요소를 사용하는 모바일 네트워크](/help/using/mobile-network-router.md)**
* **[동봉된 회사 네트워크(유선/무선)](/help/using/enclosed-corporate-network.md)**

다음 표에서는 장점과 단점으로 다양한 유형의 네트워크 설정에 대해 설명합니다.

| 네트워크 설정 | 장점 | 단점 |
|--- |--- |--- |
| **직접 인터넷 네트워크(유선/무선)** | 쉽고<br>직설적인 설정UpGood중간 규모 또는 대규모<br>설치전용 네트워크는<br>캡슐화된<br>몇<br>가지장애요비교적 저렴한우수한 확장성 | 필수 인터넷 데이터 플랜 |
| **직접 모바일 네트워크** | 간편한<br>설정Up중간 규모 또는 대규모 설치 시<br>좋은 선택우수한<br>확장성 캡슐화된 스크린 | 필수 인터넷 연결 |
| **모바일 데이터 라우터 및 활성 네트워크 구성 요소를 사용하는 모바일 네트워크** | 간편한<br>설정Good choice for Mid-size or Larger Installations<br>전용 네트워크는 캡슐화할 수<br>있음몇 가지<br>실패 시점과 상대적으로 저렴한<br>확장성 | 필수 인터넷 데이터 플랜 |
| **동봉된 회사 네트워크(유선/무선)** | 높은 유연성과<br>확장성 다양한<br>방어<br>의 네트워크로 인한 높은 보안EPS<br>로EPS(Encapsulated Network)간편하게 모니터링 및유지 관리안정성 | 네트워크<br>전문가 또는 시스템 통합자에 대한 복잡하고 값비싼 권장 |