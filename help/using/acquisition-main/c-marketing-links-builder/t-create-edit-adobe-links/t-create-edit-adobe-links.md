---
description: 您可以建立或編輯行銷連結，以提供深入連結至您的行動應用程式或您的網站。
keywords: 行動
seo-description: 您可以建立或編輯行銷連結，以提供深入連結至您的行動應用程式或您的網站。
seo-title: 建立或編輯行銷連結
solution: Marketing Cloud、Analytics
title: 建立或編輯行銷連結
topic: 量度
uuid: 305a8265-38de-4d19-8c79-b3912 f5 aae7 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

您可以建立或編輯行銷連結，以提供深入連結至您的行動應用程式或網站。如需詳細資訊，請參閱 [Apple Universal Links和Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. 完成下列其中一項作業:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * 如需編輯現有連結，請在&#x200B;**[!UICONTROL 「標題」]欄中按一下連結的名稱。**

1. 在下列欄位輸入資訊:

   * **[!UICONTROL 行銷連結名稱]**:

      (**Required**) Specify a descriptive name for your Marketing Link. 名稱僅顯示在 Adobe Mobile Services UI 中的行銷連結頁面上。描述性名稱可協助您或組織中的其他人員快速找到特定連結，並可提供其目的的洞察。

   * **[!UICONTROL 唯一追蹤代碼]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. 您可以檢視詳細說明追蹤代碼使用的報告。

   * **[!UICONTROL 新增追蹤內容資料]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. 在&#x200B;**[!UICONTROL 「自訂內容資料」]下拉式清單中，選取預設標籤或您自己的標籤。**&#x200B;上下文資料用於在部署行銷連結時進行報告。

      下列預設集標記可供使用:

      * **自訂上下文資料**&#x200B;指定索引鍵和值。如果您新增自訂內容資料，必須建立處理規則。如需詳細資訊，請參閱 [處理規則概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

      * **來源**&#x200B;指定原始反向連結，例如「電子報」或「首頁」。

      * **Medium**&#x200B;指定行銷媒體，例如「橫幅」或「電子郵件」。

      * **內容**：指定廣告的名稱或ID與連結。

      * **詞語**&#x200B;指定廣告的付費詞語或其他搜尋詞。
1. 按一下&#x200B;**[!UICONTROL 儲存]**。
1. 在下列欄位輸入資訊:

   * **(必要)** 在 **[!UICONTROL 後援URL]**&#x200B;中，指定將使用者導向至目的地無法符合的URL(例如，如果使用者位於桌面或其他不符合目的地規則的平台)。
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      如需詳細資訊，請參閱 [「Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) 」或 [「Apple Universal Links」和「Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)」。

   * **(條件性)** 如果選取 **[!UICONTROL 「通用」或「應用程式連結]** 」，則在 **[!UICONTROL 「自訂路徑]**」中，使用者可以在網域後面定義URL路徑，並使用任何查詢參數。如需詳細資訊，請參閱 [Apple Universal Links和Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. 如果使用者已安裝應用程式，則會顯示插入式登陸頁面。

   如需詳細資訊，請參閱 [插頁廣告](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. 在「目的地」頁面中設定連結。

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL 新增決策]**
      * **[!UICONTROL 新增路徑]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL 作業系統決策]**

         支援的作業系統包括 iOS、Android、AMX 等等

      * **[!UICONTROL 裝置類型]**

         裝置類型包括桌上型電腦、電子閱讀器、遊戲主機、行動電話、數位機上盒等等
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL 網頁連結]**
      * **[!UICONTROL 應用程式深層連結]**
      * **[!UICONTROL 混合式連結]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. 若要追蹤贏取，請使用&#x200B;**[!UICONTROL 「應用程式商店」]目的地類型。**

      如需詳細資訊，請參閱 [建立新連結目的地](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)。




1. 若要儲存行銷連結，請按一下 ![「線上」](assets/icon_elipses.png) 和「 **[!UICONTROL 儲存]**」。
