---
description: 以下資訊可協助您往返 V3 贏取促銷活動連結 (根據裝置指紋)。
seo-description: 以下資訊可協助您往返 V3 贏取促銷活動連結 (根據裝置指紋)。
seo-title: 測試 V3 贏取
solution: Marketing Cloud,Analytics
title: 測試 V3 贏取
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

以下資訊可協助您往返 V3 贏取促銷活動連結 (根據裝置指紋)。

>[!IMPORTANT]
>
> V3 贏取會參照您在 Adobe Mobile Services 使用者介面中透過「贏取產生器」所建立的贏取連結。若要使用此功能，您必須將 iOS SDK 升級至 4.6.0 版或更新版本。

如果行動應用程式尚未在 App Store 上架，在您建立促銷活動連結後，請選取任一行動應用程式作為目的地。這只會影響贏取伺服器將您重新導向的應用程式 (在您點選贏取連結後)，而不會影響測試連結的能力。

1. 完成[「行動應用程式贏取」](/help/ios/acquisition-main/acquisition.md)中的先決條件任務。
1. 導覽至 Adobe Mobile Services 使用者介面中的&#x200B;**[!UICONTROL 「贏取產生器」]，然後產生贏取促銷活動 URL。**

   例如:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   如果您在贏取連結中同時參照了 iOS 和 Android 應用程式，請使用 Apple Store 作為預設商店。
1. 在電腦的瀏覽器上開啟剛才產生的連結，並前往 `https://c00.adobe.com/v3/<appid>/end`。

   您應會在 JSON 回應中看見 `contextData`:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. 確認設定檔案中的下列設定是否正確:

   | 設定 | 值 |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. *`appid`* should equal the *`appid`* in your acquisition link. |
   | analytics | `referrerTimeout` 的值應大於 0。 |


1. (條件式) 如果應用程式設定檔案中的 `ssl` 設定為 true，請更新您的贏取連結，以使用 HTTPS 通訊協定。
1. 按一下您計畫安裝應用程式之行動裝置所產生的連結。

   Adobe 伺服器 (`c00.adobe.com`) 會儲存裝置指紋，然後重新導向至 App Store。您不必僅為了測試而下載應用程式。
1. 在您於步驟 6 中使用的同一行動裝置上，首次啟動應用程式。

   您可以刪除應用程式並重新安裝 (如有必要)。
1. (選擇性) 您可以啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   如果沒有看見上述記錄，請確定您已完成步驟 4 及步驟 5。

   以下是有關可能錯誤的一些資訊：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`發生網路錯誤。

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

         您應會看見兩則傳送至贏取伺服器的要求，一為 `/v3/<appid>/start`，一為 `/v3/<appid>/end`。使用者代理程式中傳送的項目若有所不同，可能會造成屬性失效。

         >[!TIP]
         >
         >請確 `https://c00.adobe.com/v3/<appid>/start` 定 `https://c00.adobe.com/v3/<appid>/end` 值與使用者代理值相同。

      * 贏取連結和來自 SDK 的點擊應使用相同的 HTTP/HTTPS 通訊協定。

         若這兩者分別使用不同通訊協定 (舉例來說，連結使用的是 HTTP，而 SDK 使用 HTTPS)，則每個要求的 IP 位址可能會有所不同 (發生在某些電信業者上)，且屬性可能會失效。
