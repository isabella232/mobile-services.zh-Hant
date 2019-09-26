---
description: Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.
keywords: 行動
seo-description: Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.
seo-title: Apple Universal Links and Android App Links
solution: Marketing Cloud,Analytics
title: Apple Universal連結和Android應用程式連結
topic: 量度
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal連結和Android應用程式連結{#universal-links-and-app-links}

「通用連結」(iOS)和「應用程式連結」(Android)可讓您連線至iOS或Android應用程式中的深層連結。

>[!IMPORTANT]
>
>從iOS 9.2開始，不支援深層連結。 您必須使用Apple Universal Links來深入連結至您的應用程式或網站。

## 通用連結 {#section_F8147944679A42E59CF4FD8814E5EF12}

Universal Links allow you to connect to deep links in your iOS app and are supported in iOS 9.2 or later. 當存取「通用連結」時，iOS會將連結直接重新導向至您應用程式中的Deeplink。 如果您的應用程式未安裝，它會改為在瀏覽器中開啟您網站的URL。 For more information about Universal Links, see Support Universal Links.[](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

## App Links

「應用程式連結」可讓您連線至Android應用程式中的深層連結，且在Android 6.0或更新版本中受支援。 當存取「應用程式連結」時，Android會將連結直接重新導向至您應用程式中的Deeplink。 如果您的應用程式未安裝，它會改為在瀏覽器中開啟您網站的URL。 For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 使用通用或應用程式連結建立行銷連結 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以建立使用通用或應用程式連結的行銷連結。

### 設定通用連結

1. 若要在iOS應用程式中設定「通用連結」，請前往「在Apple中 [處理通用連結」](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. 在Adobe Mobile services中，設定網站關聯檔案：

   a.在Mobile services首頁中，選取您要設定通用連結的應用程式。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the iOS app that handles the Universal Links is added to the Add App Store Apps section.****

   >[!TIP]
   >
   >如果未 **[!UICONTROL 顯示「新增App Store應用程式]** 」區段，請按一下「 **[!UICONTROL 新增App Store應用程式」連結]** 。

   d.在「通用 **[!UICONTROL 連結和應用程式連結選項」區段中]** ，選取iOS應用程式並輸入應用程式ID。

   f.按一下 **[!UICONTROL 儲存]**。

   您必須至少提供一個iOS應用程式選擇和一個應用程式ID，否則您會收到錯誤訊息。

   >[!IMPORTANT]
   >
   >您可以按一下通用連結和應用程式連結選項區段裡的「更新」以更新文件。However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用通用連結

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.按一下 **[!UICONTROL 建立新]**。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d.如果您在上述的「在Adobe Mobile Services中設定網站關聯檔案」區段中設定了網站關聯檔案 ** ，則預設會選取此選項。

   如果您未設定檔案，「使用通用連 **[!UICONTROL 結或應用程式連結」選項會停用，並]** 預設選取「使用插入式連結 **** 」。

   e.如果選取「 **[!UICONTROL 使用通用連結或應用程式連結]** 」選項，則會 **[!UICONTROL 顯示「自訂路徑]** 」欄位。

   這容許使用者根據網域和任何查詢參數定義 URL 路徑。例如，若您輸入 您 `my/universal/link?os=9.2`的完整行銷連結URL變 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`成

   f.按一下「 **[!UICONTROL 決策]** 」頁籤並配置決策樹。

   h.如果已安裝iOS應用程式，應用程式會使用其邏輯來處理Deeplink。 當應用程式未安裝時，最終目標僅會做為備援。 由於未安裝應用程式，因此最終目的地只能是網頁連結或應用程式商店。

   i.按一下 **[!UICONTROL 儲存]**。

>[!TIP]
>
>儲存行銷連結後，行銷連結選項便無法變更。 This is because you do not want to change the behavior of the Marketing Links that may have already been distributed.


### Configure an App Link

1. To set up App Links in your Android app, go to Add Android App Links.[](https://developer.android.com/studio/write/app-link-indexing)

1. In Adobe Mobile Services, set up the site-association documents:

   a.在Mobile services首頁中，選取您要設定應用程式連結的應用程式。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the Android app that handles Universal Links or App Links is added to the Add App Store Apps section.****

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Scroll to the Universal Links and App Links Options section.****

   e.按一下「 **[!UICONTROL 應用程式連結(Android)]** 」標籤。

   f.選取Android應用程式，然後輸入SHA-256憑證指紋。

   g. Click Save.****

   You must provide at least one Android app selection and one SHA-256 certificate, or you will receive an error.

   >[!IMPORTANT]
   >
   >您可以按一下&#x200B;****&#x200B;通用連結和應用程式連結選項]區段裡的「**[!UICONTROL 更新]」以更新文件。[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Use an App Link

1. In Adobe Mobile Services, create a Marketing Link that uses App Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.按一下 **[!UICONTROL 建立新]**。

   c.在「行銷 **[!UICONTROL 連結選項」區段中]** ，選 **[!UICONTROL 取「使用通用連結或應用程式連結」]**。

   d. If you configured the site-association documents from step 2, this option is selected by default.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e.如果 **[!UICONTROL 選取「使用通用連結」或「應用程式連結]** 」，則會 **[!UICONTROL 顯示「自訂路徑]** 」欄位。

   這容許使用者根據網域和任何查詢參數定義 URL 路徑。例如，若您輸入 , your full Marketing Link URL becomes .`my/app/link?os=6.0``https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`

   f.按一下「 **[!UICONTROL 決策]** 」頁籤並配置決策樹。

   g.如果已安裝Android應用程式，應用程式會使用其邏輯來處理Deeplink。

   最終目的地僅會做為未安裝應用程式時的備援案例。 由於未安裝應用程式，因此最終目的地只能是網頁連結或應用程式商店。

   h.按一下 **[!UICONTROL 儲存]**。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. This is because you do not want to change the behavior of the Marketing Links that may have already been distributed.

## 使用行銷連結

您現在可以在訊息和應用程式中的其他區域使用這些行銷連結。

>[!IMPORTANT]
>
>您不會看到「通用連結」或「應用程式連結」的點按追蹤計數，也無法使用插入式連結。

