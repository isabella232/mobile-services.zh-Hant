---
description: 這是預設行動量度和維度的參考資訊。
keywords: mobile
seo-description: 這是預設行動量度和維度的參考資訊。
seo-title: 行動量度和維度參考
solution: Marketing Cloud,Analytics
title: 行動量度和維度參考
topic: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '637'
ht-degree: 100%

---


# 行動量度和維度參考 {#mobile-metrics-and-dimensions-reference}

這些資訊可協助您進一步了解預設行動量度和維度。

>[!TIP]
>
>在 Adobe Analytics 中設定的量度權限會套用至 Mobile Services。當您在沒有適當權限的情況下嘗試執行報表時，會發生錯誤。

## 量度 {#section_6704C815147D44AF96151D626BEB813C}

以下是預設行動量度的清單：

* **首次啟動**

   安裝或重新安裝後第一次執行時觸發。

* **升級**

   升級或版本編號變更後第一次執行時觸發。

* **每日參與使用者**

   於特定一天使用應用程式時觸發。

   >[!TIP]
   >
   >每日參與使用者事件不會自動儲存至 Analytics 量度。您必須建立處理規則，設定自訂事件來擷取此量度。

* **每月參與使用者**

   於特定月份使用應用程式時觸發。

   >[!TIP]
   >每月參與使用者事件不會自動儲存至 Analytics 量度。您必須建立處理規則，設定自訂事件來擷取此量度。

* **啟動**

   在非安裝或升級情況下的任何執行時觸發。這也會在應用程式在背景執行時觸發。依預設，如果應用程式在背景執行達 5 分鐘以上，就會觸發新的啟動。您可在「管理應用程式設定」頁面上的 **[!UICONTROL SDK 分析選項]**&#x200B;中，設定應用程式在背景執行累積多長時間後，才會觸發新的啟動。如需詳細資訊，請參閱[設定 SDK 分析選項](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)中的&#x200B;*工作階段逾時 (秒)*&#x200B;列。

   >[!IMPORTANT]
   >由於 [!UICONTROL Adobe Analytics] 中的造訪數與 [!UICONTROL Adobe Mobile Services] 中的行動應用程式啟動數計算方式不同，因此報表中呈現的結果也會有所差異。如需詳細資訊，請參閱[比較造訪數和行動應用程式啟動數](https://helpx.adobe.com/tw/analytics/kb/compare-visits-and-mobile-app-launches.html)。

* **當機**

   應用程式未正確退出時觸發。一旦應用程式於當機後啟動，就會傳送此事件。

   >[!TIP]
   >如果未呼叫 quit，系統便會將該應用程式視為當機。

* **工作階段長度總計**

   累積總工作階段長度。

## 維度 {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

以下是預設行動維度的清單：

* **安裝日期**

   安裝後首次啟動的日期。日期格式為 *YYYY/MM/DD*。

* **應用程式 ID**

   以下列格式儲存應用程式名稱和版本：`[AppName] [BundleVersion]`，例如：`myapp 1.1`。

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
   >上次升級的間隔天數不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

* **上次升級後啟動次數**

   自應用程式版本編號上次變更後的啟動次數。

   >[!TIP]
   >
   >上次升級後啟動次數不會自動儲存至 Analytics 變數。您必須建立處理規則，將此值複製到 Analytics 變數以進行報告。

* **裝置名稱**

   儲存裝置名稱。在 iOS 中，以逗號分隔的兩位數字串可識別 iOS 裝置。第一個數字代表裝置代別，第二個數字則代表裝置系列的不同成員版本。如需常用裝置名稱的完整清單，請參閱 [iOS 裝置版本](/help/ios/reference/device-versions.md)。

* **電信業者名稱**

   儲存行動服務提供商的名稱。

* **解析度**

   寬和高 (以實際像素表示)。
