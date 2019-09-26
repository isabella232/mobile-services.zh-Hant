---
description: 新增程式庫至專案後，就可隨處在您的應用程式中執行任何 Analytics 方法呼叫 (請務必匯入 ADBMobile.h 至類別)。
seo-description: 新增程式庫至專案後，就可隨處在您的應用程式中執行任何 Analytics 方法呼叫 (請務必匯入 ADBMobile.h 至類別)。
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

新增程式庫至專案後，就可隨處在您的應用程式中執行任何 Analytics 方法呼叫 (請務必匯入 ADBMobile.h 至類別)。

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

在新增程式碼之前，請要求您的 Analytics 管理員完成下列步驟，以啟用行動應用程式生命週期追蹤。如此一來可確保報表套裝在您開始開發時已準備好擷取量度。


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## 收集生命週期度量 {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   例如:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. SDK 會在應用程式關閉時設定標記，表示應用程式已成功退出。If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


If you've looked at the ADBMobile Class and Method Reference, you are probably wondering where to set events, eVars, props, heirs, and lists. [](/help/blackberry/methods.md)在第 4 版中，您已無法在應用程式中直接指派那些變數類型。SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至應用程式商店。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在透過處理規則對應前，都不會出現在報表中。

任何您直接指派給變數的值，應已改為新增至 `data` HashMap。

## 處理規則 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

處理規則是用來複製您在內容資料變數中傳送至 eVar、prop 及其他變數的資料以進行報告。

2013 年峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)

[處理規則](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[獲得使用處理規則的授權](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我們建議您使用命名空間為內容資料變數分組，可協助您維持邏輯排序。例如，若您想要收集產品資訊，將需要定義以下變數:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

內容資料變數在處理規則介面中按字母排序，讓您快速了解哪些變數在同一個命名空間中。

此外，我們聽說有部分人員使用 eVar 或 prop 編號來命名內容資料鍵值:

```js
"eVar1":"jimbo"
```

這樣可協助您在處理規則中執行一次性對應時變得&#x200B;*較為*&#x200B;容易，但在偵錯時會失去易讀性，使日後的程式碼更新變得更困難。因此，我們強烈建議您為鍵值和值使用描述性名稱:

```js
"username":"jimbo"
```

定義計數器事件的內容變數可以具有相同的鍵值和值:

```js
"logon":"logon"
```

定義增量器事件的內容資料變數可以將事件作為鍵值，並將遞增的量作為值:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe reserves the namespace . `a.`除了此微小限制之外，您登入公司中的內容資料變數必須是唯一的以避免衝突。

## Enable offline tracking {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

在啟用離線追蹤前，請特別留意設定檔案參考中所說明的時間戳記需求。

## 分析方法

For a list of the Analytics methods that are available for BlackBerry, see Analytics methods in Adobe Mobile Class and Method Reference.**[](/help/blackberry/methods.md)