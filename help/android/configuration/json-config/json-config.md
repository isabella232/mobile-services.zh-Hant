---
description: 此資訊可協助您使用 ADBMobile.json 設定檔。
seo-description: 此資訊可協助您使用 ADBMobile.json 設定檔。
seo-title: ADBMobile JSON 設定
solution: Experience Cloud,Analytics
title: ADBMobile JSON 設定
topic: Developer and implementation
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1678'
ht-degree: 100%

---


# ADBMobile JSON 設定檔案 {#adbmobile-json-config}

此資訊可協助您了解 ADBMobile.json 設定檔案中的變數。

## `ADBMobileConfig.json` 設定檔案參考 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

您的應用程式可以跨多平台使用此相同的設定檔案：

>[!TIP]
>
>在 **Android** 中，`ADBMobileConfig.json` 檔案必須放置在 `assets` 資料夾中。

以下是 JSON 檔案中的變數清單，以及每個變數所需的最低 SDK 版本：

* **acquisition**
   * 最低 SDK 版本：4.1
   * 啟用行動應用程式贏取。
      * `server`，即在初次啟動時會接受檢查是否有贏取反向連結的贏取伺服器。
      * `appid` – 即產生的 ID，可在贏取伺服器上唯一識別此應用程式。

   如果缺少此區段，請啟用行動應用程式贏取並重新下載 SDK 設定檔。如需詳細資訊，請參閱變數清單中的 *referrerTimeout*。

* **analyticsForwardingEnabled**
   * 最低 SDK 版本為 4.8.0。
   * 預設值為 `false`。

      `audienceManager` 物件中的屬性。如果已設定 Audience Manager 且 `analyticsForwardingEnabled` 已設為 `true`，所有的 Analytics 流量也會轉送至 Audience Manager。

* **backdateSessionInfo**
   * 最低 SDK 版本：4.6.
   * 啟用/停用 Adobe SDK 日期回溯工作階段資訊點擊的能力。

      工作階段資訊點擊目前包含當機和工作階段長度，可予以啟用或停用。

      **啟用或停用點擊**

      * 若將值設為 `false`，表示&#x200B;**停用**&#x200B;點擊。SDK 會回到 4.1 版之前的行為，將上一個工作階段的工作階段資訊與後續工作階段的第一次點擊混合在一起。Adobe SDK 也會將工作階段資訊加至目前的生命週期，以免造訪數據膨脹。由於造訪數據不再膨脹，造訪次數會立即下降。

      * 若您未提供值，系統的預設值會是 `true`，亦即&#x200B;**啟用**&#x200B;點擊。啟用點擊後，Adobe SDK 會將工作階段資訊點擊回溯至上一個工作階段最後一次點擊後 1 秒。換句話說，當機和工作階段資料會與正確的發生日期相互關聯。其中一個副作用，是 SDK 可能會為回溯點擊產生一次造訪。應用程式每次重新啟動，日期都會回溯一個點擊。

         >[!IMPORTANT]
         >
         >日期回溯工作階段點撃資訊會以工作階段資訊伺服器呼叫傳送，且可能適用額外的伺服器呼叫。

* **batchLimit**
   * 最低 SDK 版本：4.1
   * 連續呼叫中可傳送的點撃數臨界值。

      例如，如果 `batchLimit` 設為 10，則在第 10 個點擊前的每個點擊都會先儲存在佇列中。第 10 個點擊傳入時，系統便會連續傳送全部 10 個點擊。

      請記住以下資訊：

      * 預設值為 `0`，即表示未啟用批次處理程序。
      * 需要使用 `offlineEnabled = true`。

* **charset**
   * 最低 SDK 版本：4.0
   * 定義您用於傳送至 Analytics 之資料的字元集。

      字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。

* **clientCode**
   * 最低 SDK 版本：4.0
   * 您獲派的用戶端代碼。

      >[!IMPORTANT]
      >
      >Target 必須有此變數。

