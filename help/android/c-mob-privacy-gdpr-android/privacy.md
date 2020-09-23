---
description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-description: 本資訊可協助您處理 GDPR 資料刪除請求。
seo-title: 設定使用者的選擇狀態
solution: Experience Cloud,Analytics
title: 設定使用者的選擇狀態
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 67%

---


# 設定使用者的選擇狀態{#setting-the-user-s-opt-status}

本資訊可協助您處理 GDPR 資料刪除請求。

>[!IMPORTANT]
>
>從 Android SDK 4.15 版開始，若將隱私權狀態設定為`unknown`，將保留 Audience Manager 與 Experience Cloud ID 點撃。

您可以透過下列設定，控制裝置上是否允許 Analytics、Target 及 Audience Manager 活動:

* [ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)中的 `privacyDefault`。

   此設定會控制持續使用的初始設定，直到在程式碼中變更為止。

* `Config.setPrivacyStatus` 方法。

   使用此方法變更隱私權設定後，這項變更仍然有效，直到您再次變更或解除安裝並再次安裝應用程式為止。 有關這些方法的詳細資訊，請參 [閱配置方法](/help/android/configuration/methods.md)。

以下表格說明了各個隱私權狀態:

* **選擇加入**

   * **Analytics**:會傳送點擊。
   * **目標**:Mbox請求會傳送。
   * **Audience Manager**:會傳送訊號和ID同步。
   * JSON 設定檔案中的值: `optedin`
   * `setPrivacyStatus` 中的值: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **選擇退出**

   * **Analytics**:會捨棄點擊。
   * **目標**:不允許Mbox請求。
   * **Audience Manager**:不允許信號和ID同步。
   * JSON 設定檔案中的值: `optedout`
   * `setPrivacyStatus` 中的值: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **未知**

   * **Analytics**: 如果&#x200B;**已啟用**&#x200B;離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果<b>沒有</b>啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   * **目標**:Mbox請求會傳送。
   * **Audience Manager**:會傳送訊號和ID同步。
   * JSON 設定檔案中的值: `optunknown`
   * `setPrivacyStatus` 中的值: `MOBILE_PRIVACY_STATUS_UNKNOWN`

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

