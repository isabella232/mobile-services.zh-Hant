---
description: 您可以手動設定URL參數，以建立行銷連結，即時取得新的行動應用程式使用者。
keywords: 行動
seo-description: You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.
seo-title: Manually create Acquisition links
solution: Marketing Cloud,Analytics
title: Manually create Acquisition links
topic: 量度
uuid: d7709203-f793-4982-adaa-9c3c914aca2b
translation-type: tm+mt
source-git-commit: 54e3b2d673356a616987537d20758bef8b044db4

---


# Manually create Acquisition links {#create-acquisition-link-manually}

You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.

>[!IMPORTANT]
>
>此功能需要SDK 4.6版或更新版本。 如需詳細資訊，請參閱「贏 [取必要條件](/help/using/acquisition-main/c-acquisition-prerequisites.md)」。

下圖說明手動建立追蹤連結的元件，並顯示您在手動建立贏取連結時必須正確設定的不同URL參數。

![](assets/acquisition_url.png)

系統會配置此連結來執行適用於行動應用程式的 Google Play Store 或 Apple App Store 平台特定重新導向。如果無法判別目標，預設商店設定為 Apple App Store。安裝應用程式後，自訂內容索引鍵 `my.custom.key:test` 會附加至 Analytics 安裝點擊。

若要手動建立連結，請使用下列 URL 格式:

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>您使用的Android SDK版本對此程式沒有影響。

若是 iOS，請確認您使用正確的通訊協定:

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** if you are using iOS SDK 4.7.0 or later and **[!UICONTROL Use HTTPS]** **is** selected on the Manage App Settings page.

在符合下列條件的情況下:

* `{mobile-services-app-hash}` 與配置檔案中的應用程式標識符相 `acquisition:appid ` 匹配。

   You can locate `{mobile-services-app-hash}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` 是特別命名的標準 URL 查詢參數清單.

以下為參數清單:

* **`a_g_id`**

   Google Play 商店應用程式識別碼.

   * 範例值： `com.adobe.beardcons`

* **`a_g_lo`**

   Google Play 商店地區設定覆寫.

   * 範例值： `ko`

* **`a_i_id`**

   iTunes 應用程式識別碼.

   * 範例值： `835196493`

* **`a_i_lo`**

   iTunes 地區設定覆寫.

   * 範例值： `jp`

* **`a_dd`**

   自動重新導向的預設商店.

   * 範例值： `i | g`

* **`a_cid`**

   自訂 ID 覆寫 (通常 iOS 是 IDFA，Android 是 ADID).

   * 範例值： `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * 範例值： `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   使用者募集活動名稱.

   如果您想比較不同贏取連結的績效，此參數為必需的報表項目。

   * 範例值：2015年首腦會議

* **`ctxa.referrer.campaign.trackingcode`**

   追蹤程式碼

   如果您想比較不同贏取連結的績效，此參數為必需的報表項目。

   * 範例值： `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   來源。

   * 範例值：廣告網路

* **`ctxa.referrer.campaign.medium`**

   媒體

   * 範例值：電子郵件

* **`ctxa.referrer.campaign.content`**

   內容

   * 範例值：影像編號325689

* **`ctxa.referrer.campaign.term`**

   詞語

   * 範例值：遠足和靴子


當您手動建立贏取連結時，請記住下列資訊：

* 不符合上表參數的所有參數，都會視為應用程式商店重新導向的一部分而傳遞。
* All parameters are technically optional, although the link will be nonfunctional, if at least one store ID is specified.

   An example of a store ID is `a_g_id`/ `a_i_id`.

* 如果無法自動判別目的地商店，且沒有提供預設商店，系統便會傳回 404 錯誤。

