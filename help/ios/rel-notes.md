---
description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 發行說明和已知問題。
seo-description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 發行說明和已知問題。
seo-title: 發行說明
solution: Marketing Cloud,Analytics
title: 發行說明
topic: 開發人員和實施
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 發行說明 {#release-notes}

以下是適用於Experience cloud解決方案的iOS SDK 4.x的發行說明、已知問題和修補程式資訊：

**2019年9月20日：版本4.18.8**

* 應用程式內傳訊：

   * 在執行iOS 10或更新版本的裝置上， `UserNotifications` 架構現在可用來排程連結至的應用程式的本機通知 `UserNotifications.framework`。
   * 全螢幕訊息現在會使用 `WebKit.framework`Xcode專案中必須連結的WKWebViews。
   * 已修正推送點進裝載無法用作應用程式內訊息特徵的錯誤。
   * 已修正當機問題。

* 一般——已修正每次Analytics呼叫時，SDK資料會同步至配對watchOS應用程式的錯誤。

**2019年8月2日：版本4.18.7**

* 還原4.18.6版中所引入的變更，此變更在某些環境中造成執行11.0以上iOS版本的裝置當機。

* Adobe Target:新增屬 `requestLocationParameters` 性，可 `ADBTargetRequestObject`讓impressionId隨Target請求一起傳送。

**2019年7月18日：版本4.18.6**

* Adobe Target: 所有要求現在都會在 URL 查詢參數中納入用戶端和 `sessionId`。
* Adobe Target: 修正記憶體流失。
* 訪客 ID 服務: `visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019年6月5日：4.18.5版**

* Analytics —— 啟用推播通知時，將推播選擇加入狀態附加至生命週期資料。

**2019年5月24日：版本4.18.4**

* 訪客ID服務——增加
   `visitorGetUrlVariablesAsync` API至30秒。

* 訪客ID服務- `setPushIdentifier` API呼叫現在會在每次呼叫訪客ID服務時傳送同步呼叫給該服務。

如需詳細瞭解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
