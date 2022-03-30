---
description: 建立、管理和報告應用程式內以及推送訊息。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 傳訊
topic-fix: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
exl-id: e6d076fc-3176-4591-8388-314b936c58cd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 100%

---

# 傳訊 {#messaging}

您可以建立、管理和報告應用程式內及推送訊息。

## 新版 Adobe Experience Cloud SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> 如果您使用 Adobe Experience Platform Mobile SDK 搭配 Adobe Launch，您&#x200B;**必須**&#x200B;同時安裝 Adobe Analytics Mobile Services 擴充功能，方可使用贏取連結之類的 Adobe Mobile Services 功能。如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。如需有關使用推播訊息和應用程式內訊息搭配 Experience Platform SDK，請參閱[設定推播訊息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)和[設定應用程式內訊息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)。

## 應用程式內訊息 {#section_8984F4568BC24D32A87429FFCB5184A6}

應用程式內訊息是根據使用者的動作和特性，即時傳送給使用者。訊息是從已由 SDK 追蹤的 Analytics 資料觸發。

支援的訊息類型如下：

* 自訂與佈景主題
* 全螢幕
* 原生警報
* 本機通知

為協助您瞭解應用程式內訊息的運作方式，以下提供其他資訊:

* 應用程式內訊息需使用 SDK 4.2 版或更新版本。
* 您必須指定擁有行動應用程式管理員權限的使用者。

   這些權限可讓使用者存取贏取連結和應用程式內訊息。如需詳細資訊，請參閱[角色和權限](/help/using/gs/c-mob-roles-and-permissions.md)。
* 訊息經核准後，即會自動發佈至應用程式。
* SDK 會在訊息參數 (例如特性、觸發器和排程) 符合時，向使用者顯示訊息。
* 訊息可使用線上 URL 納入自訂 HTML 或影像。

   您也可以為離線時觸發的訊息指定應用程式套件中的備份或替代影像。
* 使用中及完成的訊息提供檢視總計、點進率等報表。
* 自訂訊息有範本可用，可讓您輕鬆建立專屬的應用程式內訊息。

## 推送訊息 {#section_90555A55BCE7427A90B1577E14BEF51B}

推送訊息會傳送給選擇收到通知的使用者。您可以在 Analytics 區段或自訂區段中將這些推送訊息定位給使用者。推送訊息很適合用來與被動使用者重新互動，或是傳達與特定時間和位置相關的資訊，因為訊息會在您的應用程式外部顯示。

設定推送訊息之前，請參閱[啟用推送訊息的必要條件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)。執行這些工作後，您必須在應用程式的設定中設定推播訊息。如需詳細資訊，請參閱[設定推播訊息](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md)。
