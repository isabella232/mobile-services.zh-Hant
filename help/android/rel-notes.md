---
description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 發行說明和已知問題。
seo-title: 發行說明
solution: Marketing Cloud、Analytics
title: 發行說明
topic: 開發人員和實施
uuid: 16bb4de8-a216-47a8-928c-3b1 e1421 adf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# 發行說明 {#release-notes}

以下是適用於Experience Cloud解決方案的Android SDK4.x發行說明、已知問題和Hotfix資訊：

**2019年月日：第4.17.9版**

* 訪客ID服務：修正呼叫SyncIdentifiers時 `StrictMode` 發生的違規問題。

   這項違規行為是因為讀取主要執行緒上的共用偏好設定所造成。

* Adobe Target：新增 `requestLocationParameters` 屬性， `TargetRequestObject`可讓IMpressionID隨Target請求傳送。

**2019年月18日：第4.17.8版**

* Adobe Target：所有請求現在都會在URL查詢參數中納入用戶端和sessionId。
* 應用程式內傳訊: 修正透過空白點選連結 URL 觸發訊息時，Android 應用程式當機的問題。
* 訪客 ID 服務: `Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019年月日：4.17.7版**

* 一般-在低於20的Android API層級上的網路呼叫現在會使用TLS1.1或TLS1.2。
* Analytics-啓用推播通知時，附加的推播通知狀態至生命週期資料。

**2019年月24日：4.17.6版**

* 訪客ID服務-
   `setPushIdentifier` API呼叫現在會在每次呼叫訪客ID服務時傳送同步呼叫。

* 訪客ID服務-增加連線並將逾時從秒讀取到秒。


如需詳細瞭解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
