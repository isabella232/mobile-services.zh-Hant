---
description: 下列指示可協助您使用以裝置指紋為基礎的行銷連結來回往返贏取促銷活動。
keywords: android;library;mobile;sdk
seo-description: 下列指示可協助您使用以裝置指紋為基礎的行銷連結來回往返贏取促銷活動。
seo-title: 測試Marketing Link贏取
solution: Marketing Cloud,Analytics
title: 測試Marketing Link贏取
topic: 開發人員和實施
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

下列指示可協助您使用以裝置指紋為基礎的行銷連結來回往返贏取促銷活動。

1. 完成[「行動應用程式贏取」](/help/ios/acquisition-main/acquisition.md)中的先決條件任務。
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   例如:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   您應會在 JSON 回應中看見 contextData:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 確認設定檔案中的下列設定是否正確:

   | 設定 | 值 |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` should equal the  *`appid`* in your acquisition link. |
   | analytics | `referrerTimeout` 的值應大於 0。 |

1. (條件式) 如果應用程式設定檔案中的 SSL 設定為 `false`，請更新您的贏取連結，改採 HTTP 通訊協定，而非 HTTPS。
1. 在您要安裝應用程式的行動裝置上，按一下剛才產生的連結。

   Adobe 伺服器 (`c00.adobe.com`) 會儲存裝置指紋，然後重新導向至 App Store。您不必僅為了測試而下載應用程式。
1. 在您於步驟 6 中使用的同一行動裝置上，首次啟動應用程式。

   您可以刪除應用程式並重新安裝 (如有必要)。
1. (選擇性) 啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   如果您未看到這些記錄檔，請確認您已完成步驟4和5。

   以下是有關可能錯誤的一些資訊：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      發生網路錯誤。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      回應的格式不正確。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      回應中沒有 `contextData` 參數。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` 不包含在中 `contextData`。

   * `Analytics - Acquisition referrer timed out`

      無法於 `referrerTimeout` 所定義的時間內取得回應。請增加值，然後再試一次。您也應確定在開啟贏取連結後才安裝應用程式，而且使用的網路應與您點選 URL 並開啟應用程式時所用的網路相同。

請記住以下資訊:

* 贏取伺服器會根據連結點擊 (步驟 6) 和應用程式啟動時 (步驟 7) 所記錄的 IP 位址和使用者代理程式資訊，來提供屬性配對。

   您應位於與您點選 URL 以及開啟應用程式時所用的同一網路之中。

* 藉由使用 HTTP 監控工具，即可監控從應用程式傳送的點擊，以便提供贏取屬性的驗證。

   您應會看見兩則傳送至贏取伺服器的要求，一為 `/v3/<appid>/start`，一為 `/v3/<appid>/end`。

* 使用者代理程式中傳送的項目若有所不同，可能會造成屬性失效。

   請確 `https://c00.adobe.com/v3/<appid>/start` 定 `https://c00.adobe.com/v3/<appid>/end` 值與使用者代理值相同。

* 贏取連結和來自 SDK 的點擊應使用相同的 HTTP/HTTPS 通訊協定。

   If the link and the hit are using different protocols, where for example, the link uses HTTP and the SDK uses HTTPS, the IP address might differ on some carriers for each request. 這可能會造成屬性失效。

* 行銷連結會在伺服器端快取10分鐘的過期時間。

   When you make changes to Marketing Links, you should wait about 10 minutes before using the links.