---
description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 發行說明和已知問題。
seo-description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 發行說明和已知問題。
seo-title: 發行說明
solution: Marketing Cloud、Analytics
title: 發行說明
topic: 開發人員和實施
uuid: e1613dc5-02a4-43a7-97a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# 發行說明 {#release-notes}

以下是適用於Experience Cloud解決方案的iOS SDK4.x發行說明、已知問題和Hotfix資訊：

**2019年月日：4.18.7版**

* 回復4.18.6版中推出的變更，在某些環境下，在執行iOS版本之前的裝置上導致當機的裝置當機。

* Adobe Target：新增 `requestLocationParameters` 屬性， `ADBTargetRequestObject`可讓IMpressionID隨Target請求傳送。

**2019年月18日：4.18.6版**

* Adobe Target: 所有要求現在都會在 URL 查詢參數中納入用戶端和 `sessionId`。
* Adobe Target: 修正記憶體流失。
* 訪客 ID 服務: `visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

**2019年月日：第4.185版**

* Analytics-啓用推播通知時，附加推播通知至生命週期資料。

**2019年月24日：第4.18.4版**

* 訪客ID服務-提高
   `visitorGetUrlVariablesAsync` API為30秒。

* 訪客ID服務- `setPushIdentifier` API呼叫現在會在每次呼叫訪客ID服務時傳送同步呼叫。

如需詳細瞭解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