* **coopUnsafe**
   * 最低 SDK 版本：4.16.1
   * `marketingCloud` 物件的布林值屬性一旦設為 `true`，就會導致裝置退出 Experience Cloud 的 Device Co-Op。
   * 預設值為 `false`。
   * **唯有**&#x200B;以 Device Co-op 佈建的客戶，才會使用此設定。

   若 Device Co-op 成員要求將此值設為 `true`，您需要與 Co-op 團隊合作，為您的 Device Co-op 帳戶申請封鎖名單標幟。沒有自助式路徑可供啟用這些標幟。

   請記住以下資訊：

   * `coopUnsafe` 設為 `true` 時，`coop_unsafe=1` 一律會附加至 Audience Manager 和訪客 ID 點擊。
   * 如果啟用 Analytics 伺服器端轉送至 Audience Manager，您也會看到 `coop_unsafe=1` Analytics 點擊。


* **environmentId**
   * 最低 SDK 版本：4.14
   * 您想使用之環境的 ID。

      您可以指定有效的 ID (`environmentId=8`)，要是沒有 `environmentId`，系統會使用預設的生產環境。

* **lifecycleTimeout**
   * 最低 SDK 版本：4.0
   * 預設值為 300 秒。

      指定應用程式啟動後，直至系統將該次啟動視為新工作階段之間須經過的時間長度 (以秒為單位)。您的應用程式傳送至背景並重新啟動時，此逾時也適用。

      應用程式在背景執行的時間不會計入工作階段中。

* **messages**

   * 最低 SDK 版本：4.2
   * 由 Adobe Mobile Services 自動產生，定義應用程式內傳訊的設定。如需詳細資訊，請參閱下方的&#x200B;*訊息說明*&#x200B;一節。

* **offlineEnabled**

   * 最低 SDK 版本：4.0
   * 啟用後，點擊會在裝置離線時排入佇列，並在稍後裝置上線時傳送。

      您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

      預設值為 `false`。

      >[!IMPORTANT]
      >
      >如果報表套裝已啟用時間戳記，您的 `offlineEnabled` 組態屬性&#x200B;**必須**&#x200B;為 true。如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;**必須**&#x200B;為 false。
      >
      >若未正確設定，資料將會遺失。如果您不確定報表套裝是否啟用時間戳記，請連絡客戶服務人員，或從 Adobe Mobile Services 下載設定檔。

      如果您目前回報 AppMeasurement 資料的報表套裝也可從 JavaScript 收集資料，則必須為行動資料設定個別的報表套裝，或在使用 `s.timestamp` 變數的所有 JavaScript 點擊上加上自訂時間戳記。

* **org**

   * 最低 SDK 版本：4.3
   * 指定 ID 服務的 Experience Cloud 組織 ID。

* **poi**
   * 最低 SDK 版本：4.0
   * 每個地標 (POI) 陣列內含 POI 名稱、該地標區域的經緯度以及半徑 (以公尺為單位)。

      POI 名稱可以是任何字串。送出 `trackLocation` 呼叫後，如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      自 4.2 版開始，POI 皆會在 Adobe Mobile 介面中定義，並會動態同步至應用程式設定檔。此同步需使用 `analytics.poi` 設定：

      ```javascript
        “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      若尚未設定此設定，則必須更新 `ADBMobile.json` 檔案以包含此行。若要下載更新的設定檔，請參閱[開始之前](/help/android/getting-started/requirements.md)。

* **postback**
   * 最低 SDK 版本：4.6
   * 以下是「回撥」訊息範本的定義：

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      程式碼中的 `payload` 物件是會進入 `ADBMobileConfig.json` 檔案之訊息定義的裝載範例。如需詳細資訊，請參閱[回傳](/help/android/analytics-main/postbacks/postbacks.md)。

* **privacyDefault**
   * 最低 SDK 版本：4.0
   * 預設值為 `optedin`。
      * 若為 `optedin`，點擊會立即傳送。
      * 若為 `optedout`，點擊會被捨棄。
      * 若為 `optunknown`，如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為`optedin`為止。這只會設定初始值。如果已在程式碼中設定或變更此值，即會使用新的值直到再次變更，或應用程式解除安裝並重新安裝為止。


* **referrerTimeout**
   * 最低 SDK 版本：4.1
   * SDK 在初始啟動到逾時前等待贏取反向連結資料的秒數。如果您使用贏取，建議將逾時設為 5 秒。

      >[!IMPORTANT]
      >
      >「贏取」必須有此變數。如果變數設為 `0` 或不包含變數，SDK 不會等待贏取資料，且不會追蹤贏取量度。

* **remotes**
   * 最低 SDK 版本：4.2
   * 自動設定並為動態設定檔定義 Adobe 已裝載端點。

      每個設定檔的最後一次更新時間將對每次啟動時的當前版本進行檢查，且會下載並儲存更新。
      * `analytics.poi` 是裝載 POI 設定的端點。
      * `messages` 是裝載應用程式內訊息設定的端點。

* **rsids**
   * 最低 SDK 版本：4.0
   * 要接收 Analytics 資料的一或多個報表套裝。多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Analytics 必須有此變數。

* **server**
   * 最低 SDK 版本：4.0
   * Analytics 或 Audience Management 伺服器，依父節點而定。應該以伺服器網域填入此變數，不含 `https://` 或 `https://` 通訊協定前置詞。此前置詞會由資料庫自動處理且是以 `ssl` 變數為基礎。如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **ssl**
   * 最低 SDK 版本：4.0
   * 預設值為 `false`。

      啟用 (`true`) 或停用 (`false`) 透過 SSL (HTTPS) 傳送測量資料的能力。

      以下顯示「回撥」訊息範本的定義：

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * 最低 SDK 版本：4.0
   * 決定 Target 等待回應的時間長度。


