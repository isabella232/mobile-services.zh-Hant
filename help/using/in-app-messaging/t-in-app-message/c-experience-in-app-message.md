---
description: 配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。
keywords: mobile
seo-description: 配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。
seo-title: 體驗  應用程式內訊息
solution: Experience Cloud,Analytics
title: 體驗  應用程式內訊息
topic: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 100%

---


# 體驗: 應用程式內訊息 {#experience-in-app-message}

配置應用程式內訊息的體驗選項，包含類型 (全螢幕、警示或通知) 及顯示、文字及按鈕選項。

1. 在您的應用程式中，依序按一下&#x200B;**[!UICONTROL 「傳訊]** > **[!UICONTROL 管理訊息]** > **[!UICONTROL 建立訊息]** > **[!UICONTROL 建立應用程式內訊息」]**。
1. 在「體驗」頁面中輸入訊息的名稱。
1. 填妥&#x200B;**[!UICONTROL 輸入]**&#x200B;區段中的欄位:

   * **[!UICONTROL 類型]**
為您的應用程式內訊息行銷活動選取訊息類型:

      * **[!UICONTROL 全螢幕]**
      * **[!UICONTROL 警報]**
      * **[!UICONTROL 本機通知]**
   * **[!UICONTROL 範本]**

      針對您的內容自訂有主題的回應訊息範本。

      >[!TIP]
      >
      >只有在選取&#x200B;**[!UICONTROL 全螢幕]**&#x200B;訊息類型時，才會顯示此選項。

   * **[!UICONTROL 自訂]**

      載入您的自訂 HTML 內容 (僅限全螢幕)。您必須提供點進連結和取消連結。

      1. 按一下&#x200B;**[!UICONTROL 「瀏覽」]**&#x200B;並下載 HTML 檔案，或將 HTML 文件拖曳到視窗。
      1. 按一下「**[!UICONTROL 下載範例]**」可檢視自訂 HTML 內容範例。

      >[!TIP]
      >
      >只有在選取&#x200B;**[!F全螢幕]**&#x200B;訊息類型時，才會顯示此選項。



1. 填妥&#x200B;**[!UICONTROL 顯示]**&#x200B;區段中的欄位:

   * **[!UICONTROL 主題]**

   選取訊息的主題。

   * **[!UICONTROL 版面配置]**

      選取裝置畫面上的應用程式版面配置。

   * **[!UICONTROL 影像 URL]**

      影像的 URL。如果您在使用全螢幕範本時遇到調整大小的問題，請參閱[應用程式內傳訊疑難排解](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)中的&#x200B;*我的影像無法完全符合範本所提供的空間*。

   * **[!UICONTROL 套件影像]**

      應用程式程式碼套件中所含影像的路徑。沒有影像時，就會使用此選項。影像無法使用時也是如此。舉例來說，若裝置為離線狀態，便無可用的影像。如果您在使用全螢幕範本時遇到調整大小的問題，請參閱[應用程式內傳訊疑難排解](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)中的&#x200B;*我的影像無法完全符合範本所提供的空間*。


1. 填妥&#x200B;**[!UICONTROL 文字]**&#x200B;區段中的欄位:

   * **[!UICONTROL Header]**

      輸入訊息檔頭的文字。

   * **[!UICONTROL 內容]**

      輸入訊息內容的文字。

1. 填妥&#x200B;**[!UICONTROL 按鈕]**&#x200B;區段中的欄位:

   * **[!UICONTROL 點進按鈕]**

      **[!UICONTROL 點進]**&#x200B;按鈕的標籤。點選此按鈕即計為一次成功的點進。系統會將使用者重新導向至目的地。

   * **[!UICONTROL 目標]**

      選取當使用者點進訊息時要傳送給他們的特定目的地 (例如網頁、深層或混合式連結)。成功點進的重新導向 URL。

      此 URL 可能包含下列資訊:

      * `{userId}`，此資訊會以使用者識別碼取代，如果未設定使用者識別碼，則會留空。
      * `{trackingId}`，此資訊會以 aid (與 *s_vi* Cookie 關聯) 取代。
      * `{messageId}`，此資訊會以應用程式內訊息的唯一 ID 取代。
      * `{lifetimeValue}`，此資訊會以期限值取代；若不存在期限值，則使用 0。

      以下是追蹤使用者 ID 的範例: `https://www.mysite.com?uid={userId}`.

      如果點進 URL 使用 `https://` 或 `https://`，URL 會在應用程式外部的裝置瀏覽器中開啟。否則，每個平台都支援可讓您開啟或參考您的應用程式的配置 (如果應用程式在開發時就已設定為支援自訂配置)。

      >[!TIP]
      >
      >若您使用&#x200B;**[!UICONTROL 網頁連結]**&#x200B;或&#x200B;**[!UICONTROL 自訂連結]**&#x200B;目的地類型，則不會追蹤這種目的地類型，系統只會追蹤&#x200B;**[!UICONTROL 深層連結]**。如需詳細資訊，請參閱[目的地](/help/using/acquisition-main/c-create-destinations.md)。


1. (可選) 按下列圖示以預覽訊息的配置:

   * **[!UICONTROL 摘要]**&#x200B;會隱藏預覽窗格。

      按一下![預覽](assets/icon_preview.png)可重新顯示預覽窗格。

   * **[!UICONTROL 變更方向]**

      若要將預覽方向從縱向變更為橫向模式，請按一下![方向](assets/icon_orientation.png)。若是手錶，方向會從圓形變更為方形錶面。

   * **[!UICONTROL 在使用者的手錶上預覽]**

      若要預覽訊息在使用者手錶上的顯示效果，請按一下 ![手錶圖示](assets/icon_watch.png)。

   * **[!UICONTROL 在使用者的行動電話上預覽]**

      若要預覽訊息在使用者行動電話上的顯示效果，請按一下 ![電話圖示](assets/icon_phone.png)。

   * **[!UICONTROL 在使用者的平板電腦上預覽]**

      若要預覽訊息在使用者平板電腦上的顯示效果，請按一下 ![平板電腦圖示](assets/icon_tablet.png)。

      在預覽窗格底部，您可以檢視上一步驟所選對象的說明。您也可以在預覽窗格底部，檢視上一步驟中所選對象的說明。

1. 設定[排程選項](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)。
