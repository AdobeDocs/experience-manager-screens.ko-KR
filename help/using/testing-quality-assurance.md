---
title: 테스트 및 품질 보증
seo-title: AEM Screens 테스트 및 품질 보증
description: 이 페이지에서는 AEM Screens 우수 사례 지침 테스트 및 품질 보증에 대해 설명합니다.
seo-description: 이 페이지에서는 AEM Screens 우수 사례 지침 테스트 및 품질 보증에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# 테스트 및 품질 보증 {#testing-quality}

>[!NOTE]
>이 활동의 일반적인 이해 관계자는 A/V 통합자입니다.

디지털 사이니지 네트워크의 실제 배포에 더 가까워짐에 따라 모든 하드웨어 구성 요소, 모든 소프트웨어 구성 요소 및 모든 네트워킹 구성 요소를 비롯한 네트워크의 모든 요소를 해결하는 테스트 및 QA 계획을 만들어야 합니다.
이 단계에서는 전체 테스트 시스템을 작성하고 완전히 테스트해야 합니다.

이전에 정의한 KPI를 모두 식별하고 해당 KPI에 대해 산출물을 측정하는 확인 목록을 만들어야 합니다.

>[!NOTE]
>
>이 단계는 나중에 장비와 함께 배송되고 나중에 참조하기 위해 현장에 보관될 수 있는 설치 및 사용 안내서를 만드는 도구로도 사용해야 합니다.

다음 요소를 고려해야 합니다.

## 1. 기계적 고려 사항 {#mechanical-considerations}

다음과 같은 기계적 고려 사항을 고려해야 합니다.

* 디스플레이 마운트
* 플레이어 장착
* 환기
* 주변 첨부 파일
* 케이블 관리
* 장치 네트워킹

## 2. 소프트웨어 고려 사항 {#software-considerations}

다음 소프트웨어 고려 사항을 권장합니다.

* 디바이스 등록
* 미디어 출판
* 재생
* 데이터베이스 종속성(이전에 정의됨)


## 3. 장치 관리 고려 사항 {#device-management-considerations}

AEM Screens에는 Screens 플레이어 애플리케이션 끝점을 관리할 수 있는 장치 컨트롤 센터 모듈이 포함되어 있습니다.

Screens 플레이어 응용 프로그램이 설치되고 AEM 인스턴스에 등록된 *플레이어* 하드웨어 장치를 참조합니다.
이 모듈에서는 다음을 수행할 수 있습니다.

1. 플레이어 응용 프로그램 오류 로그 모니터링
1. 원격 스크린샷 관리
1. 컨텐츠 다운로드 관리
1. 애플리케이션 다시 시작 문제 관리

***장치 컨트롤 센터***&#x200B;에 대한 자세한 내용은 **AEM Screens 사용자 안내서**&#x200B;에서 [장치 컨트롤 센터 문제 해결](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html)을 참조하십시오.

>[!CAUTION]
>
> 장치 제어 센터를 사용하여 다음을 수행할 수 없습니다.
> 1. 플레이어 애플리케이션의 새 버전 설치
> 1. 시스템 수준 리소스 모니터링
> 1. 시스템 수준 오류 문제 해결
> 1. 원격 데스크톱 개입 허용



>[!NOTE]
>
> Adobe은 전용 타사 장치 관리 플랫폼을 모든 배포에 사용하도록 권장합니다.

선택한 특정 플랫폼은 ***대상 운영 체제***, ***프로젝트 요구 사항*** 및 ***끝점 수***&#x200B;를 비롯한 여러 요소에 따라 달라집니다.

몇 가지 예는 다음과 같습니다.

* Google Chrome 장치 관리
* TeamViewer
* AirWatch
* 42Gears
* 독점 AV Integrator Middleware
