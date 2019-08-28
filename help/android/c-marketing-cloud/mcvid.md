---
description: Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-description: Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-title: Experience Cloud ID組態
solution: Marketing Cloud、Analytics
title: Experience Cloud ID組態
topic: 開發人員和實施
uuid: 8ebdf2ff-c581-448f-9542-f99 a19784 fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service提供跨Experience Cloud解決方案的通用訪客ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。

>[!TIP]
>
>除非您使用Adobe Experience Platform Identity Service，否則不需要填入此ID。For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>此功能需要SDK4.3版或更新版本。

若要啟用 Experience Cloud ID:

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期* 中 [的新增SDK和設定檔案至IntelliJ IDEA或Eclipse專案](/help/android/getting-started/dev-qs.md)。

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含 `marketingCloudorg`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 組織 ID 會唯一識別 Adobe Experience Cloud 中的每一間客戶公司，並與以下值類似: 

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >您必須包含 `@AdobeOrg`。

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 如需詳細資訊，請參閱[開始之前](/help/android/getting-started/requirements.md)。

完成設定後，即會產生一個 Experience Cloud ID 並包含在所有點撃中。其他 ID，例如自訂和自動產生的 ID，會繼續在每次點撃時一併傳送。
