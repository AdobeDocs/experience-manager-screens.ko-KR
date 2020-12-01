---
title: REST API
seo-title: REST API
description: AEM Screens은 사이렌 사양을 따르는 간단한 RESTful API를 제공합니다. 컨텐츠 구조를 탐색하고 환경의 장치에 명령을 보내는 방법을 알려면 이 페이지를 따르십시오.
seo-description: AEM Screens은 사이렌 사양을 따르는 간단한 RESTful API를 제공합니다. 컨텐츠 구조를 탐색하고 환경의 장치에 명령을 보내는 방법을 알려면 이 페이지를 따르십시오.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# REST API{#rest-apis}

AEM Screens은 [Synamn](https://github.com/kevinswiber/siren) 사양을 따르는 간단한 RESTful API를 제공합니다. 이를 통해 컨텐츠 구조를 탐색하고 환경의 장치에 명령을 보낼 수 있습니다.

API는 [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json)에서 액세스할 수 있습니다.

## 콘텐츠 구조 탐색 {#navigating-content-structure}

API 호출에서 반환되는 JSON은 현재 리소스와 관련된 개체를 나열합니다. 나열된 자체 링크에 따라 이러한 각 엔티티는 REST 리소스로 다시 액세스할 수 있습니다.

예를 들어 Adobe 데모 대표 위치의 디스플레이에 액세스하려면 다음을 호출할 수 있습니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

또는 말림 사용:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

결과는 다음과 같습니다.

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

그런 다음 단일 화면 디스플레이에 액세스하려면 다음을 호출할 수 있습니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## 리소스 {#executing-actions-on-the-resource}에 대한 작업 실행

API 호출에 의해 반환되는 JSON에는 리소스에 사용 가능한 작업 목록이 포함될 수 있습니다.

예를 들어 디스플레이에는 해당 디스플레이에 할당된 모든 장치에 명령을 보낼 수 있는 *broadcast-command* 동작이 표시됩니다.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

또는 말림 사용:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***결과:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

이 작업을 트리거하려면 다음을 호출합니다.

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

또는 말림 사용:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

