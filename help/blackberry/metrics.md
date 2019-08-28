---
description: 在實施生命週期並連結至疑難排解生命週期資料後，行動資料庫即可自動測量量度和維度。
keywords: Android；資料庫；行動；sdk
seo-description: 在實施生命週期並連結至疑難排解生命週期資料後，行動資料庫即可自動測量量度和維度。
seo-title: 生命週期量度
solution: Marketing Cloud、Analytics
title: 生命週期量度
topic: 開發人員和實施
uuid: 5a371f11-6521-410f-a01 f-fc3 b280 b050 f
translation-type: tm+mt
source-git-commit: 6c440c2130781943796cdfb581a39a8167f5ba13

---


# Lifecycle metrics {#lifecycle-metrics}

在實施生命週期並連結至疑難排解生命週期資料後，行動資料庫即可自動測量量度和維度。

如需詳細資訊，請前往知識庫的[疑難排解生命週期資料](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定後，生命週期量度會在內容資料參數中傳送至 Analytics、隨著每次 mbox 呼叫傳送在參數中傳送至 Target，並以訊號形式傳送至對象管理。Analytics 和 Target 會使用相同格式，而觀眾管理則對每個量度使用不同的首碼。

對於Analytics，會自動擷取與每個生命週期追蹤呼叫一起傳送的上下文資料，並使用度量或維度來報告。

### 量度

* **a.media.name**

   在安裝或重新安裝後首次執行時觸發。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **升級**

   在升級或版本編號變更後首次執行時觸發。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!IMPORTANT]
   >
   >此度量不會自動儲存在Analytics量度中。您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。&gt;&gt;&gt;&gt;

   >[!IMPORTANT]
   >
   >此度量不會自動儲存在Analytics量度中。您必須建立處理規則，設定自訂事件來擷取此量度。

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

   安裝後首次啟動的日期。日期格式 `MM/DD/YYYY`為。

   * Analytics context data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **應用程式 ID**

   以下列格式儲存應用程式名稱和版本:
   `[AppName] [BundleVersion]`。

   以下是此格式的範例: `myapp 1.1`。

   * Analytics context data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **啟動次數**

   應用程式啟動或在背景執行的次數。

   * Analytics context data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **距首次使用的天數**

   自首次執行後的天數。

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **上次使用間隔天數**

   距離上次使用的天數。

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **小時**

   測量應用程式的啟動時數。此量度使用 24 小時數字格式，且用於時間分界，以判斷尖峰使用時間。

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **星期**

   應用程式啟動的工作日數。

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **作業系統版本**

   作業系統的版本。

   * Analytics context data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **上次升級的間隔天數**

   距應用程式版本編號上次變更的天數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **裝置名稱**

   儲存裝置名稱。

   * Analytics context data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **電信業者名稱**

   儲存行動服務提供者的名稱，如裝置所提供。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics context data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **解析度**

   寬 x 高 (以實際像素表示)。

   * Analytics context data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

下列度量和維度會依列出的方法在行動解決方案變數中擷取。

* **位置 (10 公里以內)**

   Populated by `trackLocation` methods.

   * Analytics上下文資料/Target參數：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * 觀眾管理特徵：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   Populated by `trackLocation` methods.

   * Analytics上下文資料/Target參數：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * 觀眾管理特徵：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置 (1 公尺以內)**

   Populated by `trackLocation` methods.

   * Analytics上下文資料/Target參數：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * 觀眾管理特徵：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **興趣點名稱**

   當裝置處於定義地標範圍內時由 `trackLocation` 方法填入。

   * Analytics上下文資料/Target參數：

      * `a.loc.poi`
   * 觀眾管理特徵：

      * `c_a_loc_poi`


* **至興趣點中心的距離**

   當裝置處於定義地標範圍內時由 `trackLocation` 方法填入。

   * Analytics上下文資料/Target參數：

      * `a.loc.dist`
   * 觀眾管理特徵：

      * `c_a_loc_dist`
