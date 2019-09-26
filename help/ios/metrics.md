---
description: 下表列出的量度與維度，可在生命週期實施後由行動資料庫自動進行測量。
seo-description: 下表列出的量度與維度，可在生命週期實施後由行動資料庫自動進行測量。
seo-title: 生命週期量度
solution: Marketing Cloud,Analytics
title: 生命週期量度
topic: 開發人員和實施
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lifecycle metrics {#lifecycle-metrics}

以下是實施生命週期後，行動程式庫可自動測量的度量和維度。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定生命週期量度後，量度會在內容資料參數中傳送至 Analytics、隨著每次 mbox 呼叫在參數中傳送至 Target，並以訊號形式傳送至 Audience Manager。Analytics 和 Target 會使用相同格式，而 Audience Manager 則對每個量度使用不同的首碼。

對於 Analytics，系統會自動擷取隨著每個生命週期追蹤呼叫傳送的內容資料，並使用第一欄中列出的量度或維度回報。

>[!TIP]
>
>說明中提供例外。

### 量度

* **首次啟動**

   在安裝或重新安裝後首次執行時觸發。

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **升級**

   在升級或只要版本編號變更後首次執行時觸發。

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **啟動**

   在每次執行時觸發，包括損毀和安裝。當超出生命週期工作階段逾時期間後，應用程式從背景繼續執行時也會觸發。

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **當機**

   於關閉前，應用程式不在背景執行時觸發。事件會在當機後再度啟動應用程式時傳送。Adobe Mobile 當機報告不會實施未攔截之例外狀況的全域處理常式。

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **前一個作業長度**

   根據在背景中開啟應用程式的時間，報告先前的應用程式工作階段持續的秒數。

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> The Daily Engaged Users and Monthly Engaged Users metrics are not automatically stored in an Analytics metric. **** You must create a processing rule that sets a custom event to capture these metrics.

### 維度

* **安裝日期**

   安裝後首次啟動的日期。The date format is .`MM/DD/YYYY`

   * Analytics 上下文資料/目標: `a.InstallDate`
   * 讀者管理: `c_a_InstallDate`

* **應用程式 ID**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. 例如, `myapp 1.1`.

   * Analytics 上下文資料/目標: `a.AppID`
   * 讀者管理: `c_a_AppID`

* **啟動次數**

   應用程式啟動或在背景執行的次數。

   * Analytics 上下文資料/目標: `a.Launches`
   * 讀者管理: `c_a_Launches`

* **距首次使用的天數**

   自首次執行起的天數。

   * Analytics 上下文資料/目標: `a.DaysSinceFirstUse`
   * 讀者管理: `c_a_DaysSinceFirstUse`

* **上次使用間隔天數**

   距離上次使用的天數。

   * Analytics 上下文資料/目標: `a.DaysSinceLastUse`
   * 讀者管理: `c_a_DaysSinceLastUse`

* **小時**

   測量應用程式的啟動時數，並使用 24 小時數字格式。用於時間分界，以判斷尖峰使用時間。

   * Analytics 上下文資料/目標: `a.HourOfDay`
   * 讀者管理: `c_a_HourOfDay`

* **星期**

   應用程式啟動的工作日數。

   * Analytics 上下文資料/目標: `a.DayOfWeek`
   * 讀者管理: `c_a_DayOfWeek`

* **作業系統版本**

   距應用程式版本編號上次變更的天數。

   * Analytics 上下文資料/目標: `a.OSVersion`
   * 讀者管理: `c_a_OSVersion|OS version`

* **上次升級的間隔天數**

   上次升級的間隔天數.

   * Analytics 上下文資料/目標: `a.DaysSinceLastUpgrade`
   * 讀者管理: `c_a_DaysSinceLastUpgrade`

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   * Analytics 上下文資料/目標: `a.LaunchesSinceUpgrade`
   * 讀者管理: `c_a_LaunchesSinceUpgrade`

* **裝置名稱**

   儲存裝置名稱。以逗號分隔的兩位數字串，用以識別 iOS 裝置。第一個數字通常代表裝置代別，第二個數字通常提供裝置系列的不同成員版本。如需常見裝置名稱清單，請參閱  iOS 裝置版本.

   * Analytics 上下文資料/目標: `a.DeviceName`
   * 讀者管理: `c_a_DeviceName`

* **電信業者名稱**

   儲存行動服務提供者的名稱，如裝置所提供。

   * Analytics 上下文資料/目標: `a.CarrierName`
   * 讀者管理: `c_a_CarrierName`

* **解析度**

   寬 x 高 (以實際像素表示)。

   * Analytics 上下文資料/目標: `a.Resolution`
   * 讀者管理: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >「上 *次升級後的天數*」、「上次升級後的啟動次數 *」和「電信業者名稱*** 」維度不會自動儲存在Analytics變數中。 您必須建立處理規則，將值複製至Analytics變數以用於報告。


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

The following metrics and dimensions are captured in mobile solution variables by the listed method.

### 量度

* **動作時間總計**

   由 trackTimedAction 方法填入。

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **應用程式中的動作時間**

   由 trackTimedAction 方法填入。

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **期限值 (事件)**

   由 trackLifetimeValue 方法填入。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### 維度

* **位置 (10 公里以內)**

   Populated by `trackLocation` methods.

   * Analytics上下文資料/Target參數：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * 觀眾管理特徵：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   由 trackLocation 方法填入。

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

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **至興趣點中心的距離**

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **期限值 (轉換變數)**

   由 trackLifetimeValue 方法填入。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **追蹤代碼**

   由「行動應用程式贏取」填入。由 Adobe Mobile Services 自動產生。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **促銷活動**

   行銷活動名稱，亦儲存於行銷活動變數中。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **促銷活動內容**

   顯示連結的內容名稱或 ID。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **促銷活動媒體**

   行銷媒體，例如橫幅或電子郵件。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **促銷活動來源**

   原始轉介來源，例如電子報或社交媒體網路。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **促銷活動詞語**

   您想要以此贏取追蹤的付費關鍵字或其他詞語。由「行動應用程式贏取」填入。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
