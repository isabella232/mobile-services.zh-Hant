---
description: 本資訊可協助您處理 GDPR 資料刪除請求。
solution: Experience Cloud,Analytics
title: 設定使用者的選擇狀態
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# 設定使用者的選擇狀態 {#setting-the-user-s-opt-status}

本資訊可協助您處理 GDPR 資料刪除請求。

>[!IMPORTANT]
>
>從 Experience Cloud iOS SDK 4.15 版開始，若將隱私權狀態設定為`unknown`，將保留 Audience Manager 與 Experience Cloud ID 點撃。

您可以透過下列設定，控制裝置上是否允許 Analytics、Target 及 Audience Manager 活動:

* [ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)中的 `privacyDefault`。

   此設定會控制持續使用的初始設定，直到在程式碼中變更為止。

* `setPrivacyStatus`方法。

   使用此方法變更隱私權設定後，變更會是永久性的，除非您使用此方法再次變更，或是您解除安裝應用程式並再次安裝。

   如需這些方法的詳細資訊，請參閱[設定方法](/help/ios/configuration/json-config/json-config.md)。

以下是有關各個隱私權狀態的資訊:

* **選擇加入**

   * Analytics: 會傳送點擊。
   * Target: 會傳送 mbox 要求。
   * Audience Manager: 會傳送訊號和 ID 同步。
   * JSON 設定檔案中的值: `optedin`
   * `setPrivacyStatus` 中的值: `ADBMobilePrivacyStatusOptIn`

* **選擇退出**

   * Analytics: 會捨棄點擊。
   * Target: 不允許 mbox 要求。
   * Audience Manager: 不允許訊號和 ID 同步。
   * JSON 設定檔案中的值: `optedout`
   * `setPrivacyStatus` 中的值: `ADBMobilePrivacyStatusOptOut`

* **未知**

   * Analytics: 如果&#x200B;**已**&#x200B;啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果&#x200B;**沒有**&#x200B;啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * Target: 會傳送 mbox 要求。
   * Audience Manager: 會傳送訊號和 ID 同步。
   * JSON 設定檔案中的值: `optunknown`
   * `setPrivacyStatus` 中的值: `ADBMobilePrivacyStatusUnknown`

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
