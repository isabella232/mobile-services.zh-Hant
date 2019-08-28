---
description: 點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。
seo-description: 點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。
seo-title: 點擊批次處理程序
solution: Marketing Cloud、Analytics
title: 點擊批次處理程序
topic: 開發人員和實施
uuid: 3dda7372-0695-4cb7-b779-1abca2 d0 d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 點擊批次處理程序 {#hit-batching}

點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。

>[!IMPORTANT]
>
>點擊批次處理需要SDK4.1版或更新版本。

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

當設定的數字高於 0 時，SDK 會讓排入佇列的點擊數等於 *`batchLimit`*. 超過此臨界值後，佇列中的所有點擊都會傳送。

下列方法可搭配點擊批次處理程序使用:

* `trackingGetQueueSize()` 傳回 `NSUInteger` 點擊批次處理佇列中目前的點擊次數。
* `trackingSendQueuedHits()` 強制程式庫傳送佇列中所有點擊，不論目前佇列中有多少點擊。
* `trackingClearQueue()` 會清除佇列中的所有點擊，而不會進行傳送。

>[!CAUTION]
>
>必須啓用離線追蹤才能使用點擊批次處理。

