---
title: 테스트 및 품질 보증
description: 모범 사례 안내서에서 AEM Screens에 대한 테스트 및 품질 보증에 대해 알아봅니다.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 테스트 및 품질 보증 {#testing-quality}

>[!NOTE]
>이 활동의 일반적인 이해 당사자는 오디오-비디오 통합자입니다.

디지털 사이니지 네트워크의 배포가 가까워지면 모든 하드웨어 구성 요소, 모든 소프트웨어 구성 요소, 모든 네트워킹 구성 요소를 포함한 네트워크의 모든 요소를 해결하는 테스트 및 QA 계획을 만듭니다.
이 단계에서는 전체 테스트 시스템을 구축하고 완전히 테스트해야 합니다.

이전에 정의한 모든 KPI를 식별하고 이에 대해 결과물을 측정하는 체크리스트를 작성해야 합니다.

>[!NOTE]
>
>이 단계는 설치 및 사용 안내서를 작성하는 도구로도 사용해야 합니다. 두 제품 모두 나중에 장비와 함께 선적하여 나중에 참조할 수 있도록 사이트에 보관할 수 있습니다.

다음 요소를 고려해야 합니다.

## 1. 기계적 고려 사항 {#mechanical-considerations}

다음과 같은 기계적 고려 사항을 권장합니다.

* 디스플레이 장착
* 플레이어 장착
* 환기
* 주변장치 부착물
* 케이블 관리
* 장치 네트워킹

## 2. 소프트웨어 고려 사항 {#software-considerations}

다음 소프트웨어 고려 사항을 권장합니다.

* 장치 등록
* 미디어 게시
* 재생
* 데이터베이스 종속성(이전에 정의됨)


## 3. 장치 관리 고려 사항 {#device-management-considerations}

AEM Screens에는 Screens 플레이어 애플리케이션 엔드포인트를 관리할 수 있는 Device Control Center 모듈이 포함되어 있습니다.

Screens 플레이어 응용 프로그램이 설치되어 있고 AEM 인스턴스에 등록된 *player* 하드웨어 장치를 참조합니다.
이 모듈에서는 다음 작업을 수행할 수 있습니다.

1. 플레이어 애플리케이션 오류 로그 모니터링
1. 원격 스크린샷 관리
1. 콘텐츠 다운로드 관리
1. 응용 프로그램 다시 시작 문제 관리

***장치 제어 센터***&#x200B;에 대한 자세한 내용은 **AEM Screens 사용 안내서**&#x200B;의 [장치 제어 센터 문제 해결](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens)을 참조하세요.

>[!CAUTION]
>
>Device Control Center 를 사용하여 다음을 수행하지 마십시오.
>
>* 플레이어 애플리케이션의 새 버전 설치
>* 시스템 수준 리소스 모니터링
>* 시스템 수준 오류 문제 해결
>* 원격 데스크톱 작업 허용


>[!NOTE]
>
> Adobe은 모든 배포에 전용 타사 장치 관리 플랫폼을 사용할 것을 권장합니다.

선택한 특정 플랫폼은 ***대상 운영 체제***, ***프로젝트 요구 사항*** 및 ***끝점 수***&#x200B;를 포함한 여러 요소에 따라 다릅니다.

몇 가지 예는 다음과 같습니다.

* Google Chrome 장치 관리
* TeamViewer
* 에어워치
* `42Gears`
* 독점 오디오-비디오 통합기 미들웨어
