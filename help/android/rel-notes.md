---
description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-title: 發行說明
solution: Marketing Cloud,Analytics
title: 發行說明
topic: 開發人員和實施
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 發行說明 {#release-notes}

以下是Experience cloud解決方案專用Android SDK 4.x的發行說明、已知問題和修補程式資訊：

**2019年9月20日：版本4.17.10**

* 一般：修正Android API 21或更新版本上某些地區的地區字串產生問題。

**2019年7月18日：版本4.17.8**

* Adobe Target:所有請求現在都會在URL查詢參數中包含用戶端和sessionId。
* 應用程式內傳訊: 修正透過空白點選連結 URL 觸發訊息時，Android 應用程式當機的問題。
* 訪客 ID 服務: `Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019年6月6日：版本4.17.7**

* 一般——低於20的Android API層級的網路呼叫現在會使用TLS 1.1或TLS 1.2。
* Analytics —— 啟用推播通知時，將推播選擇加入狀態附加至生命週期資料。

**2019年5月24日：版本4.17.6**

* 訪客ID服務-
   `setPushIdentifier` API呼叫現在會在每次呼叫訪客ID服務時傳送非同步呼叫。

* 訪客ID服務——將連線和讀取逾時從2秒增加為5秒。


如需詳細瞭解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
