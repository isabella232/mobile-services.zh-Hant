---
description: 在實施生命週期並連結至疑難排解生命週期資料後，行動資料庫即可自動測量量度和維度。
keywords: android;library;mobile;sdk
seo-description: 在實施生命週期並連結至疑難排解生命週期資料後，行動資料庫即可自動測量量度和維度。
seo-title: 生命週期量度
solution: Marketing Cloud,Analytics
title: 生命週期量度
topic: 開發人員和實施
uuid: a8f3ebac-be3b-4948-82bb-105d46cff6d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Lifecycle metrics{#lifecycle-metrics}

本節提供行動程式庫在實施生命週期後可自動測量的量度和維度，以及疑難排解生命週期資料的連結。 如需疑難排解的詳細資訊，請前往「疑難排解 [生命週期」資料](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)。

## 全新Adobe Experience Platform Mobile SDK版本

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始，請前往Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定後，生命週期量度會在內容資料參數中傳送至 Analytics、隨著每次 mbox 呼叫傳送在參數中傳送至 Target，並以訊號形式傳送至對象管理。Analytics 和 Target 會使用相同格式，而觀眾管理則對每個量度使用不同的首碼。

對於Analytics，每次生命週期追蹤呼叫所傳送的上下文資料會使用量度或維度自動擷取並報告，並記錄例外情況。

### 量度

* **首次啟動**

   在安裝或重新安裝後首次執行時觸發。

   * Analytics 上下文資料/目標參數: `a.InstallEvent`
   * Audience Manager 訊號: `c_a_InstallEvent`

* **升級**

   在升級或版本編號變更後首次執行時觸發。

   * Analytics 上下文資料/目標參數: `a.UpgradeEvent`
   * Audience Manager 訊號: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics量度中。 您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics 上下文資料/目標參數: `a.DailyEngUserEvent`
   * Audience Manager 訊號: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics量度中。 您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics 上下文資料/目標參數: `a.MonthlyEngUserEvent`
   * Audience Manager 訊號: `c_a_MonthlyEngUserEvent`

* **啟動**

   在每次執行時觸發，包括損毀和安裝。當超出生命週期工作階段逾時，也會在從背景繼續時觸發。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics量度中。 您必須建立處理規則，設定自訂事件來擷取此量度。

   * Analytics 上下文資料/目標參數: `a.LaunchEvent`
   * Audience Manager 訊號: `c_a_LaunchEvent`

* **當機**

   於關閉前，應用程式不在背景執行時觸發。事件會在當機後啟動應用程式時傳送。Adobe Mobile 當機報告不會實施未攔截之例外狀況的全域處理常式。

   * Analytics 上下文資料/目標參數: `a.CrashEvent`
   * Audience Manager 訊號: `c_a_CrashEvent`

* **前一個作業長度**

   根據在背景中開啟應用程式的時間，報告先前的應用程式工作階段持續的秒數。

   * Analytics 上下文資料/目標參數: `a.PrevSessionLength`
   * Audience Manager 訊號: `c_a_PrevSessionLength`


### 維度

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 MM/DD/YYYY。

   * Analytics 上下文資料/目標參數: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **應用程式 ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 以下是此格式的範例: `myapp 1.1`。

   * Analytics 上下文資料/目標參數: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **啟動次數**

   應用程式啟動或在背景執行的次數。

   * Analytics 上下文資料/目標參數: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **距首次使用的天數**

   自首次執行後的天數。

   * Analytics 上下文資料/目標參數: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **上次使用間隔天數**

   距離上次使用的天數。

   * Analytics 上下文資料/目標參數: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **小時**

   測量應用程式的啟動時數。此量度使用 24 小時數字格式，且用於時間分界，以判斷尖峰使用時間。

   * Analytics 上下文資料/目標參數: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **星期**

   應用程式啟動的工作日數。

   * Analytics 上下文資料/目標參數: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **作業系統版本**

   作業系統版本。

   * Analytics 上下文資料/目標參數: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **上次升級的間隔天數**

   距應用程式版本編號上次變更的天數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics 上下文資料/目標參數: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics 上下文資料/目標參數: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **裝置名稱**

   儲存裝置名稱。

   * Analytics 上下文資料/目標參數: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **電信業者名稱**

   儲存行動服務提供者的名稱，如裝置所提供。重要: 此量度不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   >[!IMPORTANT]
   >
   >此量度不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

   * Analytics 上下文資料/目標參數: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **解析度**

   寬 x 高 (以實際像素表示)。

   * Analytics 上下文資料/目標參數: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

系統會透過&#x200B;**「說明」**&#x200B;欄中所列的方法，在行動解決方案變數中擷取以下量度和維度。

### 量度

* **動作時間總計**

   Populated by `trackTimedAction` methods.

   * Analytics 上下文資料/目標參數: `a.action.time.total`
   * Audience manager特徵： `c_a_action_time_total`

* **應用程式中的動作時間**

   Populated by `trackTimedAction` methods.

   * Analytics 上下文資料/目標參數: `a.action.time.inapp`
   * Audience manager特徵： `c_a_action_time_inapp`

* **期限值 (事件)**

   Populated by `trackLifetimeValue` methods.

   * Analytics 上下文資料/目標參數: `a.ltv.amount`
   * Audience manager特徵： `c_a_ltv_amount`

### 維度

* **位置 (10 公里以內)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience manager特徵：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   由 trackLocation 方法填入。

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience manager特徵：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置 (1 公尺以內)**

   由 trackLocation 方法填入。

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience manager特徵：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **興趣點名稱**

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Audience manager特徵： `c_a_loc_poi`

* **至興趣點中心的距離**

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Audience Manager Trait: `c_a_loc_dist`

* **期限值 (轉換變數)**

   由 trackLifetimeValue 方法填入。

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

* **追蹤代碼**

   由「行動應用程式贏取」填入，並由 Adobe Mobile Services 自動產生。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience Manager Trait: `c_a_referrer_campaign_trackingcode`

* ** 促銷活動

   行銷活動名稱，亦儲存於行銷活動變數中。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Audience Manager Trait: `c_a_referrer_campaign_name`

* **促銷活動內容**

   顯示連結的內容名稱或 ID。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Audience Manager Trait: `c_a_referrer_campaign_content`

* **促銷活動媒體**

   行銷媒體，例如橫幅或電子郵件。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Audience Manager Trait: `c_a_referrer_campaign_medium`

* **促銷活動來源**

   原始轉介來源，例如電子報或社交媒體網路。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience Manager Trait: `c_a_referrer_campaign_source`

* **促銷活動詞語**

   您想要以此贏取追蹤的付費關鍵字或其他詞語。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience Manager Trait: `c_a_referrer_campaign_term`
