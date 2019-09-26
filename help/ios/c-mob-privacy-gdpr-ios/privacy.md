---
description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-title: 設定使用者的選擇狀態
solution: Marketing Cloud,Analytics
title: 設定使用者的選擇狀態
topic: 開發人員和實施
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

本資訊可協助您處理 GDPR 資料刪除請求。

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

您可以透過下列設定，控制裝置上是否允許 Analytics、Target 及 Audience Manager 活動:

* `privacyDefault` in [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

   此設定會控制持續使用的初始設定，直到在程式碼中變更為止。

* `setPrivacyStatus`方法。

   透過此方法變更隱私權設定後，此變更會永久生效，直到您使用此方法再次變更，或解除安裝並再次安裝應用程式為止。

   如需這些方法的詳細資訊，請參閱 [設定方法](/help/ios/configuration/json-config/json-config.md).

Here is information about each privacy status:

* **選擇加入**

   * Analytics: 會傳送點擊。
   * Target: 會傳送 mbox 要求。
   * Audience Manager: 會傳送訊號和 ID 同步。
   * Value in the JSON config file: `optedin`
   * Value in : `setPrivacyStatus``ADBMobilePrivacyStatusOptIn`

* **選擇退出**

   * Analytics: 會捨棄點擊。
   * Target: 不允許 mbox 要求。
   * Audience Manager: 不允許訊號和 ID 同步。
   * Value in the JSON config file: `optedout`
   * Value in : `setPrivacyStatus``ADBMobilePrivacyStatusOptOut`

* **未知**

   * Analytics: 如果&#x200B;**已**&#x200B;啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果&#x200B;**沒有**&#x200B;啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * Target: 會傳送 mbox 要求。
   * Audience Manager: 會傳送訊號和 ID 同步。
   * Value in the JSON config file: `optunknown`
   * Value in : `setPrivacyStatus``ADBMobilePrivacyStatusUnknown`

## 範例 {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

