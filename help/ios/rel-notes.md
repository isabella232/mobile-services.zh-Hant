---
description: Experience Cloud 解決方案專用 iOS SDK 4.x 的發行說明和已知問題。
seo-description: Experience Cloud 解決方案專用 iOS SDK 4.x 的發行說明和已知問題。
seo-title: 發行說明
solution: Experience Cloud,Analytics
title: 發行說明
topic-fix: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
exl-id: dd1e6bab-65e7-4a68-b3ec-21fb1a08aca2
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---

# 發行說明 {#release-notes}

以下是適用於 Experience Cloud 解決方案之 iOS SDK 4.x 的發行說明、已知問題和 Hotfix 資訊：

**2021 年 1 月 13 日：4.21.1 版**

* 一般 - 修正應用程式關閉期間可能導致 SQLite 發生例外狀況的問題。

**2020 年 12 月 15 日：4.21.0 版**

* 一般 - 現已使用 XCFramework 發佈 SDK，以便支援採用最新 Apple M1 架構的硬體，同時繼續支援現有的 Intel 架構。
   * 重要：升級至 AdobeMobile XCFramework 需有 Xcode 12.0 以上版本
   * 重要：如果使用 Cocoapod，升級至 AdobeMobile XCFramework 需有 Cocoapod 1.10.0 以上版本

**2020 年 11 月 4 日：4.20.0 版**

* 訪客 ID 服務：若在啟用/停用廣告追蹤後呼叫 setAdvertisingIdentifier，系統會新增 device_consent 狀態參數。
* Analytics：修正已連結 iAd.framework 且裝置啟用「有限廣告追蹤」後，Analytics 點擊延遲傳送的錯誤。

**2020 年 7 月 16 日：4.19.3 版**

* 一般 - 修正具有多個 Equals 登入查詢參數的深度連結 URL 無法正確處理的錯誤。

**2020 年 3 月 24 日：4.19.2 版**

* 一般 - 修正 Target 程式碼中的部分漏洞。

**2020 年 3 月 12 日：4.19.1 版**

* 一般 - 解決追蹤呼叫的內容資料中列舉 Swifte 時可能導致當機的問題。
* Target - Target 工作階段 ID 現在會在傳送至 Adobe Analytics 的內部 Analytics for Target 點擊中，以內容資料參數「a.target.sessionId」的形式新增。

**2020 年 2 月 4 日：4.19.0 版**

* 生命週期 - 新增 API pauseCollectingLifecycleData，以緩解某些舊 iOS 裝置回報的作業長度異常資料。

**2019 年 11 月 8 日：4.18.9 版**

* 應用程式內傳訊功能 - 修正全螢幕訊息無法載入快取或隨附影像的錯誤。

**2019 年 9 月 20 日：4.18.8 版**

* 應用程式內傳訊：

   * 在執行 iOS 10 或更新版本的裝置上，`UserNotifications` 架構現可用來排定連結至 `UserNotifications.framework` 之應用程式的本機通知。
   * 全螢幕訊息現可使用來自 `WebKit.framework` 的 WKWebViews，而您的 Xcode 專案中必須連結該架構。
   * 修正無法使用推送點進裝載做為應用程式內傳訊特徵的錯誤。
   * 修正當機問題。

* 一般 - 修正在每個 Analytics 呼叫上 SDK 資料已同步處理到配對的 WatchOS 應用程式的錯誤。

**2019 年 8 月 2 日：4.18.7 版**

* 回復 4.18.6 版中已導入的變更，在某些環境下，該變更在執行比 11.0 更舊的 iOS 版本的裝置上已導致當機問題。

* Adobe Target：在 `ADBTargetRequestObject` 中新增 `requestLocationParameters` 屬性，以便透過 Target 要求傳送 impressionId。

**2019 年 7 月 18 日：4.18.6 版**

* Adobe Target：所有要求現在都會在 URL 查詢參數中納入用戶端和 `sessionId`。
* Adobe Target：修正記憶體流失。
* 訪客 ID 服務：`visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019 年 6 月 5 日：4.18.5 版**

* Analytics - 在啟用推送通知時，會將推送選擇加入狀態附加至生命週期資料。

**2019 年 5 月 24 日：4.18.4 版**

* 訪客 ID 服務 - 將 
   `visitorGetUrlVariablesAsync` API 的傳回逾時增加至 30 秒。

* 訪客 ID 服務 - `setPushIdentifier` API 呼叫現在會在每次呼叫時將同步處理呼叫傳送至訪客 ID 服務。

如需詳細了解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://docs.adobe.com/content/help/zh-Hant/release-notes/experience-cloud/current.html)。
