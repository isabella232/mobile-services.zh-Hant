---
description: 點擊批次處理程序可讓應用程式保留點擊不傳送，直到佇列中的點擊數超過設定上限為止。
keywords: Android；資料庫；行動；sdk
seo-description: 點擊批次處理程序可讓應用程式保留點擊不傳送，直到佇列中的點擊數超過設定上限為止。
seo-title: 點擊批次處理程序
solution: Marketing Cloud、Analytics
title: 點擊批次處理程序
topic: 開發人員和實施
uuid: ada35be3-242b-4b2b-a828-9fb998 dd58 b5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 點擊批次處理程序 {#hit-batching}

點擊批次處理程序可讓應用程式保留點擊不傳送，直到佇列中的點擊數超過設定上限為止。

>[!IMPORTANT]
>
>若要使用點擊批次處理，您 **必須** 啓用離線追蹤並擁有SDK4.1版或更新版本

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. 超過此臨界值後，佇列中的所有點擊都會傳送。

下列方法可搭配點擊批次處理程序使用:

* `Analytics.getQueueSize` 會在目前點擊批次處理程序佇列中傳回 `long` 與點擊數。

* `Analytics.sendQueuedHits` 會強制資料庫傳送佇列中的所有點擊，不論目前還有多少點擊處於佇列中皆然。
* `Analytics.clearQueue` 會清除佇列中的所有點擊，而不會進行傳送。
