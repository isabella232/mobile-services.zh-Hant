---
description: 您可以傳遞因任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，不須更新程式碼。
seo-description: 您可以傳遞因任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，不須更新程式碼。
seo-title: 應用程式內傳訊
solution: Experience Cloud,Analytics
title: 應用程式內傳訊
topic: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---


# 應用程式內傳訊 {#in-app-messaging}

您可以傳遞因任何分析資料或事件觸發的應用程式內訊息。實施後，訊息會動態傳遞至應用程式，不須更新程式碼。

## 新版 Adobe Experience Cloud SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

>[!IMPORTANT]
>
>我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> 如果您使用 Adobe Experience Platform Mobile SDK 搭配 Adobe Launch，您&#x200B;**必須**&#x200B;同時安裝 Adobe Analytics Mobile Services 擴充功能，方可使用應用程式內訊息和推播通知之類的 Adobe Mobile Services 功能。如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。如需如何將推送訊息及應用程式內訊息與 Experience Cloud SDK 搭配使用的詳細資訊，請參閱[設定推送傳訊](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)與[設定應用程式內傳訊](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)。

>[!IMPORTANT]
>
>若要使用應用程式內傳訊，您&#x200B;**必須**&#x200B;有 SDK 4.2 版或更新版本。

您可以建立訊息，以及定義訊息顯示時間的 Adobe Mobile Services 規則。如需詳細資訊，請參閱[建立應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。若要顯示應用程式內訊息，必須更新 SDK。即使您尚未定義任何訊息，也可以完成這些步驟。在您定義訊息後，訊息會動態傳遞至您的應用程式，且顯示時不含應用程式商店更新。

## 啟用應用程式內傳訊 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔案至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 更新 `AndroidManifest.xml` 檔案以宣告全螢幕活動並啟用訊息通知處理常式:

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

1. 確認 `ADBMobileConfig.json` 檔案包含應用程式內傳訊必需的設定。

   >[!IMPORTANT]
   >
   >`messages` 或 `remotes` 為必要項目。

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

   如果未設定此物件，請從 Adobe Mobile Services 下載更新的 `ADBMobileConfig.json` 檔案。如需詳細資訊，請參閱[開始之前](/help/android/getting-started/requirements.md)。

## 追蹤應用程式內訊息 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Android Mobile SDK 會追蹤您應用程式內訊息的下列量度：

* 全螢幕和警報式應用程式內訊息：

   * **曝光次數**：使用者觸發應用程式內訊息時。
   * **點進次數**: 使用者按下&#x200B;**[!UICONTROL 點進]**&#x200B;時。
   * **取消**: 使用者按下&#x200B;**[!UICONTROL 取消]**&#x200B;時。

* 如果是自訂的全螢幕應用程式內訊息，訊息中的 HTML 內容必須包含正確的程式碼，才能通知 SDK 追蹤以下的按鈕:

   * **點進** (重新導向) 追蹤範例:

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **取消** (關閉) 追蹤範例:

      `adbinapp://cancel`

## 本機後援影像 {#section_DEACC1CE549B4573B556A44A52409941}

建立全螢幕訊息時，您可以選擇指定後援影像。如果您的訊息無法從網路擷取預定影像，SDK 會嘗試從應用程式的資產檔案夾載入同名影像。這可讓您以原始格式顯示訊息，即使使用者離線或無法連線至預定影像亦然。

>[!IMPORTANT]
>
>在 Adobe Mobile Services 中設定訊息時，系統會指定後援影像的資產名稱，您必須確保指定的資源可用。

## 設定通知圖示 {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

以下方法可讓您設定顯示在通知區域的大/小型圖示，以及當通知出現在通知匣時會顯示的大型圖示。

* **Config.setSmallIconResourceId(int resourceId)**

   設定用於 SDK 所建立之通知的小型圖示。此圖示會顯示在狀態列中，亦即當使用者在通知中心看到完整通知時，畫面所顯示的次要影像。

   * 以下是此方法的語法:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   設定用於 SDK 所建立之通知的大型圖示。此圖示是使用者在通知中心查看完整通知時所顯示的主要影像。

   * 以下是此方法的語法:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
