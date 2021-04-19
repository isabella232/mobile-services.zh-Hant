---
description: 點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。
seo-description: 點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。
seo-title: 點擊批次處理程序
solution: Experience Cloud,Analytics
title: 點擊批次處理程序
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 100%

---

# 點擊批次處理程序 {#hit-batching}

點擊批次處理程序可讓應用程式 (已啟用離線追蹤功能) 保留點擊不傳送，直到佇列中的點擊數超過可設定上限為止。

>[!IMPORTANT]
>
>點擊批次處理程序需使用 SDK 4.1 版或更新版本。

若要啟用點擊批次處理程序，請更新 `ADBMobileConfig.json` 檔案，並指定 `batchLimit` 的值:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

當設定的數字高於 0 時，SDK 會讓排入佇列的點擊數等於 *`batchLimit`*。超過此臨界值後，系統會傳送佇列中的所有點擊。

下列方法可搭配點擊批次處理程序使用：

* `trackingGetQueueSize()` 會在目前點擊批次處理程序佇列中傳回 `NSUInteger` 與點擊數。
* `trackingSendQueuedHits()` 會強制資料庫傳送佇列中的所有點擊，不論目前還有多少處於佇列中皆然。
* `trackingClearQueue()` 會清除佇列中的所有點擊，而不會進行傳送。

>[!CAUTION]
>
>必須啟用離線追蹤功能才可使用點擊批次處理程序。
