---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Marketing Cloud、Analytics
title: Analytics
topic: 開發人員和實施
uuid: fa0ef6c4-c04 d-46955-9eb4-ada4 e9920 e6 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Analytics {#analytics}

將程式庫新增至專案之後，您可以在應用程式中的任何位置進行任何Analytics方法呼叫。

>[!TIP]
>
>確定您匯入 `ADBMobile.h` 至類別。

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

在新增程式碼之前，請要求您的 Analytics 管理員完成下列步驟，以啟用行動應用程式生命週期追蹤。如此一來可確保報表套裝在您開始開發時已準備好擷取量度。

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

生命週期量度現已準備好供擷取，且「行動應用程式報表」出現在行銷報表介面中的&#x200B;**「報表」**&#x200B;選單中。


### 新版本

新版本的行動應用程式報告會定期發行。新版本不會自動套用至您的報表套裝，您必須重複這些步驟以進行升級。每次新增新的 Experience Cloud 功能至應用程式時，建議您重複這些步驟以確保擁有最新配置。


## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

若要在應用程式中收集生命週期量度，請依下列範例新增呼叫至應用程式啟用的時間。


### 預設. js中的WinJS


```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# 在 App.xaml.cs 中

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### App. xaml. cpp中的C/CX

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

If `CollectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. SDK 會在應用程式關閉時設定標記，表示應用程式已成功退出。If this flag is not set, `CollectLifecyleData()` reports a crash.


## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}


如果您已查看 [「ADBMobile類別」和「方法參考」](/help/windows-appstore/c-configuration/methods.md)，您可能會懷疑如何設定事件、eVar、prop、heir和清單。在第 4 版中，您已無法在應用程式中直接指派那些變數類型。SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至應用程式商店。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在透過處理規則對應前，都不會出現在報表中。

任何您直接指派給變數的值，應已改為新增至內容資料。


## 處理規則 {#section_66EE762EEA5E4728864166201617DEBF}

處理規則是用來複製您在內容資料變數中傳送至 eVar、prop 及其他變數的資料以進行報告。

2013 年峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)

[處理規則概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[取得使用處理規則的授權](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

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

將定義計數器事件的內容變數設為 "1":

```js
"logon":"1"
```

定義增量器事件的內容資料變數可設定遞增的值:

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe保留命名空間 `a.`。除了此微小限制之外，您登入公司中的內容資料變數必須是唯一的以避免衝突。

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

若要在 *`products`* 行動SDK中設定，您必須使用特殊語法。請參閱 [產品變數](/help/windows-appstore/analytics/products/products.md)。

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md). 啓用離線追蹤前，請注意設定檔案參考中所述的時間戳記需求。

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

地理位置可讓您測量位置資料 (緯度/經度) 和預先定義的地標。Each `TrackLocation` call sends:

* 緯度/經度和 POI (若位在 `ADBMobileConfig.json` 設定檔案中所定義的 POI 內)。這些資訊會傳遞至行動解決方案變數以進行自動報告。
* 以內容資料傳遞之與中心的距離和精確度。使用處理規則擷取。

若要追蹤位置:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

如果下列 POI 被定義在 `ADBMobileConfig.json` 設定檔案中:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

當裝置位置被判斷位在定義地標的 7,000 公尺半徑內，含有 "San Francisco" 值的 `a.loc.poi` 內容資料變數會與 `TrackLocation` 點擊一併傳送。`a.loc.dist` 內容變數會以公尺為單位傳送來自定義座標的距離。

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

期限值可讓您測量每個使用者的期限值並將其設為目標。每次您以 `TrackLifetimeValueIncrease` 傳送一個值時，就會將該值新增至現有值。期限值儲存在裝置上，且可透過呼叫 `GetLifetimeValue` 隨時擷取。此值可用來儲存期限購買數、廣告檢視次數、視訊完成次數、社交分享和照片上傳數等等。

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

計時動作可讓您測量停留在應用程式內的時間，以及動作從開始到結束的總時間。SDK 會計算每個工作階段的時間量，以及跨工作階段的動作完成總時間。此可用來定義區段以比較購買所需時間、通過層級和結帳流程等動作。

* 從開始到結束期間停留在應用程式內的總秒數 (跨工作階段)
* 從開始到結束的總秒數 (時鐘時間)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
