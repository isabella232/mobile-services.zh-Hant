---
description: 配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。
keywords: 行動
seo-description: 配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。
seo-title: 體驗應用程式內訊息
solution: Marketing Cloud、Analytics
title: 體驗應用程式內訊息
topic: 量度
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fcebb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 在「體驗」頁面中輸入訊息的名稱。
1. 填妥&#x200B;**[!UICONTROL 輸入]區段中的欄位:**

   * **[!UICONTROL 類型]**：選取應用程式內訊息促銷活動的訊息類型：

      * **[!UICONTROL 全螢幕]**
      * **[!UICONTROL 警報]**
      * **[!UICONTROL 本機通知]**
   * **[!UICONTROL 範本]**

      針對您的內容自訂有主題的回應訊息範本。

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL 自訂]**

      載入您自訂的 HTML 內容 (僅限全螢幕)。您必須提供點進連結和取消連結。

      1. 按一下&#x200B;**[!UICONTROL 「瀏覽」]並下載 HTML 檔案，或將 HTML 文件拖曳到視窗。**
      1. 按一下「**[!UICONTROL 下載範例]」可檢視自訂 HTML 內容範例。**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. 填妥&#x200B;**[!UICONTROL 顯示]區段中的欄位:**

   * **[!UICONTROL 主題]**
   選取訊息的主題。

   * **[!UICONTROL 版面配置]**

      選取裝置畫面上的應用程式版面配置。

   * **[!UICONTROL 影像 URL]**

      影像的 URL。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL 套件影像]**

      應用程式程式碼套件中影像的路徑。此選項用於畫面無影像時，或無可用影像時。舉例來說，若裝置為離線狀態，便無可用的影像。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. 填妥&#x200B;**[!UICONTROL 文字]區段中的欄位:**

   * **[!UICONTROL 檔頭]**

      輸入訊息檔頭的文字。

   * **[!UICONTROL 內容]**

      輸入訊息內容的文字。

1. 填妥&#x200B;**[!UICONTROL 按鈕]區段中的欄位:**

   * **[!UICONTROL 點進按鈕]**

      **[!UICONTROL 點進]按鈕的標籤。**&#x200B;點選此按鈕會計算為成功點進。使用者重新導向至目的地。

   * **[!UICONTROL 目標]**

      選取當使用者點進訊息時要傳送給他們的特定目的地 (例如網頁、深層或混合式連結)。成功點進的重新導向 URL。

      此 URL 可能包含下列資訊:

      * `{userId}`則會以使用者識別碼取代，或在未設定使用者識別碼時為空白。
      * `{trackingId}`則會以aid(與 *s_ vi* Cookie關聯)取代。
      * `{messageId}`則會以應用程式內訊息的唯一ID取代。
      * `{lifetimeValue}`則會以期限值取代，若沒有期限值則加以取代。
      以下是追蹤使用者 ID 的範例: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. 否則，每個平台都支援可讓您開啟或參考您的應用程式的配置 (如果應用程式在開發時就已設定為支援自訂配置)。

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. 系統只會追蹤&#x200B;**[!UICONTROL 深層連結]。** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (可選) 按下列圖示以預覽訊息的配置:

   * **[!UICONTROL 摘要]** 會隱藏預覽窗格。

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL 變更方向]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 對於Watch，方向會從圓形變更為方形表面。

   * **[!UICONTROL 預覽使用者的手錶]**

      若要預覽顯示在使用者手錶上的訊息，請按一下 ![「觀看」圖示](assets/icon_watch.png)。

   * **[!UICONTROL 在使用者的行動電話上預覽]**

      若要預覽您的訊息，因為它會顯示在使用者的行動電話點按 ![手機圖示](assets/icon_phone.png)上。

   * **[!UICONTROL 在使用者的平板電腦上預覽]**

      若要在使用者的平板電腦中預覽您的訊息，請按一下 ![平板電腦圖示](assets/icon_tablet.png)。

      在預覽窗格底部，您可以檢視上一步驟所選對象的說明。您也可以在預覽窗格底部，檢視上一步驟中所選對象的說明。

1. 設定 [排程選項](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)。
