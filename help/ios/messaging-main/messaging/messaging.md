---
description: 此資訊可協助您使用 iOS 應用程式中的應用程式內傳訊。
seo-description: 此資訊可協助您使用 iOS 應用程式中的應用程式內傳訊。
seo-title: 應用程式內傳訊
solution: Marketing Cloud,Analytics
title: 應用程式內傳訊
topic: 開發人員和實施
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 應用程式內傳訊 {#in-app-messaging}

此資訊可協助您使用 iOS 應用程式中的應用程式內傳訊。

若要使用應用程式內傳訊，您&#x200B;**必須**&#x200B;有 SDK 4.2 版或更新版本。

一些要記住的資訊:

* 訊息和定義訊息顯示時機的規則都是在 Adobe Mobile Services 中建立的。如需詳細資訊，請參閱[建立應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。
* 必須在 SDK 中套用本節說明的更新，才能顯示應用程式內訊息。

   >[!TIP]
   >
   >即使您尚未定義任何訊息，也可以完成這些步驟。在您定義訊息後，訊息會動態傳遞至您的應用程式，且顯示時不含應用程式商店更新。

## 啟用應用程式內訊息 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/requirements.md)中的&#x200B;*新增 SDK 和設定檔案至您的專案*。

1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含應用程式內傳訊必需的設定。
1. 若要在啟動時動態更新應用程式內訊息，必須有 `remotes` 物件且已正確設定:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` 或 `remotes` 為必要項目。

   如果未設定這些物件，請從 Adobe Mobile Services 下載更新的 `ADBMobileConfig.json` 檔案。如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/requirements.md)。

## 追蹤應用程式內訊息 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile Services SDK 可為您的應用程式內訊息追蹤以下度量:

* 如果是全螢幕和警示樣式的應用程式內訊息:

   * **[!UICONTROL 曝光次數]**: 使用者觸發應用程式內訊息時。
   * **[!UICONTROL 點進次數]**: 使用者按下&#x200B;**[!UICONTROL 點進]**&#x200B;按鈕時。
   * **[!UICONTROL 取消次數]**: 使用者按下&#x200B;**[!UICONTROL 取消]**&#x200B;按鈕時。

* 如果是自訂的全螢幕應用程式內訊息，訊息中的 HTML 內容必須包含正確的程式碼，才能通知 SDK 追蹤以下的按鈕:

   * **[!UICONTROL 點進]** (重新導向) 追蹤範例: `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL 取消]** (關閉) 追蹤範例: `adbinapp://cancel`

* 如果是本機 (遠端) 通知:

   * **[!UICONTROL 曝光次數]**: 使用者觸發通知時。
   * **[!UICONTROL 開啟次數]**: 使用者從通知開啟應用程式時。
   以下是如何包含開啟追蹤的範例:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## 本機後援影像 {#section_DEACC1CE549B4573B556A44A52409941}

在 Adobe Mobile Services 中立全螢幕訊息時，您可以選擇指定後援影像。如果您的訊息無法從 Web 擷取其要使用的影像，SDK 會嘗試從應用程式套件載入相同名稱的影像。這讓您即使在使用者離線，或無法連線至預先決定的影像時，也可以用原本的形式來顯示訊息。

在 Adobe Mobile Services 中設定訊息時，系統會指定後援影像的資產名稱。

>[!IMPORTANT]
>
>您必須確保指定的資源可用。

