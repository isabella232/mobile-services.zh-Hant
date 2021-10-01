---
description: 可協助您使用ADBMobile JSON設定檔案的資訊。
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json 設定
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 42%

---

# ADBMobileConfig.json設定檔案 {#adbmobileconfig-json-config}

可協助您使用ADBMobile JSON設定檔案的資訊。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。設定方法的前置詞為「Config」。

* **rsids**

   （**Analytics需要**）一或多個報表套裝，用以接收Analytics資料。 多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

   * 此方法的語法如下：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   （**Analytics和Audience Management要求**）。 Analytics或Audience Management伺服器，根據父節點。 應該以伺服器網域填入此變數，不含 `"https://"` 或 `"https://"` 通訊協定前置詞。通訊協定前置詞會由程式庫根據`ssl`變數自動處理。

   如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用於傳送至Analytics之資料的字元集。 字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。如需詳細資訊，請參閱Adobe Analytics檔案中的[charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html)變數。

* **ssl**

   啟用(`true`)或停用(`false`)透過SSL(`HTTPS`)傳送測量資料。 預設值為 `false`。

* **offlineEnabled**

   啟用(`true`)時，點擊會在裝置離線時排入佇列，並在稍後裝置上線時傳送。 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   如果報表套裝已啟用時間戳記，您的`offlineEnabled`組態屬性&#x200B;*必須*&#x200B;為`true`。 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 `false`.

   若未正確設定，資料將會遺失。如果您不確定報表套裝是否啟用時間戳記，請聯絡客戶服務。 如果您目前回報AppMeasurement資料的報表套裝也可從JavaScript收集資料，則可能需要為行動資料設定個別的報表套裝，或在使用`s.timestamp`變數的所有JavaScript點擊上加上自訂時間戳記。

   預設值為 `false`。

* **lifecycleTimeout**

   指定應用程式啟動後，直至系統將該次啟動視為新工作階段之間須經過的時間長度 (以秒為單位)。您的應用程式傳送至背景並重新啟動時，此逾時也適用。應用程式在背景執行的時間不會計入工作階段中。

   預設值為300秒。

* **batchLimit**

   批次傳送點擊。

   例如，若設為`50`，則會將點擊排入佇列，直到儲存50個點擊為止，然後會傳送所有佇列的點擊。 需要`offlineEnabled=true`，預設值為`0`（無批次處理）。

* **privacyDefault**

   選項為：

   * `optedin` – 會立即傳送點擊。
   * `optedout` – 會捨棄點擊。
   * `optunknown`  — 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入（屆時會傳送點擊）或選擇退出（屆時會捨棄點擊）為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      這只會設定預設值。 如果您曾在程式碼中設定或變更此值，則程式碼設定的值會儲存在本機儲存體中，並持續使用，直到變更，或應用程式解除安裝並重新安裝為止。

      預設值為 `optedin`。

* **poi**

   每個 POI 陣列內含 POI 名稱、該地標區域的經緯度以及半徑 (以公尺為單位)。POI 名稱可以是任何字串。送出 `trackLocation` 呼叫後，如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此變數的范常式式碼：

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   （**Target**&#x200B;所需）您指派的用戶端代碼。

* **timeout**

   決定target等待回應的時間長度。

以下是`ADBMobileConfig.json`檔案的範例：

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
