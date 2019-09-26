---
description: 列出行動程式庫可自動測量的量度和維度。
keywords: android;library;mobile;sdk
seo-description: 列出行動程式庫可自動測量的量度和維度。
seo-title: 生命週期量度
solution: Marketing Cloud,Analytics
title: 生命週期量度
topic: 開發人員和實施
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics{#lifecycle-metrics}

列出行動程式庫可自動測量的量度和維度。

如需詳細資訊，請參閱「疑難排 [解生命週期資料」](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定後，生命週期量度會在內容資料參數中傳送至 Analytics、隨著每次 mbox 呼叫在參數中傳送至 Target，並以訊號形式傳送至 Audience Manager。Analytics和Target使用相同的格式，而Audience manager對每個量度使用不同的首碼。

For Analytics, the context data that is sent with each lifecycle tracking call is automatically captured in and reported on by using the metric or dimension listed below, and exceptions are noted.

### 量度

* **首次啟動**

   在安裝或重新安裝後首次執行時觸發。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **升級**

   在升級或版本編號變更後首次執行時觸發。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!TIP]
   >
   >此量度不會自動儲存在Analytics量度中。 您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics量度中。 您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **啟動**

   在每次執行時觸發，包括損毀和安裝。當超出生命週期工作階段逾時，也會在從背景繼續時觸發。

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **當機**

   於關閉前，應用程式不在背景執行時觸發。事件會在當機後啟動應用程式時傳送。Adobe Mobile 當機報告不會實施未攔截之例外狀況的全域處理常式。

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **前一個作業長度**

   根據在背景中開啟應用程式的時間，報告先前的應用程式工作階段持續的秒數。

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### 維度

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 `MM/DD/YYYY`。

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **應用程式 ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 以下是此格式的範例: `myapp 1.1`。

   * Analytics context data/Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **啟動次數**

   應用程式啟動或在背景執行的次數。

   * Analytics context data/Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **距首次使用的天數**

   自首次執行後的天數。

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **上次使用間隔天數**

   距離上次使用的天數。

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **小時**

   測量應用程式的啟動時數。此量度使用 24 小時數字格式，且用於時間分界，以判斷尖峰使用時間。

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **星期**

   應用程式啟動的工作日數。

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **作業系統版本**

   作業系統版本。

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **上次升級的間隔天數**

   距應用程式版本編號上次變更的天數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **裝置名稱**

   儲存裝置名稱。

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **電信業者名稱**

   儲存行動服務提供者的名稱，如裝置所提供。

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **解析度**

   寬 x 高 (以實際像素表示)。

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下度量和維度會依說明中所列的方法擷取到行動解決方案變數中。

### 量度

* **動作時間總計**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.total`
   * Audience manager特徵： `c_a_action_time_total`

* **應用程式中的動作時間**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Audience manager特徵： `c_a_action_time_inapp`

* **期限值 (事件)**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience manager特徵： `c_a_ltv_amount`

## 維度

* **位置 (10 公里以內)**

   Populated by `trackLocation` methods.

   * Analytics上下文資料/Target參數：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience manager特徵：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   Populated by `trackLocation` methods.

   * Analytics context data/Target parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager trait:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置 (1 公尺以內)**

   Populated by `trackLocation` methods.

   * Analytics context data/Target parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager trait:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **興趣點名稱**

   當裝置處於定義地標範圍內時由 `trackLocation` 方法填入。

   * Analytics context data/Target parameter: `a.loc.poi`
   * Audience manager特徵： `c_a_loc_poi`

* **至興趣點中心的距離**

   當裝置處於定義地標範圍內時由 `trackLocation` 方法填入。

   * Analytics context data/Target parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **期限值 (轉換變數)**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`
