---
description: 您可以設定推送訊息和豐富推送訊息的體驗選項，包括名稱、訊息文字和目的地選項。您也可以配置進階選項，包含 iOS 裝置的裝載選項和自訂選項。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 體驗  推送訊息
topic-fix: Metrics
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
exl-id: 9158487e-6ac5-4f17-a8ff-15de0360ab60
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 100%

---

# 體驗：推送訊息 {#experience-push-message}

您可以設定推送訊息和豐富推送訊息的體驗選項，包括名稱、訊息文字和目的地選項。您也可以配置進階選項，包含 iOS 裝置的裝載選項和自訂選項。

1. 在新推送訊息的「對象」頁面上，按一下&#x200B;**[!UICONTROL 體驗]**。

   ![體驗推送訊息畫面](assets/experience-push-message.png)

1. 輸入此訊息的名稱。
1. 在&#x200B;**[!UICONTROL 訊息]**&#x200B;區段的下列欄位中輸入資訊：

   * **[!UICONTROL 內容]**

      指定訊息的文字。您最多可以指定 140 個字元。

   * **[!UICONTROL 媒體 URL]**

      輸入您打算用於推送通知訊息的媒體檔案 URL。如需使用豐富推送通知的需求，請參閱下文的&#x200B;*豐富推送通知需求*。

      >[!IMPORTANT]
      >
      >若要在推送通知中顯示影像或影片，請記住以下事項：
      > * `attachment-url` 資料會在推送裝載中處理。
      > * 媒體 URL 必須可以處理尖峰請求。


   * **[!UICONTROL 目標]**

      選取當使用者點進訊息時要傳送給他們的特定目的地 (例如網頁、深層或混合式連結)。如需詳細資訊，請參閱[目的地](/help/using/acquisition-main/c-create-destinations.md)。

      >[!TIP]
      >
      >若您使用*****&#x200B;網頁連結或&#x200B;**[!UICONTROL 自訂連結]**&#x200B;目的地類型，則不會追蹤這種目的地類型，系統只會追蹤&#x200B;**[!UICONTROL 深層連結]**。

## 豐富推送通知需求

傳送豐富推送通知的需求如下：

* **支援的版本**

   下列版本支援豐富推送通知：
   * Android 4.1.0 或更新版本
   * iOS 10 或更新版本

      >[!IMPORTANT]
      >
      >請記住以下資訊：
      >* 傳送至較舊版本的豐富推送訊息仍會如期傳送，但只會顯示文字。
      >* 目前不支援監看功能。


* **檔案格式**

   以下是支援的檔案格式：
   * 影像：JPG 和 PNG
   * 動畫 (僅限 iOS)：GIF
   * 視訊 (僅限 iOS)：MP4

* **URL 格式**
   * 僅限 HTTPS

* **大小調整**
   * 影像須為 2:1 格式，否則將會被裁切。

如需設定豐富推送通知的詳細資訊，請參閱下列內容：

* [在 Android 中接收推送通知](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [在 iOS 中接收豐富推送通知](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

若要在「體驗」頁面上設定推送訊息：

1. (**選用**) 按一下&#x200B;**[!UICONTROL 顯示進階選項]**&#x200B;連結來設定其他選項：

   * **[!UICONTROL 裝載：資料]**

      在 JSON 提供自訂的推送裝載，並會透過推送或本機通知傳送至應用程式。Android 和 iOS 的上限為 4KB。

   * **[!UICONTROL Apple 選項：類別]**

      提供推送和本機通知的類別。如需詳細資訊，請參閱 *iOS Developer Library (iOS 開發人員資料庫)* 中的[管理您的應用程式通知支援](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9)。

   * **[!UICONTROL Apple 選項：聲音]**

      提供應用程式套件中要播放的聲音檔之檔名。如果未設定，則會播放預設警示聲。如需詳細資訊，請參閱 *iOS Developer Library (iOS 開發人員資料庫)* 中的[管理您的應用程式通知支援](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10)。

   * **[!UICONTROL Apple 選項：可用內容]**

      選取此選項，以便在訊息到達時，iOS 會在背景喚醒應用程式，並允許應用程式根據訊息裝載執行代碼。如需相關資訊，請參閱 *iOS Developer Library* 中的 [Apple 推播通知服務 (Apple Push Notification Service)](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1)。

1. (選用) 按下列圖示即可預覽訊息版面：

   * **[!UICONTROL x 摘要]**

      隱藏預覽窗格。按一下![預覽](assets/icon_preview.png)可重新顯示預覽窗格。

   * **[!UICONTROL 變更方向]**

      若要將預覽方向從縱向變更為橫向模式，請按一下![方向](assets/icon_orientation.png)。若是手錶，方向會從圓形錶面變更為方形錶面。

   * **[!UICONTROL 在使用者的手錶上預覽]**

      若要預覽訊息在使用者手錶上的顯示效果，請按一下 ![手錶圖示](assets/icon_watch.png)。

   * **[!UICONTROL 在使用者的行動電話上預覽]**

      若要預覽訊息在使用者行動電話上的顯示效果，請按一下 ![電話圖示](assets/icon_phone.png)。

   * **[!UICONTROL 在使用者的平板電腦上預覽]**

      若要預覽訊息在使用者平板電腦上的顯示效果，請按一下 ![平板電腦圖示](assets/icon_tablet.png)。
   在預覽窗格底部，您可以檢視上一步驟所選對象的說明。

1. (**選用**) 按一下&#x200B;**[!UICONTROL 測試]**&#x200B;推送您的訊息至指定裝置，以用於進行測試。
1. 選取服務並輸入至少一個想要推送訊息的裝置之推送代號。

   以逗號分隔的清單指定代號，即可推送訊息至一個以上裝置。

1. 設定訊息的排程選項。

   如需詳細資訊，請參閱[排程：推送訊息](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)。
