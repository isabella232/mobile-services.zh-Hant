---
description: 本節介紹如何從以前的Windows移動SDK的3.x版遷移到通用Windows平台4.x SDK以用於Experience Cloud解決方案。
solution: Experience Cloud Services,Analytics
title: 移轉至 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# 遷移到4.x SDK{#migrate-to-x}

本節介紹如何從3.x版的Windows移動SDK遷移到通用Windows平台4.x SDK，用於Experience Cloud解決方案。

隨著移動到4.x版，現在可以通過靜態方法訪問所有功能。 你不再需要跟蹤你自己的物品。

以下各節將指導您從3.x版遷移到4.x版。

## 移除未使用的屬性 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

你可能注意到 `ADBMobileConfig.json` 下載時包含的檔案。 此檔案包含特定於應用程式的全局設定，並替換了以前版本中使用的大多數配置變數。

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

以下表格列出您需要移至設定檔案的設定變數。將第一列中變數的值集移到第二列中的變數，然後從代碼中刪除舊配置變數。

### 從3.x遷移

下表提供了3.x SDK中的變數清單和4.x SDK中的新名稱：

| 配置變數/方法 | 中的變數 `ADBMobileConfig.json` 的子菜單。 |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | 移除，不再使用。 |
| linkTrackVars | 移除，不再使用。 |
| linkTrackEvents | 移除，不再使用。 |

## 更新追蹤呼叫和追蹤變數 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

而不是使用以Web為中心 `Track` 和 `TrackLink` 調用，版本4 SDK使用兩種在移動世界中更有意義的方法：

* `TrackState` 狀態是您的應用中可用的視圖，如「首頁儀表板」、「應用設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

* `TrackAction` 操作是您想要衡量的應用中發生的情況，如「登錄」、「橫幅點擊」、「訂閱源」和其他度量。 這些調用不會增量頁面視圖。

的 `contextData` 這兩種方法的參數都包含作為上下文資料發送的名稱 — 值對。

### 事件、Prop、eVar

如果你看過 [SDK方法](/help/universal-windows/c-configuration/methods.md)你可能在想，該在哪裡設定活動、電視、道具、繼承人和清單。 在版本4中，您無法再直接在應用程式中分配這些類型的變數。 SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點：

* 您可以直接變更資料對應，而無須將更新提交至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。在使用處理規則映射這些值之前，這些值不會出現在報表中。

有關詳細資訊，請參見 *處理規則* 部分 [分析概述](/help/universal-windows/analytics/analytics.md)。

應將您直接分配給變數的任何值添加到上下文資料。 這意味著 `SetProp`。 `SetEvar`、和對持久上下文資料的分配應全部刪除，並將值添加到上下文資料。

### AppSection/伺服器、GeoZip、交易 ID、促銷活動以及其他標準變數

您正在測量對象上設定的任何其他資料（包括上面列出的變數）應添加到上下文資料中。 也就是說，只有在 `TrackState` 或 `TrackAction` 呼叫是 `data` 的下界。

**取代追蹤呼叫**

在整個代碼中，將以下方法替換為調用 `trackState` 或 `trackAction`:

**從3.x遷移：**

* TrackAppState(TrackState)
* 跟蹤事件（跟蹤操作）
* 跟蹤（跟蹤操作）
* TrackLinkURL(TrackAction)

## 自定義ID服務 {#section_2CF930C13BA64F04959846E578B608F3}

以呼叫 `visitorID`: 取代`setUserIdentifier` 變數。

## 離線追蹤 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

已在 `ADBMobileConfig.json` 的子菜單。所有其他離線配置都會自動完成。

在整個代碼中，刪除對以下方法的調用：

**從3.x遷移：**

* 集合線上
* 設定離線

## Products 變數 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由於處理規則中沒有該產品變數，因此您可以使用以下語法來設定 `products`:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

值 `"&&products"` (在本例中，值為 `";Cool Shoe`&quot;)應按照您正在跟蹤的事件類型的products字串語法進行操作。
