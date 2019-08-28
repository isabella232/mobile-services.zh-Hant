---
description: 通用連結(iOS)和App Links(Android)可讓您連線至iOS或Android應用程式中的深層連結。
keywords: 行動
seo-description: 通用連結(iOS)和App Links(Android)可讓您連線至iOS或Android應用程式中的深層連結。
seo-title: Apple Universal Links和Android應用程式連結
solution: Marketing Cloud、Analytics
title: Apple Universal Links和Android應用程式連結
topic: 量度
uuid: 8d6441dc-4307-4454-95ea-d77 EC796 f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links和Android應用程式連結{#universal-links-and-app-links}

通用連結(iOS)和App Links(Android)可讓您連線至iOS或Android應用程式中的深層連結。

>[!IMPORTANT]
>
>從iOS9.2開始，不支援深層連結。您必須使用Apple Universal Links深入連結您的應用程式或網站。

## 通用連結 {#section_F8147944679A42E59CF4FD8814E5EF12}

通用連結可讓您連線至iOS應用程式中的深層連結，並在iOS9.2或更新版本中受到支援。存取通用連結時，iOS會直接將連結重新導向至應用程式中的深層連結。如果未安裝應用程式，則會改為在瀏覽器中開啓網站的URL。如需通用連結的詳細資訊，請參閱 [支援通用連結](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)。

## 應用程式連結

應用程式連結可讓您連線至Android應用程式中的深層連結，並且在Android6.0或更新版本中受到支援。存取應用程式連結時，Android會直接將連結重新導向至應用程式中的深層連結。如果未安裝應用程式，則會改為在瀏覽器中開啓網站的URL。For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 使用通用或應用程式連結建立行銷連結 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以建立使用通用或應用程式連結的行銷連結。

### 設定Universal Link

1. 若要在iOS應用程式中設定通用連結，請前往 [「在Apple中處理通用連結](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)」。

2. 在Adobe Mobile Services中，設定網站關聯文件：

   a. 在Mobile Services首頁中，選取您要設定通用連結的應用程式。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 確保處理通用連結的iOS應用程式已新增至 **[!UICONTROL 「新增應用程式商店應用程式]** 」區段。

   >[!TIP]
   >
   >如果 **[!UICONTROL 「新增App Store應用程式]** 」區段未顯示，請按一下 **[!UICONTROL 「新增App Store App]** 」連結。

   d. 在 **[!UICONTROL 「通用連結」和「應用程式連結選項]** 」區段中，選取iOS應用程式並輸入應用程式ID。

   f. 按一下 **[!UICONTROL 「儲存]**」。

   您至少必須提供一個iOS應用程式選擇和一個應用程式ID，否則會收到錯誤。

   >[!IMPORTANT]
   >
   >您可以按一下通用連結和應用程式連結選項區段裡的「更新」以更新文件。However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用Universal Link

1. 在Adobe Mobile Services中，建立使用通用連結的行銷連結：

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 按一下 **[!UICONTROL 「新建]**」。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. 如果您在上述「 *Adobe Mobile Services* 」區段中設定網站關聯文件，則預設會選取此選項。

   如果您未設定文件，則會停用 **[!UICONTROL 「使用通用連結」或「應用程式連結」]** 選項，預設會選取「 **** 使用插入式連結」。

   e. 如果選取 **[!UICONTROL 「使用通用連結」或「應用程式連結」]** 選項，則會顯示 **[!UICONTROL 「自訂路徑]** 」欄位。

   這容許使用者根據網域和任何查詢參數定義 URL 路徑。例如，若您輸入`my/universal/link?os=9.2`就會變成您的完整行銷連結URL `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`。

   f. 按一下 **[!UICONTROL 「決策]** 」標籤並設定您的決策樹。

   h. 如果iOS應用程式已安裝，應用程式會使用其邏輯來處理深層連結。最終目的地僅在未安裝應用程式時做為備援。由於未安裝應用程式，最終目的地只能是網頁連結或應用程式商店。

   i. 按一下 **[!UICONTROL 「儲存]**」。

>[!TIP]
>
>儲存行銷連結後，就無法變更行銷連結選項。這是因為您不想變更可能已經分發的行銷連結行為。


### 設定應用程式連結

1. 若要在Android應用程式中設定應用程式連結，請前往 [「新增Android應用程式連結](https://developer.android.com/studio/write/app-link-indexing)」。

1. 在Adobe Mobile Services中，設定網站關聯文件：

   a. 在Mobile Services首頁中，選取您要設定應用程式連結的應用程式。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 確保處理通用連結或應用程式連結的Android應用程式已新增至 **[!UICONTROL 「新增應用程式商店應用程式]** 」區段。

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. 捲動至 **[!UICONTROL 「通用連結」和「應用程式連結選項]** 」區段。

   e. 按一下 **[!UICONTROL 「應用程式連結(Android)]** 」索引標籤。

   f. 選取Android應用程式，然後輸入SHA-256憑證指紋。

   g. 按一下 **[!UICONTROL 「儲存]**」。

   您至少必須提供一個Android應用程式選擇和一個SHA-256憑證，否則會收到錯誤。

   >[!IMPORTANT]
   >
   >您可以按一下&#x200B;****&#x200B;通用連結和應用程式連結選項]區段裡的「**[!UICONTROL 更新]」以更新文件。[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用應用程式連結

1. 在Adobe Mobile Services中，建立使用應用程式連結的行銷連結：

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 按一下 **[!UICONTROL 「新建]**」。

   c. 在 **[!UICONTROL 「行銷連結選項]** 」區段中，選取 **[!UICONTROL 「使用通用連結」或「應用程式連結]**」。

   d. 如果您從步驟設定網站關聯文件，預設會選取此選項。

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. 如果選取 **[!UICONTROL 「使用通用連結」或「應用程式連結]** 」，則會顯示 **[!UICONTROL 「自訂路徑]** 」欄位。

   這容許使用者根據網域和任何查詢參數定義 URL 路徑。例如，若您輸入`my/app/link?os=6.0`就會變成您的完整行銷連結URL `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`。

   f. 按一下 **[!UICONTROL 「決策]** 」標籤並設定您的決策樹。

   g. 如果已安裝Android應用程式，應用程式會使用其邏輯來處理深層連結。

   最終目的地僅做為未安裝應用程式時的備援個案。由於未安裝應用程式，最終目的地只能是網頁連結或應用程式商店。

   h.  按一下 **[!UICONTROL 「儲存]**」。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. 這是因為您不想變更可能已經分發的行銷連結行為。

## 使用行銷連結

您現在可以在應用程式的訊息和其他區域使用這些行銷連結。

>[!IMPORTANT]
>
>您不會看到按一下「通用連結」或「應用程式連結」的點擊追蹤計數，也無法使用插播。

