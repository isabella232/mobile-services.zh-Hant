---
description: 協助您使用ADBMobile JSON設定檔案的資訊。
seo-description: 協助您使用ADBMobile JSON設定檔案的資訊。
seo-title: ADBMobileConfig.json設定檔案
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json設定檔案
topic-fix: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
exl-id: 520dffb8-ca47-444f-bbc9-f18413ddeb05
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 43%

---

# `ADBMobileConfig.json` 配置檔案  {#adbmobileconfig-json-config}

協助您使用`ADBMobile.json`設定檔案的資訊。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。配置方法的前置詞為&quot;Config&quot;。

* **rsids**

   （Analytics需要）一或多個報表套裝，用以接收Analytics資料。 多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

   * 以下是此變數的程式碼範例：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   （Analytics和觀眾管理需要）。 Analytics或Audience Management伺服器（根據父節點）。 應該以伺服器網域填入此變數，不含 `https://` 或 `https://` 通訊協定前置詞。通訊協定首碼由程式庫根據`ssl`變數自動處理。

   如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用來傳送至Analytics之資料的字元集。 字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。如需詳細資訊，請參閱 [s.charSet](https://docs.adobe.com/content/help/zh-Hant/analytics/implementation/vars/config-vars/charset.html)。

* **ssl**

   啟用(`true`)或停用(`false`)透過SSL(HTTPS)傳送測量資料。 預設值為 `false`。

* **offlineEnabled**

   啟用(true)時，會在裝置離線時佇列點擊，並在裝置上線時稍後傳送。 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   >[!IMPORTANT]
   >
   >如果報表套裝已啟用時間戳記，則您的`offlineEnabled`設定屬性&#x200B;*必須*&#x200B;為true。 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 false。若未正確設定，資料將會遺失。如果您不確定報表套裝是否啟用時間戳記，請連絡客戶服務。 如果您目前要將AppMeasurement資料報告至也會從JavaScript收集資料的報表套裝，則可能需要為行動資料設定個別的報表套裝，或使用`s.timestamp`變數在所有JavaScript點擊上加入自訂時間戳記。

* **lifecycleTimeout**

   指定應用程式啟動後，直至系統將該次啟動視為新工作階段之間須經過的時間長度 (以秒為單位)。您的應用程式傳送至背景並重新啟動時，此逾時也適用。應用程式在背景執行的時間不會計入工作階段中。預設值為300秒。

* **batchLimit**

   以批次傳送點擊。 例如，若設為50，則會將點擊排入佇列，直到儲存50，然後會傳送所有佇列的點擊。 需要使用 `offlineEnabled=true`。預設值為`0`（無批次處理）。

* **privacyDefault**

   * `optedin` – 會立即傳送點擊。
   * `optedout` – 會捨棄點擊。
   * `optunknown` -如果您的報表套裝已啟用時間戳記，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著會捨棄點擊）為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值為 `optedin`。

      >[!TIP]
      >
      >這僅設定預設值。 如果此值在程式碼中設定或變更，則程式碼所設定的值會儲存在本機儲存中，並持續使用，直到變更為止，或是解除安裝並重新安裝應用程式。

* **poi**

   每個 POI 陣列內含 POI 名稱、該地標區域的經緯度以及半徑 (以公尺為單位)。POI 名稱可以是任何字串。送出 `trackLocation` 呼叫後，如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此變數的程式碼範例：

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   （**Target**&#x200B;需要）您指派的用戶端代碼。

* **timeout**

   決定 Target 等待回應的時間長度。

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
