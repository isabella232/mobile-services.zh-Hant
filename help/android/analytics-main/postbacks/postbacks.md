---
description: 回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用您用來顯示應用程式內訊息的相同觸發器和特性，便可以設定 SDK 將自訂資料傳送至第三方目的地。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud,Analytics
title: 回傳概述
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 100%

---

# 回傳 {#postbacks}

回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用您用來顯示應用程式內訊息的相同觸發器和特性，便可以設定 SDK 將自訂資料傳送至第三方目的地。

>[!IMPORTANT]
>
>此功能需使用 SDK 4.6.0 版或更新版本。

回傳訊息會排入佇列，並遵守所有管理分析資料收集的現有線上/離線規則。訊息符合 (如顯示的訊息) 時，回傳訊息不會取消其餘訊息。這可在同一分析點擊發生多個回傳。如需定義，請參閱 [ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)中的&#x200B;*「回傳」*&#x200B;列。

## 範本展開 {#section_6758AD05A24C4E9E965F5253294C164A}

範本展開在 `templateurl` 和 `templatebody` 屬性中均可用。範本項目會採取 `{key}` 的形式，其中 `key` 可以是內容資料索引鍵或傳統資料索引鍵。除了附加到觸發訊息之點擊的任何自訂資料之外，範本展開可用的值僅限於[生命週期量度](/help/android/metrics.md)。目前沒有以歷程記錄或區段為準的資料可供使用。

此外，SDK 也會自動以 SDK 已知的內部資料取代特定的保留範本。

此清單包括：

| 代號名稱 | 代號說明 |
|--- |--- |
| {%sdkver%} | 傳回 SDK 版本。 |
| {%cachebust%} | 解析至 1 至 100000000 之間的一個隨機數字。 |
| {%adid%} | 傳回 Android 適用的廣告商 ID。注意，這只有在您已使用 `submitAdvertisingIdentifierTask` 時才有效。 |
| {%pushid%} | 傳回推送識別碼代號。注意，這只有在您已使用 `setPushIdentifier` 時才有效。 |
| {%timestampu%} | 傳回目前時間戳記 (以 Epoch 時間計)。 |
| {%timestampz%} | 傳回 JavaScript (ISO 8601) 格式的目前時間戳記。 |
