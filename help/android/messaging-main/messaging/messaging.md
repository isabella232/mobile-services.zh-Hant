---
description: 您可以傳遞由任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，且不需要更新程式碼。
seo-description: 您可以傳遞由任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，且不需要更新程式碼。
seo-title: 應用程式內傳訊
solution: Marketing Cloud、Analytics
title: 應用程式內傳訊
topic: 開發人員和實施
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 應用程式內傳訊 {#in-app-messaging}

您可以傳遞由任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，且不需要更新程式碼。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

>[!IMPORTANT]
>
>我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>若要使用應用程式內傳訊，您&#x200B;**必須**&#x200B;有 SDK 4.2 版或更新版本。

您可以在 Adobe Mobile Services 中建立訊息，並定義訊息顯示時機的規則。如需詳細資訊，請參閱[建立應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。若要顯示應用程式內訊息，必須更新 SDK。即使您尚未定義任何訊息，也可以完成這些步驟。在您定義訊息後，訊息會動態傳遞至您的應用程式，且顯示時不含應用程式商店更新。

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期* 中 [的新增SDK和設定檔案至IntelliJ IDEA或Eclipse專案](/help/android/getting-started/dev-qs.md)。

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   如果您選取了一個模式配置，請為訊息選取以下其中一種主題:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   例如:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 在每個 `collectLifecycleData` 呼叫中，傳遞 `this` 以提供參考給目前的活動:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` 或為 `remotes` 必要項目。

   若要在啟動時動態更新應用程式內訊息，必須有 `remotes` 物件且已正確設定:

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

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 如需詳細資訊，請參閱[開始之前](/help/android/getting-started/requirements.md)。

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Android Mobile SDK 可為您的應用程式內訊息追蹤以下量度:

* 如果是全螢幕和警示樣式的應用程式內訊息:

   * **曝光次數**: 使用者觸發應用程式內訊息時。
   * **點進**&#x200B;次數：使用者按下 **[!UICONTROL 「點進]**」。
   * **取消**：使用者按下 **[!UICONTROL 取消]**。

* 如果是自訂的全螢幕應用程式內訊息，訊息中的 HTML 內容必須包含正確的程式碼，才能通知 SDK 追蹤以下的按鈕:

   * **點進** (重新導向)範例追蹤：

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **取消** (關閉)範例追蹤：

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

建立全螢幕訊息時，您可以選擇指定後援影像。如果您的訊息無法從 Web 擷取其要使用的影像，SDK 會嘗試從應用程式資產資料夾載入相同名稱的影像。這讓您即使在使用者離線，或無法連線至預先決定的影像時，也可以用原本的形式來顯示訊息。

>[!IMPORTANT]
>
>當您在Adobe Mobile Services中設定訊息時，會指定備援影像資產名稱，您必須確保指定的資源可用。

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

以下方法可讓您設定顯示在通知區域的大/小型圖示，以及當通知出現在通知匣時會顯示的大型圖示。

* **Config.setSmallIconResourceId(int resourceId)**

   設定用於 SDK 所建立之通知的小型圖示。此圖示在使用者於通知中心查看完整通知時會出現在狀態列，且是所顯示影像的次要影像。

   * 以下是此方法的語法:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   設定用於 SDK 所建立之通知的大型圖示。此圖示是當使用者在通知中心看到完整通知時所顯示的主要影像。

   * 以下是此方法的語法:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
