---
description: 列出移動庫可以自動測量的度量和維度。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 生命週期量度
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 64%

---

# 生命週期量度{#lifecycle-metrics}

列出移動庫可以自動測量的度量和維度。

有關詳細資訊，請參見 [排除生命週期資料故障](https://helpx.adobe.com/tw/analytics/kb/troubleshoot-lifecycle-data.html)。

## 生命週期量度和維度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置後，生命週期度量將在上下文資料參數中發送到分析，在每次框調用時將參數發送到目標，並作為信號發送到Audience Manager。 分析和目標使用相同的格式，Audience Manager對每個度量使用不同的前置詞。

對於分析，每次生命週期跟蹤調用時發送的上下文資料將自動捕獲並使用下面列出的度量或維進行報告，並會記錄異常。

### 量度

* **首次啟動**

   在安裝或重新安裝後首次執行時觸發。

   * 分析上下文資料/目標參數： `a.InstallEvent`
   * Audience Manager 訊號: `c_a_InstallEvent`

* **升級**

   在升級或版本編號變更後首次執行時觸發。

   * 分析上下文資料/目標參數： `a.UpgradeEvent`
   * Audience Manager 訊號: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!TIP]
   >
   >此量度不會自動儲存至 Analytics 量度。您必須建立處理規則，設定自訂事件來擷取此量度。

   * 分析上下文資料/目標參數： `a.DailyEngUserEvent`
   * Audience Manager 訊號: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存至 Analytics 量度。您必須建立處理規則，設定自訂事件來擷取此量度。

   * 分析上下文資料/目標參數： `a.MonthlyEngUserEvent`
   * Audience Manager 訊號: `c_a_MonthlyEngUserEvent`

* **啟動**

   在每次執行時觸發，包括當機和安裝。在超過生命週期工作階段逾時的情況下，也會在從背景恢復時觸發。

   * 分析上下文資料/目標參數： `a.LaunchEvent`
   * Audience Manager 訊號: `c_a_LaunchEvent`

* **當機**

   於關閉前，應用程式不在背景執行時觸發。事件會在當機後啟動應用程式時傳送。Adobe Mobile 當機報告不會實施未攔截之例外狀況的全域處理常式。

   * 分析上下文資料/目標參數： `a.CrashEvent`
   * Audience Manager 訊號: `c_a_CrashEvent`

* **前一個作業長度**

   根據在背景中開啟應用程式的時間，報告先前的應用程式工作階段持續的秒數。

   * 分析上下文資料/目標參數： `a.PrevSessionLength`
   * Audience Manager 訊號: `c_a_PrevSessionLength`

### 維度

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 `MM/DD/YYYY`。

   * 分析上下文資料/目標： `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **應用程式 ID**

   以 `[AppName] [BundleVersion]` 格式儲存應用程式名稱和版本。以下是此格式的範例: `myapp 1.1`。

   * 分析上下文資料/目標： `a.AppID`
   * Audience Manager: `c_a_AppID`

* **啟動次數**

   應用程式啟動或在背景執行的次數。

   * 分析上下文資料/目標： `a.Launches`
   * Audience Manager: `c_a_Launches`

* **距首次使用的天數**

   自首次執行後的天數。

   * 分析上下文資料/目標： `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **上次使用間隔天數**

   距離上次使用的天數。

   * 分析上下文資料/目標： `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **小時**

   測量應用程式的啟動時數。此量度使用 24 小時數字格式，且用於時間分界，以判斷尖峰使用時間。

   * 分析上下文資料/目標： `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **星期**

   應用程式啟動的工作日數。

   * 分析上下文資料/目標： `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **作業系統版本**

   作業系統版本。

   * 分析上下文資料/目標： `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **上次升級的間隔天數**

   距應用程式版本編號上次變更的天數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * 分析上下文資料/目標： `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * 分析上下文資料/目標： `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **裝置名稱**

   儲存裝置名稱。

   * 分析上下文資料/目標： `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **電信業者名稱**

   儲存行動服務提供者的名稱，如裝置所提供。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * 分析上下文資料/目標： `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **解析度**

   寬 x 高 (以實際像素表示)。

   * 分析上下文資料/目標： `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## 其他行動量度和維度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下度量和維通過說明中列出的方法在移動解決方案變數中捕獲。

### 量度

* **動作時間總計**

   由 `trackTimedAction` 方法填入。

   * 分析上下文資料/目標參數： `a.action.time.total`
   * Audience Manager特徵： `c_a_action_time_total`

* **應用程式中的動作時間**

   由 `trackTimedAction` 方法填入。

   * 分析上下文資料/目標參數： `a.action.time.inapp`
   * Audience Manager特徵： `c_a_action_time_inapp`

* **期限值 (事件)**

   由 `trackLifetimeValue` 方法填入。

   * 分析上下文資料/目標參數： `a.ltv.amount`
   * Audience Manager特徵： `c_a_ltv_amount`

## 維度

* **位置 (10 公里以內)**

   由 `trackLocation` 方法填入。

   * 分析上下文資料/目標參數：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager特徵：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   由 `trackLocation` 方法填入。

   * 分析上下文資料/目標參數：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager特徵：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置 (1 公尺以內)**

   由 `trackLocation` 方法填入。

   * 分析上下文資料/目標參數：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager特徵：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **興趣點名稱**

   填充者 `trackLocation` 方法當設備在已定義的POI內時。

   * 分析上下文資料/目標參數： `a.loc.poi`
   * Audience Manager特徵： `c_a_loc_poi`

* **至興趣點中心的距離**

   填充者 `trackLocation` 方法當設備在已定義的POI內時。

   * 分析上下文資料/目標參數： `a.loc.dist`
   * Audience Manager特徵： `c_a_loc_dist`

* **期限值 (轉換變數)**

   由 `trackLifetimeValue` 方法填入。

   * 分析上下文資料/目標參數： `a.ltv.amount`
   * Audience Manager特徵： `c_a_ltv_amount`
