---
description: Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-description: Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience CloudID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 100%

---

# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service 提供跨 Experience Cloud 解決方案的通用訪客 ID。Analytics 需要 ID 服務才能使用 Target、視訊心率以及日後的Experience Cloud 整合。

>[!TIP]
>
>除非您使用 Adobe Experience Platform Identity Service，否則無須填入 Experience Cloud ID。如需詳細資訊，請參閱 [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/zh-Hant/id-service/using/home.html)。

**需要 SDK 4.3 版或更新版本**

## 啟用 Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的專案*。
1. 匯入資料庫：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含 `marketingCloud` `org`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 組織 ID 會不重複識別 Adobe Experience Cloud 中的每一間客戶公司，其格式與以下值類似：`016D5C175213CCA80A490D05@AdobeOrg`。

   >[!IMPORTANT]
   >
   >您必須包含 `@AdobeOrg`。

   如果這些值不存在，請從 Adobe Mobile Services 下載更新的 `ADBMobileConfig.json` 檔案。如需詳細資訊，請參閱 [ADBMobile JSON 設定](/help/ios/getting-started/requirements.md)。

設定後，系統會產生一組 Experience Cloud ID，並包含在所有點撃中。其他訪客 ID (例如自訂和自動產生的 ID) 會繼續在每次點撃時一併傳送。
