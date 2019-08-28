---
description: 此資訊可協助您使用 ADBMobile JSON 設定檔案。
seo-description: 此資訊可協助您使用 ADBMobile JSON 設定檔案。
seo-title: ADBMobileConfig. json config
solution: Marketing Cloud、Analytics
title: ADBMobileConfig. json config
topic: 開發人員和實施
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobileConfig. json config檔案 {#adbmobileconfig-json-config}

此資訊可協助您使用 ADBMobile JSON 設定檔案。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target 以及 Audience Manager。各方法會根據解決方案加上前置詞。Configuration 方法會加上前置詞 "Config"。

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. 多個報表套裝的 ID 應以逗號分隔，中間沒有空格。

   * 以下是此方法的語法:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Required by Analytics and Audience Management**). Analytics 或 Audience Management 伺服器，依父節點而定。This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. 通訊協定字首會由程式庫根據 `ssl` 變數自動處理。

   如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用於傳送至 Analytics 之資料的字元集。字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). 預設值為 `false`。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 `false`.

   如果此項目未正確設定，將會遺失資料。如果您不確定報表套裝是否啓用時間戳記，請聯絡客戶服務。If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   預設值為 `false`。

* **lifecycleTimeout**

   指定在兩次應用程式啟動之間需經過的時間長度 (單位為秒)，超過該秒數後，該次啟動即視同新的作業階段。這個逾時值也套用至將應用程式傳送至背景並重新啟動時。應用程式在背景花的時間，不算在作業階段長度中。

   預設值為300秒。

* **batchLimit**

   批次傳送點擊。

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. 需要 `offlineEnabled=true`，而預設值為 `0` (無批次處理)。

* **privacyDefault**

   選項包括：

   * `optedin` - 點擊會立即傳送。
   * `optedout` - 點擊會被捨棄。
   * `optunknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      這只會設定預設值。若已在程式碼中設定或變更此值，則程式碼設定的值會儲存在本機儲存空間，並持續使用直到變更此值，或應用程式解除安裝並重新安裝為止。

      預設值為 `optedin`。

* **poi**

   每個 POI 陣列內含 POI 名稱、該地標區域的經緯度以及半徑 (以公尺為單位)。POI 名稱可以是任何字串。送出 `trackLocation` 呼叫後，如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此變數的程式碼範例：

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   決定 target 等待回應的時間長度。

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
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
