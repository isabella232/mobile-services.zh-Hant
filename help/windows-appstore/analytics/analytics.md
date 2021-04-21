---
description: 將程式庫新增至專案後，您就可以在應用程式的任何地方進行任何Analytics方法呼叫。
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
exl-id: 1a7b32b8-731d-4ae3-9feb-dafbb7495590
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 20%

---

# Analytics {#analytics}

將程式庫新增至專案後，您就可以在應用程式的任何地方進行任何Analytics方法呼叫。

>[!TIP]
>
>請確定您將`ADBMobile.h`匯入至您的類別。

## 在Analytics {#section_F2F9234009184F20BA36B5CDE872B424}中啟用行動應用程式報表

在您新增程式碼之前，請您的Analytics管理員完成下列作業，以啟用行動應用程式生命週期追蹤。 這可確保您的報表套裝在您開始開發時，已準備好擷取量度。

1. 開啟&#x200B;**[!UICONTROL 管理工具]** > **[!UICONTROL 報表套裝]**&#x200B;並選取您的行動報表套裝。
1. 按一下「編輯設定&#x200B;**[!UICONTROL >]** > **[!UICONTROL 行動管理]** > **[!UICONTROL 行動應用報表]**」。

   ![](assets/mobile-settings.png)

1. 按一下「**[!UICONTROL 啟用最新應用程式報表」]**。

   或者，您也可以按一下「啟用行動位置追蹤」**[!UICONTROL 和「啟用背景點擊的舊版報告與歸因」]**。]****[!UICONTROL 

   ![](assets/enable-lifecycle.png)

生命週期量度現在已可供擷取，而行銷報告介面的&#x200B;**[!UICONTROL 報表]**&#x200B;功能表中會顯示行動應用報表。


### 新版本

行動應用程式報告會定期發佈新版本。 新版本不會自動套用至您的報表套裝，您必須重複這些步驟以執行升級。 每次您將新的Experience Cloud功能新增至應用程式時，我們建議您重複這些步驟，以確保您擁有最新的設定。


## 生命週期量度 {#section_532702562A7A43809407C9A2CBA80E1E}

若要在應用程式中收集生命週期度量，請在啟動應用程式時新增呼叫，如下列範例所示。


### 預設。js中的WinJS


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

### App.xaml.cs中的C#

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

### App.xaml.cpp中的C/CX

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

如果在相同作業中呼叫了兩次`CollectLifecycleData()`，則您的應用程式會在第一次呼叫後的每次呼叫上報告當機。 SDK會在應用程式關閉時設定標幟，指出成功退出。 如果未設定此標幟，`CollectLifecyleData()`會報告當機。


## 事件、Prop 以及 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}


如果您已查看[ADBMobile類別和方法參考](/help/windows-appstore/c-configuration/methods.md)，您可能會想知道在何處設定事件、eVar、prop、繼承和清單。 在第4版中，您無法再直接在應用程式中指派這些類型的變數。 SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則提供您幾項優點：

* 您可以直接變更資料對應，而無須將更新提交至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在使用處理規則對應之前，不會出現在報表中。

您直接指派給變數的任何值，應改為新增至上下文資料。


## 處理規則 {#section_66EE762EEA5E4728864166201617DEBF}

處理規則可用來將您在上下文資料變數中傳送的資料複製到evar、prop和其他變數，以供報告。

2013 年高峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)

[處理規則概觀](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[取得授權以使用處理規則](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我們建議您使用「名稱空間」將上下文資料變數分組，因為這有助於您維持邏輯順序。 例如，如果您想要收集產品的相關資訊，可以定義下列變數：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

上下文資料變數在處理規則介面中會依字母順序排序，因此命名空間可讓您快速查看位於相同命名空間中的變數。

此外，我們聽說您中有些人使用evar或prop編號來命名上下文資料索引鍵：

```js
"eVar1":"jimbo"
```

這可能會讓您在處理規則中執行一次對應時，變得更容易&#x200B;*稍微*，但在除錯時會失去可讀性，而未來的程式碼更新可能會更困難。 我們強烈建議您針對索引鍵和值使用描述性名稱：

```js
"username":"jimbo"
```

將定義計數器事件的上下文變數設定為&quot;1&quot;:

```js
"logon":"1"
```

定義增量器事件的上下文資料變數可具有遞增值：

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe 會保留命名空間 `a.`。除了這些小限制外，上下文資料變數在登入公司中只需要是唯一的，以避免衝突。

## Products 變數 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

若要在行動SDK中設定&#x200B;*`products`*，您必須使用特殊語法。 請參閱[產品變數](/help/windows-appstore/analytics/products/products.md)。

## （可選）啟用離線追蹤{#section_955B2A03EB854742BDFC4A0A3C287009}

若要在裝置離線時儲存點擊，您可以在[ADBMobileConfig.json組態](/help/windows-appstore/c-configuration/methods.md)中啟用離線追蹤。 在啟用離線追蹤之前，請注意設定檔案參考中所述的時間戳記要求。

## 地理位置與地標 {#section_BAD34A8DD013454DB355121316BD7FD4}

地理位置可讓您測量位置資料（經緯度）和預先定義的地標。 每個`TrackLocation`呼叫都發送：

* 緯度／經度和POI（如果在`ADBMobileConfig.json`組態檔中定義的POI中）。 這些變數會傳遞至行動解決方案變數，以進行自動報告。
* 中心距離與作為上下文資料傳遞的精確度。 使用處理規則擷取。

若要追蹤位置：

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

如果`ADBMobileConfig.json`配置檔案中定義了以下POI:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

當裝置位置被判斷為在定義點的7000米半徑內時，`a.loc.poi`上下文資料變數會隨`TrackLocation`點擊傳送值為&quot;San Francisco&quot;。 `a.loc.dist`上下文變數會以距離定義座標的米數傳送。

## 期限值{#section_D2C6971545BA4D639FBE07F13EF08895}

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

## 計時動作 {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

計時動作可讓您測量動作開始和結束之間的應用程式內時間和總時間。 SDK會計算作業中的時間量以及完成動作所花費的總時間（跨作業）。 這可用來定義區段，以便在購買、通過層級、結帳流程等時進行比較。

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
