---
description: 通用連結 (iOS) 和應用程式連結 (Android) 可讓您連線至 iOS 或 Android 應用程式中的深層連結。
keywords: mobile
seo-description: 通用連結 (iOS) 和應用程式連結 (Android) 可讓您連線至 iOS 或 Android 應用程式中的深層連結。
seo-title: Apple 通用連結和 Android 應用程式連結
solution: Experience Cloud,Analytics
title: Apple 通用連結和 Android 應用程式連結
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1142'
ht-degree: 100%

---


# Apple 通用連結和 Android 應用程式連結{#universal-links-and-app-links}

通用連結 (iOS) 和應用程式連結 (Android) 可讓您連線至 iOS 或 Android 應用程式中的深層連結。

>[!IMPORTANT]
>
>自 iOS 9.2 起不支援深層連結。您必須使用 Apple 通用連結來深入連結至您的應用程式或網站。

## 通用連結 {#section_F8147944679A42E59CF4FD8814E5EF12}

通用連結可讓您連線至 iOS 應用程式中的深層連結，iOS 9.2 或更新版本支援此類連結。存取通用連結時，iOS 會將連結直接重新導向至您應用程式中的深層連結。如果應用程式未安裝，則會改為在瀏覽器中開啟您網站的 URL。如需通用連結的詳細資訊，請參閱[支援通用連結](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)。

## 應用程式連結

