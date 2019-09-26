---
description: 這是預設行動量度和維度的參考資訊。
keywords: 行動
seo-description: 這是預設行動量度和維度的參考資訊。
seo-title: Mobile 量度和維度參考
solution: Marketing Cloud,Analytics
title: Mobile 量度和維度參考
topic: 量度
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

這些資訊可協助您進一步瞭解預設行動量度和維度。

>[!TIP]
>
>The dimension and metric permissions that are set in Adobe Analytics apply to Mobile Services. 當您嘗試執行沒有適當權限的報表時，會發生錯誤。

## 量度 {#section_6704C815147D44AF96151D626BEB813C}

以下是預設行動量度的清單：

* **首次啟動**

   安裝或重新安裝後第一次執行時觸發。

* **升級**

   升級或版本編號變更後第一次執行時觸發。

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!TIP]
   >The Daily Engaged Users event is not automatically stored in an Analytics metric. 您必須建立處理規則，設定自訂事件來擷取此量度。

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   >[!TIP]
   >The Monthly Engaged Users event is not automatically stored in an Analytics metric. 您必須建立處理規則，設定自訂事件來擷取此量度。

* **啟動**

   在非安裝或升級情況下的任何執行時觸發。這也會在應用程式在背景執行時觸發。依預設，如果應用程式在背景執行達 5 分鐘以上，就會觸發新的啟動。The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. 如需詳細資訊，請參 *閱「設定SDK分析選項」中的*[「作業逾時（秒）」列](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)。

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. 如需詳細資訊，請參閱[比較造訪數和行動應用程式啟動數](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html)。

* **當機**

   應用程式未正常退出時觸發。此事件會在應用程式當機後開啟時傳送。

   >[!TIP]
   >如果未呼叫quit，應用程式會被視為當機。

* **工作階段長度總計**

   累積總工作階段長度。

## 維度 {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

以下是預設行動維度的清單：

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 *MM/DD/YYYY*。

* **應用程式 ID**

   以下列格式儲存應用程式名稱和版本: `[AppName] [BundleVersion]`. 例如, `myapp 1.1`.

* **啟動次數**

   應用程式啟動或在背景執行的次數。

* **首次使用後間隔天數**

   自首次執行後的天數。

* **上次使用後間隔天數**

   距離上次使用的天數。

* **小時**

   計算應用程式啟動的時間 (小時)，採用 24 小時單位制。此維度也會用於計算離開的時間，以判斷尖峰使用期間。

* **星期**

   應用程式啟動的工作日數。

* **作業系統**

   裝置的作業系統。

* **作業系統版本**

   作業系統版本。

* **上次升級後間隔天數**

   距應用程式版本編號上次變更的天數。

   >[!TIP]
   >
   >上次升級後的天數不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!TIP]
   >
   >自上次升級後啟動不會自動儲存在Analytics變數中。 您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

* **裝置名稱**

   儲存裝置名稱。在iOS中，逗號分隔的兩位數字串會識別iOS裝置。 第一數字代表裝置產生，第二數字則代表裝置系列的不同成員。 如需常用裝置名稱的完整清單，請參閱 [iOS 裝置版本](/help/ios/reference/device-versions.md)。

* **電信業者名稱**

   儲存行動服務提供商的名稱。

* **解析度**

   寬和高 (以實際像素表示)。
