---
description: 此節說明如何從先前的 Windows 行動 SDK 3.x 版移轉至 Experience Cloud 解決方案適用的 Windows 8.1 通用應用程式商店 4.x SDK。
seo-description: 此節說明如何從先前的 Windows 行動 SDK 3.x 版移轉至 Experience Cloud 解決方案適用的 Windows 8.1 通用應用程式商店 4.x SDK。
seo-title: Migrate to the 4.x SDKs
solution: Marketing Cloud,Analytics
title: Migrate to the 4.x SDKs
topic: 開發人員和實施
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrate to the 4.x SDKs {#migrate-to-the-x-sdks}

此節說明如何從先前的 Windows 行動 SDK 3.x 版移轉至 Experience Cloud 解決方案適用的 Windows 8.1 通用應用程式商店 4.x SDK。

移轉至第 4.x 版後，所有功能現在可透過靜態方法存取，不再需要記錄您的個人物件。

以下幾節將引導您從第 3.x 版移轉至第 4.x 版。

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能已注意到下載內容中包含一個新的 `ADBMobileConfig.json` 檔案。此檔案包含應用程式專用的全域設定，並取代舊版中使用的大部分設定變數。 以下是 `ADBMobileConfig.json` 檔案的範例:

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

## 從第 3.x 版移轉

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

## Events、Props、eVars

If you've looked at the SDK methods, you are probably wondering where to set events, eVars, props, heirs, and lists. [](/help/windows-appstore/c-configuration/methods.md)在第 4 版中，您已無法在應用程式中直接指派那些變數類型。SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至應用程式商店。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在透過處理規則對應前，都不會出現在報表中。

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

任何您直接指派給變數的值，應已改為新增至內容資料。This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/伺服器、GeoZip、交易 ID、促銷活動以及其他標準變數**

您在測量物件上設定的資料，包括以上列出的變數，應已改為新增至內容資料。

簡而言之，與 `TrackState` 或 `TrackAction` 呼叫一併傳送的唯一資料是 `data` 參數中的裝載。

### 取代追蹤呼叫

在您的程式碼中，以呼叫 `trackState` 或 `trackAction` 取代以下方法:

### 從第 3.x 版移轉

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the  file. `ADBMobileConfig.json`All other offline configuration is done automatically.

在您的程式碼中，移除對以下方法的呼叫:

### 從第 3.x 版移轉

* `SetOnline`
* `SetOffline`

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

In this example, the value of `"&&products"` is `";Cool Shoe`" and should follow the products string syntax for the type of event that you are tracking.