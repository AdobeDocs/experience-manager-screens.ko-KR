---
title: "2부: 프로젝트 범위 지정 시 고려 사항"
seo-title: "Part 2: Considerations as Projects are Scoped"
description: 이 튜토리얼을 따라 콘텐츠 전략, I/O 계층, 자산 유형, 대상 세분화, 시간대, 비즈니스 운영 요구 사항 및 사이트 준비 고려 사항에 대해 알아보십시오.
seo-description: Follow this tutorial to learn about the content strategy, I/O layers, asset types, audience segmentation, day parts, business operations requirements, and site readiness considerations.
uuid: 96359202-8f55-4330-97c5-fc8f8c916a8d
contentOwner: jsyal
content-type: reference
topic-tags: digital-signage-networks-basics
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 10b81628-46db-4122-bf9e-96f41f080055
docset: aem65
feature: Overview
role: User, Data Architect
level: Beginner
exl-id: 7814ee96-9220-45b6-b56e-b48a9da9a319
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# 2부: 프로젝트 범위 지정 시 고려 사항 {#part-considerations-as-projects-are-scoped}

이 페이지에서는 팀원이 성공적인 AEM Screens 배포 개발을 위한 사전 영업 측면을 더 잘 이해할 수 있도록 설계된 5부로 구성된 시리즈 중 2부를 소개합니다.

## 개요 {#overview}

다음 튜토리얼에서는 프로젝트를 평가하고 적절한 설계를 준비하기 위해 관련자 입력과 함께 프로젝트 검색 중에 식별해야 하는 요소를 다룹니다.

성공적인 배포에 필요한 디지털 서명 프로그램의 주요 구성 요소는 다음과 같습니다.

* 컨텐츠 전략
* 비즈니스 운영 요구 사항
* IT 및 네트워크 환경 검색
* AV 요구 사항
* 장비 사양
* 사이트 준비

>[!NOTE]
>
>애플리케이션이 소프트웨어, 하드웨어 및 연결 리소스를 활용하여 의도한 가치를 성공적으로 제공할 수 있는 방법을 고려하는 컨텐츠 전략을 정의하는 것이 중요합니다.

## 디지털 신호체계의 프로젝트 고려 사항 요약  {#summary-of-project-considerations-in-a-digital-signage}

컨텐츠 전략을 개발할 때는 I/O 계층, 자산 유형, 대상 세분화 및 일정 요구 사항을 비롯한 몇 가지 고려 사항이 있습니다.

### I/O 레이어 {#i-o-layers}

I/O는 대상자 근접 감지를 기반으로 컨텐츠의 조건부 재생을 유도합니다. 예를 들어, 센서가 근접을 감지하면 컨텐츠 재생이 &#39;끌어오기&#39; 또는 패시브 컨텐츠에서 &#39;참여&#39; 또는 대화형 재생으로 변경될 수 있습니다. 이는 인구 통계를 기반으로 콘텐츠를 제공하는 것이 필요한 응용 프로그램에서 특히 유용합니다.

### 컨텐츠 자산 유형 {#content-asset-types}

다음 사항은 콘텐츠 자산과 관련된 최종 클라이언트의 의도를 이해하는 것으로 간주됩니다.

* 컨텐츠가 인쇄, TV 또는 웹 캠페인에서 용도 변경되었습니까?
* 콘텐츠가 정적 이미지로 구성되는지 아니면 동적으로 제공되는 구성 요소를 포함하는 템플릿으로 구성되는지 여부
* 애니메이션이 비디오나 HTML 프로그램으로 재생됩니까?
* 콘텐츠 구독 서비스, 소셜 미디어 또는 RSS 집계 서비스 또는 API 호출에서 서드파티 통합이 있습니까?
* 이미지 해상도 요구 사항은 무엇입니까?
* Screens 표준 16:9 종횡비입니까? 아니면 사용자 지정입니까? 세로 또는 가로?
* 다중 화면 비디오 월이 필요합니까? 필요한 경우 구성은 무엇입니까?
* 운영 또는 광고 매출에 연결된 컨텐츠를 다운타임을 방지하기 위해 장애 조치 전략이 필요합니까?

### 대상자 세분화, 방송 시간대 {#audience-segmentation-day-parts}

시간대 전략을 열거하면 최종 클라이언트가 콘텐츠를 세그먼트화하고 적절한 시간에 적절한 대상자에게 메시지를 타겟팅할 수 있습니다. 많은 콘텐츠 기여자가 재생 목록의 전체를 구성하는 광고 또는 소매 네트워크에 특히 효과적입니다.

### 비즈니스 운영 요구 사항 {#business-operations-requirements}

비즈니스 운영은 콘텐츠 전략 대화에서 정의하는 것도 중요합니다. 최종 클라이언트의 지원 요구 사항을 공식화하면 구축 후 기대치를 관리할 수 있어 지원 노력이 적절히 측정됩니다.

### A/V 요구 사항 {#a-v-requirements}

장비 서비스를 위한 디바이스 액세스를 둘러싼 고려 사항과 마찬가지로 장착 시나리오에도 정의가 필요합니다. 이는 초기 설치 인력 및 장비 권장사항뿐만 아니라 지속적인 서비스 및 지원 요구 사항도 결정합니다.

### 사이트 준비 {#site-readiness}

Pre-Sales 프로세스의 마지막 단계는 Site Readiness 를 결정하는 것입니다. 이는 사이트, 프로젝트 및 진행 상황 세부 정보를 캡처하는 사이트 조사를 통해 촉진될 수 있습니다. Site Readiness 는 기본적으로 설치 전 위치의 현재 상태를 캡처하며, 엔지니어가 도착하기 전에 고객이 준비하거나 해결할 계획을 세우는 모든 항목을 호출합니다. 일반적으로, 이것은 전력, 데이터, 가구 제거 및 먼지 제거와 같은 항목들을 포함한다.

## 2부: 프로젝트 범위가 지정될 때의 고려 사항에 대한 비디오 튜토리얼 {#part-video-tutorial-on-considerations-as-projects-are-scoped}

아래 튜토리얼을 따라 콘텐츠 전략, I/O 계층, 자산 유형, 대상 세분화, 시간대, 비즈니스 운영 요구 사항 및 사이트 준비 고려 사항에 대해 알아보십시오.

### 프로젝트 범위 지정 시 고려 사항

>[!VIDEO](https://video.tv.adobe.com/v/28380)

*콘텐츠 전략, I/O 레이어, 에셋 유형, 대상 세분화, 시간대, 비즈니스 운영 요구 사항 및 사이트 준비 고려 사항에 대해 알아봅니다.*

## 다음 단계 {#the-next-step}

프로젝트를 평가하고 적절한 설계를 준비하기 위해 관련자의 입력과 함께 프로젝트 검색 중에 식별된 요소를 이해하면 프로젝트 주기, 하드웨어 테스트를 둘러싼 작업, 개념 증명, 파일럿 및 롤아웃과 같은 전체 프로젝트 계획과 관련된 주요 용어를 학습해야 합니다.

다음으로 이동 **[테스트, POC, 파일럿 및 롤아웃](testing-pocs-pilots-rollouts.md)** 을 참조하십시오.
