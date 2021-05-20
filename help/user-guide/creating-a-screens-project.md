---
title: 프로젝트 생성 및 관리
seo-title: 프로젝트 만들기
description: 새 화면 프로젝트를 생성하는 방법에 대해 알려면 이 페이지를 따르십시오.
seo-description: 새 화면 프로젝트를 생성하는 방법에 대해 알려면 이 페이지를 따르십시오.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 00ea321c-3f79-4aa5-83cc-3fa2fe9e35d9
feature: 스크린 작성
role: Administrator, Developer
level: Intermediate
exl-id: d98b449f-6b7d-4c08-b507-a64dece84ba8
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 38%

---

# 프로젝트 만들기 및 관리 {#creating-and-managing-projects}

Adobe Experience Manager 링크(왼쪽 위)를 선택한 다음, [스크린]을 선택하여 AEM Screens를 사용할 수 있습니다.

또는 다음 위치로 직접 이동할 수 있습니다.`http://localhost:4502/screens.html/content/screens`


>[!NOTE]
>**탐색 팁:**
>커서 키를 사용하여 AEM에서 다양한 폴더를 탐색할 수도 있습니다. 또한 특정 엔티티를 선택하면 스페이스 바를 눌러 해당 특정 폴더의 속성을 편집하거나 볼 수도 있습니다.

## 새 스크린 프로젝트 생성 {#creating-a-new-screens-project}

아래 절차에 따라 새 스크린 프로젝트를 생성하십시오.

1. AEM 인스턴스에서 **Screens**&#x200B;를 선택합니다.

1. **스크린 프로젝트 만들기**&#x200B;를 클릭합니다.

1. 제목을 **TestScreens**&#x200B;로 입력하고 **저장**&#x200B;을 클릭합니다.

프로젝트가 생성되고 다시 스크린 프로젝트 콘솔로 돌아갑니다. 이제 프로젝트를 선택할 수 있습니다.

프로젝트에는 아래 그림과 같이 5가지 종류의 폴더가 있습니다.

* **예약**
* **위치**
* **애플리케이션**
* **장치**
* **채널**

![player1](assets/create-project.gif)

>[!NOTE]
>
>기본적으로 초기 구조에는 **예약**, **위치**, **응용 프로그램**, **채널** 및 **장치** 마스터 페이지가 포함되지만, 필요한 경우 수동으로 조정할 수 있습니다. 사용 가능한 옵션이 프로젝트와 관련이 없는 경우 옵션을 제거할 수 있습니다.


## 속성 보기 {#viewing-properties}

스크린 프로젝트를 만든 후 프로젝트를 선택하고 작업 표시줄에서 **속성** 을 클릭하여 프로젝트의 속성을 편집합니다.

다음 옵션을 사용하면 **TestScreens**&#x200B;의 속성을 편집/변경할 수 있습니다.

![이미지](assets/create-project2.png)


## 사용자 지정 폴더 만들기 {#creating-a-custom-folder}

또한 **예약**, **위치**, **응용 프로그램**, **채널** 및 **장치** 마스터 페이지에서 사용할 수 있는 고유한 사용자 지정 폴더를 만들 수 있습니다.

사용자 지정 폴더를 만들려면 다음을 수행하십시오.

1. 프로젝트를 선택하고 작업 표시줄의 더하기 아이콘 옆에 있는 **만들기**&#x200B;를 클릭합니다.
1. **만들기** 마법사가 열리면 적절한 선택 사항을 선택합니다.
1. **다음**&#x200B;을 클릭합니다.
1. 속성을 입력하고 **만들기**&#x200B;를 클릭합니다.

다음 단계는 **TestScreens**&#x200B;에서 **Applications** 마스터 페이지에 응용 프로그램 폴더를 만드는 방법을 보여 줍니다.

![player2-1](assets/create-project3.gif)

### 다음 단계 {#the-next-steps}

고유한 프로젝트를 만들었으면 [채널 관리](managing-channels.md)를 참조하여 채널에서 컨텐츠를 만들고 관리하십시오.
