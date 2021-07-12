---
title: Security 검사 목록
seo-title: Security 검사 목록
description: 이 페이지에서는 질문 및 고려 사항 검사 목록과 함께 주요 보안 영역에 대해 설명합니다.
seo-description: 이 페이지에서는 Security 검사 목록에 대해 설명합니다
feature: 화면 관리
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 1%

---

# AEM Screens Security 검사 목록  {#security-checklist}

AEM Screens Security 검사 목록 페이지에서는 질문 및 고려 사항 체크리스트가 포함된 주요 보안 영역에 대해 설명합니다.

## 검사 목록 테이블 {#checklist-table}

| **보안 영역** | **확인 목록** | **예/아니요/NA** |
|---|---|---|
| **AEM 및 Screens 소프트웨어 업데이트** | ***a.*** *최신 Adobe Experience Manager(AEM) 서비스 팩이 적용되었습니까?* <br>***b.***  *최신 AEM Screens 기능 팩이 적용되었습니까?* <br>***c.*** *AEM Screens Player  [다운로드에서 사용 가능한 최신 AEM Screens Player 소프트웨어를 사용하고 있습니까](https://download.macromedia.com/screens/)?* |
| **물리적 보안** | ***a.*** *불필요한 포트를 모두 비활성화했습니까?* <br>***b.***  *케이블 연결 및 하드웨어를 확보했습니까?* <br>***c.*** *해당하는 경우 컨테이너를 사용하고 있습니까?* |
| **네트워크 보안** | ***a.*** *서명 장치에 격리된 서브넷을 사용하고 있습니까?* <br>***b.***  *격리된 서브넷에서 AEM, Adobe Analytics 또는 기타 필수 서비스를 포함한 필요한 종단점에 대한 액세스를 허용합니까?* <br>***c.*** *엔터프라이즈 모범 사례를 사용하여 Wi-Fi를 확보했습니까?* <br>***d.*** *동기화된 재생을 사용하는 경우 마스터 장치에서만 WebSocket에 대해 TCP 24503을 허용하시겠습니까?* <br>***e.*** *인증된 장치만 작성자에 대한 등록 서비스에 액세스할 수 있도록 플레이어 장치의 IP 주소 범위를 차단하지 않았습니까?* |
| **운영 체제 보안** | ***a.*** *최신 버전의 운영 체제로 업그레이드하여 필요한 모든 보안 패치를 적용했습니까?* <br>***b.*** *불필요한 서비스를 모두 비활성화하고 불필요한 응용 프로그램을 제거했습니까?* <br>***c. 엔터프라이즈*** *정책을 적용하기 위해 장치를 장치 관리에 등록했습니까?* <br>***d.*** *장치를 단일 애플리케이션(플레이어) 키오스크로 잠갔습니까?* <br>***e.*** *시간에 따라 OS 보안 업데이트를 설치할 수 있는 SOP(표준 운영 절차)가 있습니까?*<br>***f.*** *맬웨어 방지 소프트웨어, 관리자가 아닌 사용자와 같이 사용 중인 운영 체제에 대한 보안 모범 사례를 따랐습니까?* |
| **응용 프로그램 보안** | ***a.*** *프로덕션에 관리자 UI, 채널 전환기 및 Activity UI를 비활성화했습니까?* <br>***b.*** *프로덕션에 대한 로그 수준을 최소화했습니까?* <br>***c. AEM*** *에 연결하는 데 https를 사용하고 있습니까?* <br>***d.*** *CA 서명 인증서 또는 엔터프라이즈 PKI를 사용하고 있습니까? (자체 서명된 인증서 아님)*<br>***e.*** *SSL v3이 아닌 TLS를 사용하고 있습니까?*<br>***f.*** *등록할 때 장치 및 AEM에서 등록 토큰의 유효성을 검사하고 있습니까?*<br> ***g.*** *사용 중인 데이터를 분류했으며 장치에 PII 또는 PHI가 존재하지 않도록 분류했습니까?*<br> ***h.*** *사용 중인 데이터를 분류했으며, 장치에 PII(개인 식별 정보) 또는 PHI(Protected Health Information)가 존재하지 않습니까?*<br> ***i.*** *e-메일 모니터링을 구성했으며, 이메일 모니터링과 비 핑 장치 처리를 위한 SOP가 있습니까?* |
| **액세스 제어** | ***a.*** *내에서 RBAC(Role Based Access Control)가 확인되고 관리됩니까?* <br>***b.*** *Adobe에서 모범 사례를 사용하여 작성자, 관리자 및 플레이어에 액세스할 수 있는 권한 없음을 따르지 않았습니까?* |

### 보안 검사 목록 다운로드 중 {#download-checklist}

AEM Screens 보안 검사 목록을 다운로드하려면 여기](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)를 클릭합니다.[
