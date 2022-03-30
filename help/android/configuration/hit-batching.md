---
description: 點擊批次處理程序可讓應用程式保留點擊不傳送，直到佇列中的點擊數超過設定上限為止。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 點擊批次處理程序
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# 點擊批次處理程序 {#hit-batching}

點擊批次處理程序可讓應用程式保留點擊不傳送，直到佇列中的點擊數超過設定上限為止。

>[!IMPORTANT]
>
>若要使用點擊批次處理程序，您&#x200B;**必須**&#x200B;啟用離線追蹤，且有 SDK 4.1 版或更新版本

若要啟用點擊批次處理程序，請更新 `ADBMobileConfig.json` 檔案，並指定 `batchLimit` 的值:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

當此值被設定為大於 0 的數字時，SDK 會讓排入佇列的點擊數等於 *`batchLimit`* 值。超過此臨界值後，系統會傳送佇列中的所有點擊。

下列方法可搭配點擊批次處理程序使用：

* `Analytics.getQueueSize` 會在目前點擊批次處理程序佇列中傳回 `long` 與點擊數。

* `Analytics.sendQueuedHits` 會強制資料庫傳送佇列中的所有點擊，不論目前還有多少點擊處於佇列中皆然。
* `Analytics.clearQueue` 會清除佇列中的所有點擊，而不會進行傳送。
