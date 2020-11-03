---
description: Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-description: Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-title: Experience Cloud ID 設定
solution: Experience Cloud,Analytics
title: Experience Cloud ID 設定
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Experience Cloud ID 設定 {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。

>[!TIP]
>
>除非您使用 Adobe Experience Platform Identity Service，否則無須填入此 ID。如需詳細資訊，請參閱 [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/zh-Hant/id-service/using/home.html)。

>[!IMPORTANT]
>
>此功能需使用 SDK 4.3 版或更新版本。

若要啟用 Experience Cloud ID：

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫：

   ```java
   import com.adobe.mobile.*;
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含 `marketingCloudorg`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 組織 ID 會不重複識別 Adobe Experience Cloud 中的每一間客戶公司，其格式與以下值類似：

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >您必須包含 `@AdobeOrg`。

   如果未設定這些 ID，請從 Adobe Mobile Services 下載更新的 `ADBMobileConfig.json` 檔案。如需詳細資訊，請參閱[開始之前](/help/android/getting-started/requirements.md)。

完成設定後，系統會產生一組 Experience Cloud ID，並包含在所有點撃中。其他 ID (例如自訂和自動產生的 ID) 會繼續在每次點撃時一併傳送。
