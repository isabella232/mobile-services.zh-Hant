---
description: 本資訊可協助您從 Android 資料庫 3.x 或 2.x 版移轉至 4.x 版。
keywords: android;library;mobile;sdk
seo-description: 本資訊可協助您從 Android 資料庫 3.x 或 2.x 版移轉至 4.x 版。
seo-title: 移轉至 Android 4.x 資料庫
solution: Marketing Cloud,Analytics
title: 移轉至 Android 4.x 資料庫
topic: 開發人員和實施
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

本資訊可協助您從 Android 資料庫 3.x 或 2.x 版移轉至 4.x 版。

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  If you modify or remove the values in `SharedPreferences` that are expected by the SDK, unexpected behavior might result in the form of data inconsistencies.

在 4.x 版資料庫中，公用方法皆已整合為一個標題。同時，所有功能現已可透過類別層級方法存取，因此您無須持續追蹤指標、例項或單一項目。

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

在第 4 版中，您已無法在應用程式中指派 event、eVar、prop、heir 及 list 等變數。SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。

   這些值在透過處理規則對應前，都不會出現在報表中。

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新的 `ADBMobileConfig.json` 檔案包含應用程式專屬的全域設定，並會取代先前版本中使用的大部分設定變數。以下是 `ADBMobileConfig.json` 檔案的範例:

```js
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

以下表格列出您需要移至設定檔案的設定變數。

### 移動設定檔案

1. 將第一欄中為變數設定的值移至第二欄中的變數。
1. 從您的程式碼移除舊的設定變數。

### 從第 3.x 版移轉

若要從3.x版移轉至4版，請將組態變數／方法值移至變 `ADBMobileConfig.json` 數。

| 配置變數或方法 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 移除，不再使用。 |
| linkTrackEvents | 移除，不再使用。 |

### 從第 2.x 版移轉

若要從2.x版移轉至4版，請將值從第一欄移至第二欄中的變數。

| 設定變數 | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server"，刪除首 `"https://"` 碼。 通訊協定前置詞會根據 "ssl" 設定自動新增。 |
| trackingServerSecure | 移除。為了進行安全連線，請定義 "server" 然後啟用 "ssl"。 |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 移除，不再使用。 |
| linkTrackEvents | 移除，不再使用。 |
| timestamp | 移除，無法再設定。 |
| dc | 移除，不再使用。 |
| userAgent | 移除，無法再設定。 |
| dynamicVariablePrefix | 移除，不再使用。 |
| visitorNamespace | 移除，不再使用。 |
| usePlugins | 移除，不再使用。 |
| useBestPractices  對混合測量的所有呼叫 (getChurnInstance) | 移除，由生命週期度量取代。 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

第 4 版 SDK 使用以下方法，取代使用以 Web 為中心的 `track` 和 `trackLink` 呼叫:

* `trackState`，這些是應用程式中可用的檢視， `home dashboard`例如 `app settings`、 `cart`等等。

   這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

* `trackAction` 動作，例 `logons`如 `banner taps`, `feed subscriptions`您要測量的應用程式中發生的動作。

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## 事件、prop和eVar

在第 4 版中，您已無法在應用程式中直接指派 event、eVar、prop、heir 及　list 等變數。SDK 現在會使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則具備以下優點:

* 您可以直接變更資料對應，而不必提交更新至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。

   這些值在透過處理規則對應前，都不會出現在報表中。如需詳細資訊，請參閱 [處理規則與內容資料](/help/android/getting-started/proc-rules.md).

您直接指派給變數的值，應已改為新增至 `data` HashMap。This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server、GeoZip、交易ID、促銷活動和其他標準變數

您在測量物件上設定的資料，包括以上列出的變數，應已新增至 `data` HashMap。與 `trackState` 或 `trackAction` 呼叫一併傳送的唯一資料是 `data` 參數中的裝載。

### 取代追蹤呼叫

以呼叫 `trackState` 或 `trackAction` 取代以下方法:

* **從第 3.x 版移轉**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **從第 2.x 版移轉**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

移除對下列方法的呼叫:

**第 3.x 版**

* `setOnline`
* `setOffline`

**第 2.x 版**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

