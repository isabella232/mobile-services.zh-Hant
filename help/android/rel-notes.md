---
description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-title: 發行說明
solution: Marketing Cloud,Analytics
title: 發行說明
topic: 開發人員和實施
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 發行說明 {#release-notes}

以下是適用於 Experience Cloud 解決方案的 Android SDK 4.x 的發行說明、已知問題和 Hotfix 資訊:

**2019 年 9 月 20 日: 4.17.10 版**

* 一般: 修正 Android API Level 21 或更新版本上某些地區的地區字串產生問題。

**2019 年 7 月 18 日: 4.17.8 版**

* Adobe Target: 所有要求現在都會在 URL 查詢參數中納入用戶端和 sessionId。
* 應用程式內傳訊: 修正透過空白點選連結 URL 觸發訊息時，Android 應用程式當機的問題。
* 訪客 ID 服務: `Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019 年 6 月 6 日: 4.17.7 版**

* 一般 - 低於 20 的 Android API 層級上的網路呼叫現在將使用 TLS 1.1 或 TLS 1.2。
* Analytics - 在啟用推送通知時，將推送選擇加入狀態附加至生命週期資料。

**2019 年 5 月 24 日: 4.17.6 版**

* 訪客 ID 服務 - 
   `setPushIdentifier` API 呼叫現在會在每次呼叫時將同步處理呼叫傳送至訪客 ID 服務。

* 訪客 ID 服務 - 將連線和讀取逾時從 2 秒增加到 5 秒。


如需詳細瞭解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/zh_TW/whatsnew/)。
