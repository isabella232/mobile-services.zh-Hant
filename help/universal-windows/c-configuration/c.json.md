---
description: 幫助您使用ADBMobile JSON配置檔案的資訊。
solution: Experience Cloud Services,Analytics
title: ADBMobileConfig.json 設定
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 42%

---

# ADBMobileConfig.json配置檔案 {#adbmobileconfig-json-config}

幫助您使用ADBMobile JSON配置檔案的資訊。

SDK當前支援多個Adobe Experience Cloud解決方案，包括分析、目標和Audience Manager。 各方法會根據解決方案加上前置詞。配置方法的前置詞為「Config」。

* **rsids**

   (**分析所需**)一個或多個報告套件以接收分析資料。 多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

   * 此方法的語法如下：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**分析和受眾管理要求**)。 基於父節點的分析或受眾管理伺服器。 應該以伺服器網域填入此變數，不含 `"https://"` 或 `"https://"` 通訊協定前置詞。協定前置詞由庫根據 `ssl` 變數。

   如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義要用於發送到分析的資料的字元集。 字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。有關詳細資訊，請參見 [字元集](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html) 變數。

* **ssl**

   啟用(`true`)或禁用(`false`)通過SSL發送測量資料(`HTTPS`)。 預設值為 `false`。

* **offlineEnabled**

   啟用時(`true`)，命中在設備離線時排隊，稍後在設備聯機時發送。 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   如果在報表套件上啟用時間戳，則 `offlineEnabled` 配置屬性 *必須* 是 `true`。 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 `false`.

   若未正確設定，資料將會遺失。如果您不確定是否啟用了報表套件時間戳，請與客戶服務部聯繫。 如果您當前正在向同時從JavaScript收集資料的報告套件報告AppMeasurement資料，則可能需要為移動資料設定單獨的報告套件，或使用 `s.timestamp` 變數。

   預設值為 `false`。

* **lifecycleTimeout**

   指定應用程式啟動後，直至系統將該次啟動視為新工作階段之間須經過的時間長度 (以秒為單位)。您的應用程式傳送至背景並重新啟動時，此逾時也適用。應用程式在背景執行的時間不會計入工作階段中。

   預設值為300秒。

* **batchLimit**

   成批發送命中。

   例如，如果設定為 `50`，命中數將排入隊列，直到儲存50，然後發送所有排隊的命中數。 需要 `offlineEnabled=true`，預設值為 `0` （無批處理）。

* **privacyDefault**

   選項包括：

   * `optedin` – 會立即傳送點擊。
   * `optedout` – 會捨棄點擊。
   * `optunknown`  — 如果報告套件啟用了時間戳，則會保存命中，直到隱私狀態更改為選擇加入（然後發送命中）或選擇退出（然後丟棄命中）。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      這僅設定預設值。 如果在代碼中設定或更改了此值，則代碼設定的值將保存在本地儲存中並一直使用，直到更改，或卸載應用並重新安裝。

      預設值為 `optedin`。

* **poi**

   每個 POI 陣列內含 POI 名稱、該地標區域的經緯度以及半徑 (以公尺為單位)。POI 名稱可以是任何字串。送出 `trackLocation` 呼叫後，如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此變數的代碼示例：

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**目標要求**)分配的客戶端代碼。

* **timeout**

   確定目標等待響應的時間。

以下是 `ADBMobileConfig.json` 檔案：

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
