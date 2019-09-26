---
description: 回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。
keywords: android;library;mobile;sdk
seo-description: 回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。
seo-title: 回傳
solution: Marketing Cloud,Analytics
title: Postbacks overview
topic: 開發人員和實施
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# 回傳 {#postbacks}

回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。

>[!IMPORTANT]
>
>此功能需要SDK 4.6.0版或更新版本。

回傳訊息會排入佇列並遵循管理分析資料收集的所有現有線上/離線規則。當訊息符合時 (如同所顯示的訊息一樣)，回傳訊息不會取消剩餘的訊息。這會讓同一個分析點撃中出現多個回傳。如需定義，請參閱&#x200B;*回傳*&#x200B;列，位於 [ADBMobile JSON 設定中](/help/android/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. 目前沒有以歷史或區段為基礎的資料可用。

SDK 也會將特定的已保留範本，自動替換為 SDK 已知的內部資料。

此清單包括:

| 代號名稱 | 代號說明 |
|--- |--- |
| {%sdkver%} | 傳回SDK版本。 |
| {%cachebust%} | 解析至 1 至 100000000 之間的一個隨機數字。 |
| {%adid%} | 傳回 Android 適用的廣告商 ID。注意，這只有在您已使用 `submitAdvertisingIdentifierTask` 時才有效。 |
| {%pushid%} | 傳回推送識別碼代號。注意，這只有在您已使用 `setPushIdentifier` 時才有效。 |
| {%timestampu%} | 傳回目前時間戳記 (以 Epoch 時間計)。 |
| {%timestampz%} | 傳回 JavaScript (ISO 8601) 格式的目前時間戳記。 |