---
description: 下列說明可協助您利用行銷連結往返贏取促銷活動 (根據裝置指紋)。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 測試行銷連結贏取
topic-fix: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
exl-id: 2fb02b36-172e-4c16-9ef9-13f8288ab8a4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---

# 測試行銷連結贏取 {#testing-marketing-link-acquisition}

下列說明可協助您利用行銷連結往返贏取促銷活動 (以裝置指紋為基礎)。

1. 完成[行動應用程式贏取](/help/ios/acquisition-main/acquisition.md)中的先決條件任務。
1. 在 Adobe Mobile Services 使用者介面中，按一下&#x200B;**[!UICONTROL 行銷連結產生器]**&#x200B;並產生贏取行銷連結 URL，此 URL 會將 App Store 設為 iOS 裝置的目的地。

   例如：

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。


1. 在 iOS 裝置上開啟剛才產生的連結，然後開啟 `https://c00.adobe.com/v3/<appid>/end`。

   您應會在 JSON 回應中看見 contextData：

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 確認設定檔案中的下列設定是否正確：

   | 設定 | 值 |
   |--- |--- |
   | acquisition | 伺服器應為 `c00.adobe.com`，且 `appid` 應與您贏取連結中的 *`appid`* 相等。 |
   | analytics | `referrerTimeout` 的值應大於 0。 |

1. (視條件調整) 如果應用程式設定檔案中的 SSL 設定為 `false`，請更新您的贏取連結，改採 HTTP 通訊協定，而非 HTTPS。
1. 在您要安裝應用程式的行動裝置上，按一下剛才產生的連結。

   Adobe 伺服器 (`c00.adobe.com`) 會儲存裝置指紋，然後重新導向至 App Store。您不必僅為了測試而下載應用程式。
1. 在您於步驟 6 中使用的同一行動裝置上，首次啟動應用程式。

   您可以刪除應用程式並重新安裝 (如有必要)。
1. (選擇性) 啟用 SDK 的偵錯記錄以取得其他資訊。

   如果一切正常運作，您應會看見下列記錄：

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   如果沒有看見這些記錄，請確認您已完成步驟 4 及步驟 5。

   可能錯誤的相關資訊如下：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`：

      發生網路錯誤。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      回應的格式不正確。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      回應中沒有 `contextData` 參數。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` 中未含有 `contextData`。

   * `Analytics - Acquisition referrer timed out`

      無法於 `referrerTimeout` 所定義的時間內取得回應。請增加值，然後再試一次。同時，您也需在安裝應用程式前即確保開啟贏取連結，而且當您按下 URL 並開啟應用程式時，使用的是相同的網路。

請記住以下資訊：

* 贏取伺服器會根據連結點擊 (步驟 6) 和應用程式啟動時 (步驟 7) 所記錄的 IP 位址和使用者代理程式資訊，來提供屬性配對。

   您應位於與您點選 URL 以及開啟應用程式時所用的同一網路之中。

* 藉由使用 HTTP 監控工具，即可監控從應用程式傳送的點擊，以便提供贏取屬性的驗證。

   您應會看見兩則傳送至贏取伺服器的要求，一為 `/v3/<appid>/start`，一為 `/v3/<appid>/end`。

* 使用者代理程式中傳送的項目若有所不同，可能會造成屬性失效。

   確定 `https://c00.adobe.com/v3/<appid>/start` 和 `https://c00.adobe.com/v3/<appid>/end` 具有相同的使用者代理程式數值。

* 贏取連結和來自 SDK 的點擊應使用相同的 HTTP/HTTPS 通訊協定。

   若連結和點擊分別使用不同通訊協定 (舉例來說，連結使用的是 HTTP，而 SDK 使用 HTTPS)，則每個要求的 IP 位址在某些電信業者上可能會有所不同。這可能會造成屬性失效。

* 伺服器會快取行銷連結，並且有 10 分鐘的到期時間。

   若您變更行銷連結，應等待約 10 分鐘再使用這些連結。
