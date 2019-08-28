---
description: 回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。
seo-description: 回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。
seo-title: 回傳
solution: Marketing Cloud、Analytics
title: 回傳概述
uuid: 25e2a5fb-1203-40dd-96cd-b23 e0 f23376 d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# 回傳概述 {#postbacks}

回傳可讓您將 SDK 收集的資料傳送至第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 SDK 將自訂資料傳送至第三方目的地。

>[!IMPORTANT]
>
>此功能需要SDK4.6.0版或更新版本。

回傳訊息會排入佇列並遵循管理分析資料收集的所有現有線上/離線規則。當訊息符合時 (如同所顯示的訊息一樣)，回傳訊息不會取消剩餘的訊息。這會讓同一個分析點撃中出現多個回傳。如需定義，請參閱&#x200B;*回傳*&#x200B;列，位於 [ADBMobile JSON 設定中](/help/ios/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. 除了附加到觸發訊息之點擊的任何自訂資料之外，範本展開可用的值僅限於[標準生命週期變數清單](/help/ios/metrics.md)。目前沒有以歷史為基礎或以區段為基礎的資料可用。

SDK 也會將特定的已保留範本，自動替換為 SDK 已知的內部資料。

此清單包括:

| 代號名稱 | 代號說明 |
|--- |--- |
| `{%sdkver%}` | 傳回 SDK 版本。 |
| `{%cachebust%}` | 解析至 1 至 100000000 之間的一個隨機數字。 |
| `{%adid%}` | 傳回 IDFA。這個代號只有在您使用 `setAdvertisingIdentifier`時才有用。 |
| `{%pushid%}` | 傳回推送識別碼代號。這個代號只有在您使用 `setPushIdentifier`時才有用。 |
| `{%timestampu%}` | 傳回目前時間戳記 (以 Epoch 時間計)。 |
| `{%timestampz%}` | 傳回 JavaScript (ISO 8601) 格式的目前時間戳記。 |