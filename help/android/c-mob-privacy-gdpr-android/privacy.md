---
description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-title: 設定使用者的選擇狀態
solution: Marketing Cloud,Analytics
title: 設定使用者的選擇狀態
topic: 開發人員和實施
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

本資訊可協助您處理 GDPR 資料刪除請求。

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

您可以透過下列設定，控制裝置上是否允許 Analytics、Target 及 Audience Manager 活動:

* `privacyDefault` 在 [ADBMobile JSON設定中](/help/android/configuration/json-config/json-config.md)。

   此設定會控制持續使用的初始設定，直到在程式碼中變更為止。

* 方 `Config.setPrivacyStatus` 法。

   透過此方法變更隱私權設定後，此變更會持續生效，直到您再次變更或解取安裝並再次安裝應用程式為止。如需這些方法的詳細資訊，請參閱 [設定方法](/help/android/configuration/methods.md).

以下表格說明了各個隱私權狀態:

* **選擇加入**

   * **Analytics**: 會傳送點擊。
   * **Target**: 會傳送 mbox 要求。
   * **Audience Manager**: 會傳送訊號和 ID 同步。
   * Value in the JSON Config file: `optedin`
   * 值(在 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **選擇退出**

   * **Analytics**: 會捨棄點擊。
   * **Target**: 不允許 mbox 要求。
   * **Audience Manager**: 不允許訊號和 ID 同步。
   * Value in the JSON config file: `optedout`
   * 值(在 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **未知**

   * **Analytics**:如果啟用離 **線追蹤**，則會儲存點擊，直到隱私權狀態變更為選擇加入（傳送點擊）或選擇退出（捨棄點擊）為止。

      如果<b>沒有</b>啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   * **Target**: 會傳送 mbox 要求。
   * **Audience Manager**: 會傳送訊號和 ID 同步。
   * Value in the JSON config file: `optunknown`
   * 值(在 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## 範例 {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

