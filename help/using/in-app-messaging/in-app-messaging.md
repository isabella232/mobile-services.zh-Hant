---
description: 建立、管理和報告應用程式內以及推送訊息。
keywords: 行動
seo-description: 建立、管理和報告應用程式內以及推送訊息。
seo-title: 傳訊
solution: Marketing Cloud、Analytics
title: 傳訊
topic: 量度
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# 傳訊 {#messaging}

您可以建立、管理和報告應用程式內和推送訊息。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。如需有關使用推播訊息和應用程式內訊息搭配 Experience Platform SDK，請參閱[設定推播訊息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)和[設定應用程式內訊息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)。

## In-app messages {#section_8984F4568BC24D32A87429FFCB5184A6}

應用程式內訊息是根據使用者的動作和特性，即時傳送給使用者。訊息是從已由 SDK 追蹤的 Analytics 資料觸發。

支援的訊息類型如下:

* 自訂和主題
* 全螢幕
* 原生警告
* 本機通知

為協助您瞭解應用程式內傳訊如何運作，以下是一些額外資訊：

* 應用程式內訊息需要SDK4.2版或更新版本。
* 您必須指定誰擁有「行動應用程式管理員」權限。

   這些權限可讓您存取贏取連結和應用程式內訊息。如需詳細資訊，請參閱 [角色和權限](/help/using/gs/c-mob-roles-and-permissions.md)。
* 核准訊息後，訊息會自動發佈至應用程式。
* 條件符合所設的訊息參數 (特徵、觸發器和排程) 時，SDK 就會向使用者呈現訊息。
* 訊息可以包含自訂 HTML 或影像 (使用線上 URL)。

   您也可以指定將應用程式套件中的備份或替代影像用於離線時觸發的訊息。
* 使用中及完成的訊息提供檢視總計、點進率等報表。
* 自訂訊息有範本可用，可讓您輕鬆建立專屬的應用程式內訊息。

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

推送訊息會傳送給選擇收到通知的使用者。您可以在 Analytics 區段或自訂區段中將這些推送訊息定位給使用者。推送訊息很適合用來與被動使用者重新互動，或是傳達與特定時間和位置相關的資訊，因為訊息會在您的應用程式外部顯示。

在設定推送訊息之前，請先參閱 [「必要條件」以啓用推送訊息](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)。執行這些任務後，您必須在應用程式的設定中配置推送訊息。如需詳細資訊，請參閱[設定推送訊息](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md)。
