---
description: 此節說明如何從先前的 Windows 行動 SDK 3.x 版移轉至 Experience Cloud 解決方案適用的通用 Windows 平台 4.x SDK。
seo-description: 此節說明如何從先前的 Windows 行動 SDK 3.x 版移轉至 Experience Cloud 解決方案適用的通用 Windows 平台 4.x SDK。
seo-title: Migrate to 4.x
solution: Marketing Cloud,Analytics
title: Migrate to 4.x
topic: 開發人員和實施
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# 移轉至4.x SDK{#migrate-to-x}

This section describes how to migrate from the 3.x version of the Windows mobile SDK to the Universal Windows Platform 4.x SDK for Experience Cloud Solutions.

移至4.x版後，所有功能現在都可透過靜態方法存取。 您不再需要追蹤自己的物件。

以下幾節將引導您從第 3.x 版移轉至第 4.x 版。

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能已注意到下載內容中包含一個新的 `ADBMobileConfig.json` 檔案。此檔案包含應用程式專屬的全域設定，並會取代先前版本中使用的大部分設定變數。

以下是 `ADBMobileConfig.json` 檔案的範例:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

以下表格列出您需要移至設定檔案的設定變數。將設於首欄變數的值移動到第二個欄中的變數，然後從程式碼中移除舊設定變數。

### 從第 3.x 版移轉

下表提供3.x SDK中的變數清單，以及4.x SDK中的新名稱：

| 設定變數/方法 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | 移除，不再使用。 |
| linkTrackVars | 移除，不再使用。 |
| linkTrackEvents | 移除，不再使用。 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

第 4 版 SDK 使用在行動場景中更為合理的兩種方法，取代使用以 Web 為中心的 `Track` 和 `TrackLink` 進行呼叫:

* `TrackState`狀態為應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」和「購物車」等等。這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

* `TrackAction`動作是發生在應用程式中而且您想測量的項目，例如「登入」、「橫幅點選」、「摘要訂閱」以及其他量度。這些呼叫不會遞增頁面檢視。

這兩種方法的 `contextData` 參數包含以內容資料傳送的名稱值組。

### Events, props, eVars

如果您已檢視過 [SDK方法](/help/universal-windows/c-configuration/methods.md)，您可能會想知道在何處設定事件、eVar、prop、繼承者和清單。 在第 4 版中，您已無法在應用程式中直接指派那些變數類型。SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在透過處理規則對應前，都不會出現在報表中。

如需詳細資訊，請參閱 *Analytics總覽中的* 「處理 [規則」區段](/help/universal-windows/analytics/analytics.md)。

任何您直接指派給變數的值，應已改為新增至內容資料。This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/Server、GeoZip、交易ID、促銷活動和其他標準變數

您在測量物件上設定的資料，包括以上列出的變數，應已改為新增至內容資料。也就是說，隨或呼叫傳送的唯一資 `TrackState` 料 `TrackAction` 是參數中的裝載 `data` 值。

**取代追蹤呼叫**

在您的程式碼中，以呼叫 `trackState` 或 `trackAction` 取代以下方法:

**從第 3.x 版移轉:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## 自訂 ID 服務 {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

檔案中已啟用離線追 `ADBMobileConfig.json` 蹤。 所有其他離線設定都會自動完成。

在您的程式碼中，移除對以下方法的呼叫:

**從第 3.x 版移轉:**

* SetOnline
* SetOffline

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由於處理規則中沒有該產品變數，因此您可以使用以下語法來設定 `products`:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.
