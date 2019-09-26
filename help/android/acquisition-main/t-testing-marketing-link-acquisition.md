---
description: 下列指示可協助您在Android裝置上使用行銷連結來回往返贏取促銷活動。
keywords: android;library;mobile;sdk
seo-description: 下列指示可協助您在Android裝置上使用行銷連結來回往返贏取促銷活動。
seo-title: 測試行銷連結贏取
solution: Marketing Cloud,Analytics
title: 測試行銷連結贏取
topic: 開發人員和實施
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

下列指示可協助您在Android裝置上使用行銷連結來回往返贏取促銷活動。

如果您的行動應用程式尚未在Google play中，您可以在建立行銷連結時選取任何行動應用程式作為目的地。 這只會影響贏取伺服器將您重新導向的應用程式 (在您點擊贏取連結後)，而不會影響測試贏取連結的能力。查詢字串參數會傳遞至 Google Play 商店，然後在安裝時傳遞至應用程式，作為促銷活動廣播的一部分。往返行動應用程式贏取測試需要模擬此廣播類型。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. 這樣即可確保應用程式首次啟動時，與促銷活動查詢字串參數關聯的初始生命週期量度可以順利傳送。

1. Complete the prerequisite tasks in Mobile app acquisition and ensure that you have correctly implemented the broadcast receiver for .[](/help/android/acquisition-main/acquisition.md)`INSTALL_REFERRER`
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。

   例如:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 在 Android 裝置上開啟剛才產生的連結。

   系統會將您重新導向至另一頁面 (其 URL 類似下列範例):

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   在上例中，ID為 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

   如果您無法在裝置上取得唯一 ID，請在電腦上執行下列 `CURL` 命令，即可從回應字串中取得唯一 ID。

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   例如:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 透過於步驟 3 取得的唯一 ID 來建構贏取結束連結 (須為下列格式):

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   例如, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 在瀏覽器中開啟連結。

   您應會在 JSON 回應中看見 `contextData`:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. 重複步驟 3 以取得新的唯一 ID。
1. 確認設定檔案中的下列設定是否正確:

   | 設定 | 值 |
   |--- |--- |
   | acquisition | The server should be `c00.adobe.com`, and      *`appid`*  should equal the `appid` in your acquisition link. |
   | analytics | 為了測試的目的，請將反向連結逾時設為具有足夠的時間 (60 秒以上) 來手動傳送廣播。您可以在測試結束後將逾時設定還原為原始值。 |

1. 將裝置與電腦連接，解除安裝應用程式，然後重新安裝。
1. 啟動 ADB 殼層，然後啟動裝置上的應用程式。

   ```
   adb shell
   ```

1. 使用下列 `adb` 命令傳送廣播:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. 將 `com.adobe.android` 替換為應用程式的封裝名稱，並以應用程式中促銷活動追蹤接收器位置的接收器參考更新原本的接收器參考，然後替換與 `utm_content` 關聯的值。

   如果廣播成功，您可以預期如以下範例中的回應:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (選擇性) 您可以啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   如果您沒有看見這些記錄，請確認您已完成步驟 6 至步驟 10。

   下表包含了可能錯誤的額外資訊:

   | 錯誤 | 說明 |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | 回應的格式不正確。 |
   | Analytics - Unable to parse response (`a JSON Response`). | JSON 字串的格式不正確。 |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | 回應中沒有 `contextData` 參數。 |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` 未包含在contextData中。 |
   | Analytics - Acquisition referrer timed out. | 無法於 `referrerTimeout` 所定義的時間內取得回應。請增加值，然後再試一次。您也應確定在開啟贏取連結後才安裝應用程式。 |

請記住以下資訊:

* 藉由使用 HTTP 監控工具，即可監控從應用程式傳送的點擊，以便確認贏取屬性。
* 如需有關如何廣播 `INSTALL_REFERRER` 的詳細資訊，請參閱 Google Developers Guide (Google 開發人員指南) 中的 [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns) (測試 Google Play 促銷活動測量)。
* 您可以使用隨附的 `acquisitionTest.jar` Java 工具來協助您取得唯一 ID 和廣播安裝反向連結，如此將可協助您取得步驟 3 至步驟 10 中的資訊。

**安裝Java工具**

安裝 Java 工具:

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. 解壓縮 .jar 檔案。

   您可以在命令列上執行 .jar 檔案。

例如:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

行銷連結會在伺服器端快取10分鐘的過期時間。 如果您變更行銷連結，應等待約 10 分鐘變更生效後再使用這些連結。
