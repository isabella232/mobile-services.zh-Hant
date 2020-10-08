---
description: 這項資訊可協助您搭配Adobe Analytics使用iOS SDK。
seo-description: 這項資訊可協助您搭配Adobe Analytics使用iOS SDK。
seo-title: Analytics 概述
solution: Experience Cloud,Analytics
title: Analytics 概述
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 67%

---


# Analytics 概述 {#analytics}

本節中的資訊可協助您將 iOS SDK 與 Adobe Analytics 搭配使用。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 產生 Analytics 追蹤識別碼

在SDK中，識別碼用於追蹤使用者，以下是識別碼的階層：

1. 自訂訪客識別碼(VID)
1. Analytics追蹤識別碼(AID)
1. Experience Cloud識別碼(MID)

>[!TIP]
>
>Experience Cloud 識別碼的正確縮寫為 ECID。雖然 SDK 仍使用 MID，但這是舊稱。

AID 有時也稱為追蹤識別碼，是在應用程式沒有設定要使用 MID 時，由 SDK 產生的追蹤碼。此值會在啟動和應用程式更新之間保存在 `NSUserDefaults`。如果使用者從裝置上刪除應用程式，然後重新安裝應用程式，或者應用程式開發人員清除了 `NSUserDefaults`，SDK 便會產生新的識別碼。此程式會在Analytics報表中產生新使用者。

對於採用身分服務支援(MID)的應用程式中的使用者，現有的AID值會隨Analytics點擊傳送，而Analytics點擊則包含AID和MID。 對於具有Identity Service支援的應用程式中的新使用者，Analytics請求只包含MID。 如需識別訪客的詳細資訊，請參閱[識別訪客](https://docs.adobe.com/content/help/zh-Hant/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)。
