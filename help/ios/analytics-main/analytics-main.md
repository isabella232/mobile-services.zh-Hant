---
description: 此資訊可協助您將 iOS SDK 與 Adobe Analytics 搭配使用。
seo-description: 此資訊可協助您將 iOS SDK 與 Adobe Analytics 搭配使用。
seo-title: Analytics概觀
solution: Marketing Cloud、Analytics
title: Analytics概觀
topic: 開發人員和實施
uuid: 8c7fb76a-be0 b-4465-8151-ease7 bug11 b55
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Analytics概觀 {#analytics}

本節中的資訊可協助您搭配Adobe Analytics使用iOS SDK。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

## 產生Analytics追蹤識別碼

在 SDK 中，識別碼是用來追蹤使用者，以下為識別碼的階層關係:

1. 自訂訪客識別碼 (VID)
2. Analytics 追蹤識別碼 (AID)
3. Experience Cloud 識別碼 (MID)

>[!TIP]
>
>Experience Cloud識別碼的正確縮寫是ECID。雖然 SDK 仍使用 MID，但這是舊稱。AID 有時也稱為追蹤識別碼，是在應用程式沒有設定要使用 MID 時，由 SDK 產生的追蹤碼。此值會在啟動和應用程式更新之間保存在 `NSUserDefaults`。如果使用者從裝置上刪除應用程式，然後重新安裝應用程式，或者應用程式開發人員清除了 `NSUserDefaults`，SDK 便會產生新的識別碼。這個程序會導致 Analytics 報告中產生新的使用者。

若為導入身分服務支援 (MID) 的應用程式使用者，現有的 AID 值會與 Analytics 點擊一併傳送，且 Analytics 點擊包含 AID 和 MID。若為提供身分服務支援的應用程式的新使用者，Analytics 請求。For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