應用程式連結可讓您連線至 Android 應用程式中的深層連結，Android 6.0 或更新版本支援此類連結。存取應用程式連結時，Android 會將連結直接重新導向至您應用程式中的深層連結。如果應用程式未安裝，則會改為在瀏覽器中開啟您網站的 URL。如需應用程式連結的詳細資訊，請參閱[處理 Android 應用程式](https://developer.android.com/training/app-links/index.html)。

## 使用通用或應用程式連結建立行銷連結 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以建立使用通用或應用程式連結的行銷連結。

### 設定通用連結

1. 若要在 iOS 應用程式中設定通用連結，請前往[處理 Apple 中的通用連結](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. 在 Adobe Mobile Services 中，設定網站關聯文件:

   在 Adobe Mobile Services 首頁中，選取您想設定通用連結的應用程式。

   b. 按一下&#x200B;**[!UICONTROL 管理應用程式設定]**。

   c. 確認處理通用連結的 iOS 應用程式已新增至&#x200B;**[!UICONTROL 新增 App Store 應用程式]**&#x200B;區段中。

   >[!TIP]
   >
   >如果&#x200B;**[!UICONTROL 新增 App Store 應用程式]**&#x200B;區段沒有顯示，請按一下&#x200B;**[!UICONTROL 新增 App Store 應用程式]**&#x200B;連結。

   d. 在&#x200B;**[!UICONTROL 通用連結和應用程式連結選項]**&#x200B;區段中，選取 iOS 應用程式並輸入應用程式 ID。

   f. 按一下&#x200B;**[!UICONTROL 儲存]**。

   您必須至少提供一個選定的 iOS 應用程式和一個應用程式 ID，否則您會收到錯誤訊息。

   >[!IMPORTANT]
   >
   >您可以按一下通用連結和應用程式連結選項區段裡的「更新」以更新文件。不過按一下&#x200B;**[!UICONTROL 更新]**&#x200B;時，警告會通知您，過去您建立的通用連結或應用程式連結將會受到影響。

### 使用通用連結

1. 在 Adobe Mobile Services 中，建立使用通用連結的行銷連結:

   a. 從 Mobile Services 首頁中選取應用程式，按一下&#x200B;**[!UICONTROL 「贏取]** > **[!UICONTROL 行銷連結建立器」]**。

   b. 按一下&#x200B;**[!UICONTROL 新建]**。

   c. 在&#x200B;**[!UICONTROL 行銷連結選項]**&#x200B;下，選取&#x200B;**[!UICONTROL 使用通用連結或應用程式連結]**。

   d. 若您已設定上文&#x200B;*在 Adobe Mobile Services 中設定網站關聯文件*&#x200B;中所說明的網站關聯文件，系統會預設選取此選項。

   若尚未設定此文件，**[!UICONTROL 使用通用連結或應用程式連結]**&#x200B;選項會停用，而&#x200B;**[!UICONTROL 使用插入式連結]**&#x200B;預設為選取。

   e. 若選取了&#x200B;**[!UICONTROL 使用通用連結或應用程式連結]**&#x200B;選項，便會顯示&#x200B;**[!UICONTROL 自訂路徑]**&#x200B;欄位。

   這可讓使用者使用任意查詢參數在網域後面定義 URL 路徑。舉例來說，如果您輸入 `my/universal/link?os=9.2`，您的完整行銷連結 URL 就會變成 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`。

   f. 按一下&#x200B;**[!UICONTROL 決策]**&#x200B;分頁標籤並設定決策樹。

   h. 如果已安裝 iOS 應用程式，應用程式會以其邏輯處理深層連結。若未安裝應用程式，最終目的地的功用只有後援。由於應用程式未安裝，最終目的地只能為網頁連結或應用程式商店。

   i. 按一下&#x200B;**[!UICONTROL 儲存]**。

>[!TIP]
>
>行銷連結一經儲存，「行銷連結選項」便不能變更。這是為了防止變更可能已經散佈的行銷連結之行為。


### 設定應用程式連結

1. 若要設定 Android 應用程式中的應用程式連請前往[新增 Android 應用程式連結](https://developer.android.com/studio/write/app-link-indexing)。

1. 在 Adobe Mobile Services 中，設定網站關聯文件:

   a. 在 Adobe Mobile Services 首頁中，選取您想設定應用程式連結的應用程式。

   b. 按一下&#x200B;**[!UICONTROL 管理應用程式設定]**。

   c. 確認處理通用連結或應用程式連結的 Android 應用程式已新增至&#x200B;**[!UICONTROL 新增 App Store 應用程式]**&#x200B;區段中。

   >[!TIP]
   >
   >若此區段並未顯示，請按一下&#x200B;****&#x200B;新增 App Store 應用程式連結。

   d. 捲動至&#x200B;**[!UICONTROL 通用連結和應用程式連結選項]**&#x200B;區段。

   e. 按一下&#x200B;**[!UICONTROL 應用程式連結 (Android)]** 分頁標籤。

   f. 選取 Android 應用程式並輸入 SHA-256 憑證指紋。

   g. 按一下&#x200B;**[!UICONTROL 儲存]**。

   您必須至少提供一個選定的 Android 應用程式和一個 SHA-256 憑證，否則您會收到錯誤訊息。

   >[!IMPORTANT]
   >
   >您可以按一下&#x200B;**[!UICONTROL 通用連結和應用程式連結選項]**&#x200B;區段裡的「**[!UICONTROL 更新]**」以更新文件。不過按一下&#x200B;**[!UICONTROL 更新]**&#x200B;時，警告會通知您，過去您建立的通用連結或應用程式連結將會受到影響。

### 使用應用程式連結

1. 在 Adobe Mobile Services 中，建立使用應用程式連結的行銷連結:

   a. 從 Mobile Services 首頁中選取應用程式，按一下&#x200B;**[!UICONTROL 「贏取]** > **[!UICONTROL 行銷連結建立器」]**。

   b. 按一下&#x200B;**[!UICONTROL 新建]**。

   c. 在&#x200B;**[!UICONTROL 行銷連結選項]**&#x200B;區段中，選取&#x200B;**[!UICONTROL 使用通用連結或應用程式連結]**。

   d. 若您已透過步驟 2 設定網站關聯文件，則此選項預設為選取。

   若尚未設定，**[!UICONTROL 使用通用連結或應用程式連結]**&#x200B;選項會停用，而&#x200B;**[!UICONTROL 使用插入式連結]**&#x200B;會預設為選取。

   e. 若選取了&#x200B;**[!UICONTROL 使用通用連結或應用程式連結]**，便會顯示&#x200B;**[!UICONTROL 自訂路徑]**&#x200B;欄位。

   這可讓使用者使用任意查詢參數在網域後面定義 URL 路徑。舉例來說，如果您輸入 `my/app/link?os=6.0`，您的完整行銷連結 URL 就會變成 `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`。

   f. 按一下&#x200B;**[!UICONTROL 決策]**&#x200B;分頁標籤並設定決策樹。

   g. 如果已安裝 Android 應用程式，應用程式會以其邏輯處理深層連結。

   若未安裝應用程式，最終目的地的功用只有後援案例。由於應用程式未安裝，最終目的地只能為網頁連結或應用程式商店。

   h. 按一下&#x200B;**[!UICONTROL 儲存]**。

>[!TIP]
>
>行銷連結儲存後，**[!UICONTROL 行銷連結選項]**&#x200B;便不能變更。這是為了防止變更可能已經散佈的行銷連結之行為。

## 使用行銷連結

您現在可以在訊息和應用程式中的其他區域使用這些行銷連結。

>[!IMPORTANT]
>
>您不會看到通用連結或應用程式連結的點擊追蹤計數，也無法使用插入式連結。

