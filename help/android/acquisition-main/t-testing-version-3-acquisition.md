---
description: 以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。
keywords: android;library;mobile;sdk
seo-description: 以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。
seo-title: 測試第 3 版贏取
solution: Marketing Cloud,Analytics
title: 測試第 3 版贏取
topic: 開發人員和實施
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing V3 acquisition {#testing-version-acquisition}

以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。

>[!IMPORTANT]
>
>V3中的贏取是指您在Adobe Mobile Services UI中使用贏取產生器建立的贏取連結。 若要使用此功能，您必須升級至適用於 Experience Cloud 解決方案 4.6.0 版或更新版本的 Android SDK 4.x。

如果行動應用程式尚未在 Google Play 上架，則建立促銷活動連結後，您可以選取任一行動應用程式作為目的地。這只會影響贏取伺服器將您重新導向的應用程式 (在您點選贏取連結後)，而不會影響測試連結的能力。查詢字串參數會傳遞至 Google Play 商店，然後在安裝時傳遞至應用程式，作為促銷活動廣播的一部分。往返行動應用程式贏取測試需要模擬此廣播類型。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. 這樣即可確保應用程式首次啟動時，與促銷活動查詢字串參數關聯的初始生命週期量度可以順利傳送。

1. Complete the prerequisite tasks in Mobile App Acquisition and ensure that you have correctly implemented the broadcast receiver for .[](/help/android/acquisition-main/acquisition.md)`INSTALL_REFERRER`
1. In the Adobe Mobile Services UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。

   例如, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >If you refer to both Android and iOS apps in the acquisition link, use Google Play as the default store.

1. 在電腦的瀏覽器中開啟剛才產生的連結。

   系統會將您重新導向至另一頁面 (其 URL 類似下列範例):
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   In the previous example, the ID is .`91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 透過於步驟 3 取得的唯一 ID 來建構贏取結束連結 (須為下列格式):

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`。

   例如, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. 在電腦的瀏覽器中開啟連結。

   您應會在 JSON 回應中看見 `contextData`:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   如果您沒有看見 `contextData`，或缺少部分字串，請確認贏取 URL 是否確實按照[手動建立贏取連結](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)中指定的格式。
1. 重複步驟 3 以取得新的唯一 ID。
1. 確認設定檔案中的下列設定是否正確:

   | 設定 | 值 |
   |--- |--- |
   | acquisition | The server should be `c00.adobe.com`.   *`appid`*  should equal the `appid`  in your acquisition link. |
   | analytics | 為了測試的目的，請將反向連結逾時設為具有足夠的時間 (60 秒以上) 來手動傳送廣播。您可以在測試結束後將逾時設定還原為原始值。 |

1. 將裝置與電腦連接，解除安裝應用程式，然後重新安裝。
1. 啟動 ADB 殼層，然後啟動裝置上的應用程式。
1. 使用下列 `adb` 命令傳送廣播:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 完成下列步驟:
   1. 將 `com.adobe.android` 替換為應用程式的封裝名稱。
   1. 將接收器參考更新為應用程式中促銷活動追蹤接收器位置的參考。
   1. Replace values that are associated with `utm_content`.
   如果廣播成功，您可以預期類似於以下範例的回應:

   `Broadcasting: Intent 
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
Broadcast completed: result=0`

1. (選擇性) 您可以啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

如果沒有看見上述記錄，請確定您已完成步驟 6 至 12。

下表包含了可能錯誤的額外資訊:

| 錯誤 | 說明 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 回應的格式不正確。 |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 字串的格式不正確。 |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 回應中沒有 contextData 參數。 |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  is not included in  contextData. |
| Analytics - Acquisition referrer timed out. | 無法於 `referrerTimeout` 所定義的時間內取得回應。請增加值，然後再試一次。您也應確定在開啟贏取連結後才安裝應用程式。 |

請記住以下資訊:

* 藉由使用 HTTP 監控工具，即可監控從應用程式傳送的點擊，以便確認贏取屬性。
* 如需有關如何廣播 `INSTALL_REFERRER` 的詳細資訊，請參閱 Google Developers Guide (Google 開發人員指南) 中的 [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns) (測試 Google Play 促銷活動測量)。

* 已針對 Android 4.8.2 的贏取釋出錯誤修正。

   測試之前，請將 SDK 升級至最新版本。

* 您可以使用隨附的 `acquisitionTest.jar` Java 工具來協助您取得唯一 ID 和廣播安裝反向連結，如此將可協助您取得步驟 3 至步驟 12 中的資訊。

   **安裝 Java 工具**

安裝 Java 工具:

1. Download the [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) file.

1. 解壓縮 .jar 檔案。

   您可以在命令列上執行這個檔案。

   例如:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
