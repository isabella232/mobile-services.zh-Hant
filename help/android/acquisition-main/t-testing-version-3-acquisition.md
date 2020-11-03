---
description: 以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。
keywords: android;library;mobile;sdk
seo-description: 以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。
seo-title: 測試第 3 版贏取
solution: Experience Cloud,Analytics
title: 測試第 3 版贏取
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '820'
ht-degree: 100%

---


# 測試 V3 贏取 {#testing-version-acquisition}

以下資訊可協助您在 Android 裝置上往返版本 3 贏取促銷活動連結。

>[!IMPORTANT]
>
>第 3 版贏取會參照您在 Adobe Mobile Services 使用者介面中透過「贏取建立器」所建立的贏取連結。若要使用此功能，您必須升級至 Experience Cloud 解決方案 4.6.0 或更新版本的 Android SDK 4.x。

如果 Google Play 尚未提供行動應用程式，當您建立行銷活動連結時，您可以選取任何行動應用程式作為目的地。這只會影響您點擊贏取連結後，贏取伺服器將您重新導向所抵達的應用程式，不會影響測試連結的功能。查詢字串參數會傳遞至 Google Play 商店，然後在安裝時傳遞至應用程式，作為促銷活動廣播的一部分。往返行動應用程式贏取測試需要模擬此廣播類型。

>[!IMPORTANT]
>
>如果您是使用 Google Play Install Referrer API 來實作，則在您的應用程式出現在 Google Play 商店中之前，無法測試贏取。

應用程式必須是全新安裝，或資料已全部清除 (在&#x200B;**[!UICONTROL 設定]**&#x200B;中進行)，且每次執行測試時皆須如此。這樣即可確保應用程式首次啟動時，與促銷活動查詢字串參數關聯的初始生命週期量度可以順利傳送。

1. 完成[行動應用程式贏取](/help/android/acquisition-main/acquisition.md)中的先決條件任務，然後確定您已為 `INSTALL_REFERRER` 正確實行廣播接收器。

1. 在 Adobe Mobile Services 使用者介面中，按一下&#x200B;**[!UICONTROL 「贏取]** > **[!UICONTROL 行銷連結建立器」]**&#x200B;並產生贏取行銷連結 URL，此 URL 會將 Google Play 設為 Android 裝置的目的地。

   如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。

   例如, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >如果您在贏取連結中同時參照了 Android 和 iOS 應用程式，請使用 Google Play 做為預設商店。

1. 在電腦的瀏覽器中開啟剛才產生的連結。

   系統會將您重新導向至另一頁面 (其 URL 類似下列範例):
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 複製 `utm_content%3D` 後方的唯一 ID。

   以上一個範例來說，ID 為 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

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
   | acquisition | 伺服器應為 `c00.adobe.com`，且 *`appid`* 應與您贏取連結中的 `appid` 相等。 |
   | analytics | 為了測試的目的，請將反向連結逾時設為具有足夠的時間 (60 秒以上) 來手動傳送廣播。您可以在測試結束後將逾時設定還原為原始值。 |

1. 將裝置與電腦連接，解除安裝應用程式，然後重新安裝。
1. 啟動 ADB 殼層，然後啟動裝置上的應用程式。
1. 使用下列 `adb` 命令傳送廣播:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 完成下列步驟:
   1. 將 `com.adobe.android` 替換為應用程式的封裝名稱。
   1. 將接收器參考更新為應用程式中促銷活動追蹤接收器位置的參考。
   1. 替換與 `utm_content` 關聯的值。

   如果廣播成功，您可以預期類似於以下範例的回應:

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (選擇性) 您可以啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

若未看見前述記錄，請確認您已完成步驟 6 到 12。

下表羅列可能錯誤的額外資訊：

| 錯誤 | 說明 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 回應的格式不正確。 |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 字串的格式不正確。 |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 回應中沒有 contextData 參數。 |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | contextData 中未含有 `a.referrer.campaign.name`。 |
| Analytics - Acquisition referrer timed out. | 無法於 `referrerTimeout` 所定義的時間內取得回應。請增加值，然後再試一次。您也應確定在開啟贏取連結後才安裝應用程式的。 |

請記住以下資訊:

* 使用 HTTP 監控工具可監控從應用程式傳送的點擊，以便確認贏取屬性。
* 如需有關如何廣播 `INSTALL_REFERRER` 的詳細資訊，請參閱 Google Developers Guide (Google 開發人員指南) 中的 [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns) (測試 Google Play 促銷活動測量)。

* 已針對 Android 4.8.2 的贏取發行錯誤修正。

   測試之前，請先將 SDK 升級至最新版本。

* 您可以使用隨附的 `acquisitionTest.jar` Java 工具來協助您取得唯一 ID 和廣播安裝反向連結，如此將可協助您取得步驟 3 至步驟 12 中的資訊。

   **安裝 Java 工具**

安裝 Java 工具：

1. 下載 [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) 檔案。

1. 解壓縮 .jar 檔案。

   您可以在命令列上執行該檔案。

   例如:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
