---
description: 此資訊可協助您將 Android SDK 與 Adobe Analytics 搭配使用。
keywords: android;資料庫;行動;sdk
seo-description: 此資訊可協助您將 Android SDK 與 Adobe Analytics 搭配使用。
seo-title: Analytics 概述
solution: Marketing Cloud,Analytics
title: Analytics 概述
topic: 開發人員和實施
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Analytics 概述 {#analytics}

本節中的資訊可協助您將 Android SDK 與 Adobe Analytics 搭配使用。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 產生 Analytics 追蹤識別碼

在 SDK 中，識別碼是用來追蹤使用者，以下為識別碼的階層關係:

1. 自訂訪客識別碼 (VID)
2. Analytics 追蹤識別碼 (AID)
3. Experience Cloud 識別碼 (MID)

>[!TIP]
>
>Experience Cloud 識別碼的正確縮寫為 ECID。雖然 SDK 仍使用 MID，但這是舊稱。

AID 有時也稱為追蹤識別碼，是在應用程式沒有設定要使用 MID 時，由 SDK 產生的追蹤碼。此值會在啟動和應用程式更新之間保存在 `SharedPreferences`。如果使用者從裝置上刪除應用程式，然後重新安裝應用程式，或者應用程式開發人員清除了 SharedPreferences，SDK 便會產生新的識別碼。這個程序會導致 Analytics 報告中產生新的使用者。

若為導入身分服務支援 (MID) 的應用程式使用者，現有的 AID 值會與 Analytics 點擊一併傳送，且 Analytics 點擊包含 AID 和 MID。若為提供身分服務支援的應用程式的新使用者，Analytics 請求。如需識別訪客的詳細資訊，請參閱[識別訪客](https://docs.adobe.com/content/help/zh-Hant/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)。