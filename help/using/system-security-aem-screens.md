---
title: AEM Screens에 대한 보안 검사 목록
seo-title: AEM Screens에 대한 보안 검사 목록
description: 이 페이지에서는 AEM Screens에 대한 보안 체크리스트에 대해 설명합니다.
seo-description: 이 페이지에서는 AEM Screens에 대한 보안 체크리스트에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: 72551a4b56d1db851cad71abd2ce8c0b02bbbc30

---


# AEM Screens에 대한 시스템 보안 고려 사항 {#security-checklist}

이 페이지에서는 AEM Screens에 대한 시스템 보안 고려 사항을 강조 표시합니다.


## AEM Screens 보안 백서 {#white-paper}

이 섹션에서는 백서에 대해 설명합니다. (백서 첨부 보류 중)


## AEM Screens 보안에 대한 FAQ {#faqs-screens}

다음 FAQ 파섹

### FAQ 1 {#faq1}

플레이어 트래픽을 악성 서버로 다시 라우팅하여 악성 미디어 컨텐츠를 다운로드 및 재생하도록 지시할 수 있습니까?

**답변**

HTTPs 연결은 연결의 양쪽 끝을 식별하여 암호화하므로 가능하지 않습니다. 중간에 있다가 차단하려고 하면 암호화된 내용만 표시되고 서버를 가장하려고 하면 인증서가 다르기 때문에 플레이어가 거부됩니다.


### FAQ 2 {#faq2}

HTTP 또는 HTTP를 사용해야 합니까?

**답변**

HTTP 사용 보안을 염려하는 경우 반드시 사용해야 합니다. HTTP를 사용하면 플레이어와 서버 간에 통신이 암호화되므로 컨텐츠를 차단하거나 수정하는 것은 거의 불가능합니다.


### FAQ 3 {#faq3}

콘텐츠 다운로드에서 콘텐츠 또는 해시의 어떤 종류의 서명이 있습니까?

**답변**

모든 에셋은 서버에서 서명(SHA)한 다음 동일한 해시에 대해 플레이어에서 유효성 검사를 수행하여 무결성을 보장합니다.
해시가 일치하지 않는 경우, 3번 다시 유효성을 검사하려고 합니다. 3회 시도 후 다운로드 명령이 잘못된 것으로 간주합니다.


### FAQ 4 {#faq4}

AEM Server는 안전합니까?

**답변**

&#x200B;4. AMS를 사용하고 있다고 가정할 경우 Adobe는 사이트 또는 자산과 동일한 기능을 사용하여 모든 서버 보안을 관리합니다.


### FAQ 5 {#faq5}

장치가 안전합니까?

**답변**

물리적으로 손상된 플레이어는 이론적으로 조작되어 컨텐츠를 재생할 수 있습니다. 또한 플레이어를 꽂고 USB/HDMI 스틱을 꽂을 수도 있습니다.

따라서 케이블을 안전하게 연결할 수 있는 안전한 컨테이너에서 디바이스를 멀리 떨어진 곳으로 두는 것이 좋습니다. 또한 모든 IR 원격 포트를 비활성화합니다.

장치 OS가 정기적으로 업데이트되지 않는 경우 OS가 보안 구멍에 노출되어 네트워크를 통한 원격 공격을 허용할 수 있습니다.
>[!NOTE]
>적절한 원격 업데이트 및 제어 기능(원격 데스크톱, MDM 솔루션 등)을 사용하여 장치를 계수하는 것이 좋습니다. 예를 들어 공개 WIFI에 노출되지 않고 비공개 네트워크를 사용하는 것이 좋습니다.


### FAQ 6 {#faq6}

해커가 어떻게 선수를 해치려고 시도할까?

**답변**

플레이어 장치를 손상시키는 유일한 방법은 다음과 같습니다.

1. DNS가 서버의 호스트 이름을 사칭하도록 했고,
1. 타협
   1. 서버를 가장할 인증서 서버측
   1. 장치 및 인증서 클라이언트측

>[!IMPORTANT]
>장치가 손상되더라도 AEM에 더 이상 연결할 수 없도록 장치의 자격 증명을 쉽게 취소할 수 있습니다.




