---
description: '下列為 iOS 資料庫提供的贏取方法 '
seo-description: '下列為 iOS 資料庫提供的贏取方法 '
seo-title: 贏取方法
solution: Marketing Cloud、Analytics
title: 贏取方法
uuid: 6f88de57-793d-4d33-9a54-f6714289 d2 c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

下列為 iOS 資料庫提供的贏取方法:

支援下列方法：

* **acquisitionCampaignStartForApp:data:**

   就像使用者已按一下連結，讓開發者得以展開應用程式贏取促銷活動。此方法有助於建立手動贏取連結，並且可由您將應用程式商店重新導向，例如使用 `SKStoreView`。

   * 以下是此方法的語法:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


