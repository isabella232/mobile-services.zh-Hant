---
description: 本節說明如何從舊版Windows行動SDK的3.x版移轉至Windows 8.1 Universal App Store 4.x SDK for Experience Cloud解決方案。
seo-description: 本節說明如何從舊版Windows行動SDK的3.x版移轉至Windows 8.1 Universal App Store 4.x SDK for Experience Cloud解決方案。
seo-title: 移轉至4.x SDK
solution: Experience Cloud,Analytics
title: 移轉至4.x SDK
topic: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 13%

---


# 移轉至4.x SDK {#migrate-to-the-x-sdks}

本節說明如何從舊版Windows行動SDK的3.x版移轉至Windows 8.1 Universal App Store 4.x SDK for Experience Cloud解決方案。

移至4.x版後，所有功能現在都可透過靜態方法存取，因此不再需要追蹤您自己的物件。

以下各節將逐步引導您從3.x版移轉至4.x版。

## 移除未使用的屬性 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能注意到下載 `ADBMobileConfig.json` 時包含了新檔案。 此檔案包含應用程式專用的全域設定，並取代舊版中使用的大部分設定變數。 以下是 `ADBMobileConfig.json` 檔案的範例:

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

以下表格列出您需要移至設定檔案的設定變數。將第一欄中變數的值集移至第二欄中的變數，然後從程式碼中移除舊組態變數。

## 從3.x移轉

| 組態變數／方法 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;貨幣&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | 移除，不再使用。 |
| linkTrackVars | 移除，不再使用。 |
| linkTrackEvents | 移除，不再使用。 |

## 更新追蹤呼叫和追蹤變數 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

第4版SDK不使用以網 `Track` 頁為主 `TrackLink` 的呼叫，而是使用兩種在行動世界中更有意義的方法：

* `TrackState` 狀態是應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

* `TrackAction` 動作是您要測量的應用程式中發生的事，例如「登入」、「橫幅點選」、「動態消息訂閱」和其他量度。 這些呼叫不會增加頁面檢視。

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

## 事件、Prop、eVar

如果您已檢視過 [SDK方法](/help/windows-appstore/c-configuration/methods.md)，您可能會想知道在何處設定事件、eVar、prop、繼承者和清單。 在第4版中，您無法再直接在應用程式中指派這些類型的變數。 SDK會改用上下文資料和處理規則將應用程式資料對應至Analytics變數以進行報告。

處理規則提供您幾項優點：

* 您可以變更資料對應，毋需送出更新至App Store。
* 您可以對資料使用有意義的名稱，而不是設定報表套裝專屬的變數。
* 傳送額外資料的影響很小。 這些值在使用處理規則對應之前，不會出現在報表中。

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

您直接指派給變數的任何值，應改為新增至上下文資料。 This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server、GeoZip、交易ID、促銷活動和其他標準變數**

您在測量物件上設定的任何其他資料（包括上述的變數），應改為新增至上下文資料。

簡單地說，隨或呼叫傳送的唯一資 `TrackState` 料 `TrackAction` 是參數中的裝載 `data` 。

### 取代追蹤呼叫

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

### 從3.x移轉

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## 自訂訪客 ID {#section_2CF930C13BA64F04959846E578B608F3}

以呼叫 `visitorID`: 取代`setUserIdentifier` 變數。

## 離線追蹤 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

在整個程式碼中，移除對下列方法的呼叫：

### 從3.x移轉

* `SetOnline`
* `SetOffline`

## 產品變數 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由於處理規則中沒有該產品變數，因此您可以使用以下語法來設定 `products`:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

在此範例中，值為 `"&&products"` &quot; `";Cool Shoe`，且應遵循您追蹤之事件類型的產品字串語法。