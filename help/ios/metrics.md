---
description: 下表列出可在生命週期實施後由行動資料庫自動進行測量的量度與維度。
seo-description: 下表列出可在生命週期實施後由行動資料庫自動進行測量的量度與維度。
seo-title: 生命週期量度
solution: Experience Cloud,Analytics
title: 生命週期量度
topic-fix: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
exl-id: b51b6c41-843f-499d-9cf2-7ce96ed82fc0
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 100%

---

# 生命週期量度 {#lifecycle-metrics}

以下是可在生命週期實施後由行動資料庫自動進行測量的量度與維度。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Experience Platform Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 生命週期量度和維度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定生命週期量度後，量度會在內容資料參數中傳送至 Analytics、隨著每次 mbox 呼叫在參數中傳送至 Target，並以訊號形式傳送至 Audience Manager。Analytics 和 Target 會使用相同格式，而 Audience Manager 則對每個量度使用不同的首碼。

對於 Analytics，系統會自動擷取隨著每個生命週期追蹤呼叫傳送的內容資料，並使用第一欄中列出的量度或維度回報。

>[!TIP]
>
>說明中提供者例外。

### 量度

* **首次啟動**

   在安裝或重新安裝後首次執行時觸發。

   * Analytics 內容資料/目標參數: `a.InstallEvent`
   * Audience Manager 訊號: `c_a_InstallEvent`

* **升級**

   在升級或只要版本編號變更後首次執行時觸發。

   * Analytics 內容資料/目標參數: `a.UpgradeEvent`
   * Audience Manager 訊號: `c_a_UpgradeEvent`

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   * Analytics 內容資料/目標參數: `a.DailyEngUserEvent`
   * Audience Manager 訊號: `c_a_DailyEngUserEvent`

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   * Analytics 內容資料/目標參數: `a.MonthlyEngUserEvent`
   * Audience Manager 訊號: `c_a_MonthlyEngUserEvent`

* **啟動**

   在每次執行時觸發，包括損毀和安裝。在超過生命週期工作階段逾時後，也會在應用程式從背景恢復時觸發。

   * Analytics 內容資料/目標參數: `a.LaunchEvent`
   * Audience Manager 訊號: `c_a_LaunchEvent`

* **當機**

   於關閉前，應用程式不在背景執行時觸發。事件會在當機後再度啟動應用程式時傳送。Adobe Mobile 當機報告不會實施未攔截之例外狀況的全域處理常式。

   * Analytics 內容資料/目標參數: `a.CrashEvent`
   * Audience Manager 訊號: `c_a_CrashEvent`

* **前一個作業長度**

   根據在背景中開啟應用程式的時間，報告先前的應用程式工作階段持續的秒數。

   * Analytics 內容資料/目標參數: `a.PrevSessionLength`
   * Audience Manager 訊號: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> *每日參與使用者*&#x200B;與&#x200B;*每月參與使用者*&#x200B;量度不會自動儲存至 Analytics 量度。您必須建立處理規則，設定自訂事件來擷取這些量度。

#### 維度

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 `MM/DD/YYYY`。

   * Analytics 上下文資料/目標: `a.InstallDate`
   * 讀者管理: `c_a_InstallDate`

* **應用程式 ID**

   以 `[AppName] [BundleVersion]` 格式儲存應用程式名稱和版本。例如, `myapp 1.1`.

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

   計算應用程式啟動的時間 (小時)，採用 24 小時制。用於時間分界，以判斷尖峰使用時間。

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

   儲存裝置名稱。以逗號分隔的雙位數字串，用以識別 iOS 裝置。第一個數字通常代表裝置代別，第二個數字通常提供裝置系列的不同成員版本。如需常見裝置名稱清單，請參閱      iOS 裝置版本.

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
   >*上次升級的間隔天數*、*上次升級後啟動次數*&#x200B;以及&#x200B;*電信業者名稱*&#x200B;維度不會自動儲存至 Analytics 變數。您必須建立處理規則，將這些值複製到 Analytics 變數以進行報告。


## 其他行動量度和維度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

系統會使用列出的方法，在行動解決方案變數中擷取以下量度和維度。

### 量度

* **動作時間總計**

   由 trackTimedAction 方法填入。

   * Analytics 內容資料/目標參數: `a.action.time.total`
   * Audience Management 特徵: `c_a_action_time_total`

* **應用程式中的動作時間**

   由 trackTimedAction 方法填入。

   * Analytics 內容資料/目標參數: `a.action.time.inapp`
   * Audience Management 特徵: `c_a_action_time_inapp`

* **期限值 (事件)**

   由 trackLifetimeValue 方法填入。

   * Analytics 內容資料/目標參數: `a.ltv.amount`
   * Audience Management 特徵: `c_a_ltv_amount`


### 維度

* **位置 (10 公里以內)**

   由 `trackLocation` 方法填入。

   * Analytics 內容資料/目標參數:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management 特徵: 

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置 (100 公尺以內)**

   由 trackLocation 方法填入。

   * Analytics 內容資料/目標參數:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management 特徵:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置 (1 公尺以內)**

   由 `trackLocation` 方法填入。

   * Analytics 內容資料/目標參數:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Management 特徵:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **興趣點名稱**

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics 內容資料/目標參數: `a.loc.poi`
   * Audience Management 特徵: `c_a_loc_poi`

* **至興趣點中心的距離**

   當裝置處於定義地標範圍內時由 trackLocation 方法填入。

   * Analytics 內容資料/目標參數: `a.loc.dist`
   * Audience Management 特徵: `c_a_loc_dist`

* **期限值 (轉換變數)**

   由 trackLifetimeValue 方法填入。

   * Analytics 內容資料/目標參數: `a.ltv.amount`
   * Audience Management 特徵: `c_a_ltv_amount`

* **追蹤代碼**

   由「行動應用程式贏取」填入。由 Adobe Mobile Services 自動產生。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.trackingcode`
   * Audience Management 特徵: `c_a_referrer_campaign_trackingcode`

* **促銷活動**

   行銷活動名稱，亦儲存於行銷活動變數中。由「行動應用程式贏取」填入。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.name`
   * Audience Management 特徵: `c_a_referrer_campaign_name`

* **促銷活動內容**

   顯示連結之內容的名稱或 ID。由「行動應用程式贏取」填入。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.content`
   * Audience Management 特徵: `c_a_referrer_campaign_content`

* **促銷活動媒體**

   行銷媒體，例如橫幅或電子郵件。由「行動應用程式贏取」填入。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.medium`
   * Audience Management 特徵: `c_a_referrer_campaign_medium`

* **促銷活動來源**

   原始反向連結，例如電子報或社交媒體網路。由「行動應用程式贏取」填入。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.source`
   * Audience Management 特徵: `c_a_referrer_campaign_source`

* **促銷活動詞語**

   您要對此贏取追蹤的付費關鍵字或其他詞語。由「行動應用程式贏取」填入。

   * Analytics 內容資料/目標參數: `a.referrer.campaign.term`
   * Audience Management 特徵: `c_a_referrer_campaign_term`
