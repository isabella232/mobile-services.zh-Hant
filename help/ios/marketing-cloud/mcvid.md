---
description: Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-description: Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-title: Experience Cloud ID
solution: Marketing Cloud、Analytics
title: Experience Cloud ID
topic: 開發人員和實施
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。

>[!TIP]
>
>您不需要填入Experience Cloud ID，除非您使用Adobe Experience Platform Identity Service。For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**需要 SDK 4.3 版或更新版本**

## 啓用Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期中的新增SDK和設定檔案至您的專案*[](/help/ios/getting-started/dev-qs.md)。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含 `marketingCloud``org`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >您必須包含 `@AdobeOrg`。

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 如需詳細資訊，請參閱 [ADBMobile JSON設定](/help/ios/getting-started/requirements.md)。

設定後，即會產生一個 Experience Cloud ID 並包含在所有點撃中。其他訪客 ID，例如自訂和自動產生的 ID，會繼續在每次點撃時一併傳送。