## 範例 `ADBMobileConfig.json` 檔案 {#section_4655EF79744649E5A5AE19E3224C472C}

以下是範例 `ADBMobileConfig.json` 檔案：

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## 訊息說明 {#section_B97D654BA92149CE91F525268D7AD71F}

訊息節點會由 Adobe Mobile Services 自動產生，通常不需要手動變更。以下提供相關說明以利疑難排解：

* &quot;messageId&quot;
* 產生的 ID，必填
* &quot;template&quot;
   * &quot;alert&quot;、&quot;fullscreen&quot; 或 &quot;local&quot;
   * 必填

* &quot;showOffline&quot;
   * true 或 false
   * 預設為 false

* &quot;showRule&quot;
   * &quot;always&quot;、&quot;once&quot; 或 &quot;untilClick&quot;
   * 必填

* &quot;endDate&quot;
   * 自 1970 年 1 月 1 日以來的秒數
   * 預設為 2524730400

* &quot;startDate&quot;
   * 自 1970 年 1 月 1 日以來的秒數
   * 預設為 0

* &quot;payload&quot;
   * &quot;html&quot;
      * 僅限全螢幕範本，必填
      * 定義訊息的 html
   * &quot;image&quot;
      * 僅限全螢幕，選填
      * 用於全螢幕影像的影像 URL
   * &quot;altImage&quot;
      * 僅限全螢幕，選填
      * 要使用的套裝影像名稱 (若
         * image
         * 中指定的 URL 無法連線)
   * &quot;title&quot;
      * 全螢幕和警報，必填
      * 全螢幕或警報訊息的標題文字
   * &quot;content&quot;
      * 警報和本機通知，必填
      * 警報訊息的次要文字，或本機通知訊息的通知文字
   * &quot;confirm&quot;
      * 警報，選填
      * 確認按鈕中使用的文字
   * &quot;cancel&quot;
      * 警報，必填
      * 取消按鈕中使用的文字
   * &quot;url&quot;
      * 警報，選填
      * 按一下確認按鈕後所載入的 URL 動作
   * &quot;wait&quot;
      * 本機通知，必填
      * 符合本機通知的標準後，等待發佈本機通知的時間 (以秒為單位)



* &quot;audiences&quot;
   * 定義訊息顯示方式的物件陣列：
   * &quot;key&quot;
      * 要在點擊中尋找的變數名稱，必填
* &quot;matches&quot;
   * 比較時使用的比對器類型
   * eq = 等於
   * ne = 不等於
   * co = 包含
   * nc = 不包含
   * sw = 開頭為
   * ew = 結尾為
   * ex = 有
   * nx = 沒有
   * lt = 小於
   * le = 小於或等於
   * gt = 大於
   * ge = 大於或等於
* &quot;values&quot;
   * 比對變數值所使用的值陣列，值命名於：
      * key
      * with the matcher type in
      * matches
* &quot;triggers&quot;
   * 與適用對象相同，但此處是指動作，而非對象本身
   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
