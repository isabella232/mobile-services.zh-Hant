---
description: Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。
seo-description: Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。
seo-title: 推送訊息
solution: Marketing Cloud,Analytics
title: 推送訊息
topic: 開發人員和實施
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。

若要使用推送訊息，您&#x200B;**必須**&#x200B;有 SDK 4.6 版或更新版本。

>[!IMPORTANT]
>
>Do not manually set the Experience Cloud ID inside your app. 這樣會建立新的唯一使用者，且因其選單加入狀態將不會收到推送訊息。例如，使用者已選擇加入在您的應用程式中接收推送訊息記錄。登入後，若您在應用程式內手動設定 ID，便會建立新的唯一使用者，且未選擇加入接收推送訊息。這個新使用者不會收到您的推送訊息。
>
>不支援將應用程式移至新的報表套裝。 若您移轉到新報表套裝，推送設定可能會損毀，且訊息可能無法傳送。

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>如果您的應用程式已設定為透過Firebase Cloud Messaging(FCM)使用傳訊，下列部分步驟可能已完成。

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. 使用 Firebase Cloud Messaging (FCM) API 取得註冊 ID/Token。

   * 如需有關設定 FCM 的詳細資訊，請參閱[在 Android 上設定 Firebase Cloud Messaging 用戶端應用程式](https://firebase.google.com/docs/cloud-messaging/android/client)。
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. 在 `collectLifecycleData` 方法中傳遞活動以啟用報告。

   以下為啟用推送點進報告的需求:

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. 這可以使用方法 `putExtras` 完成。 For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 在點進的目標活動中，活動必須以 `collectLifecycleData` 呼叫傳遞至 SDK。

      請記住以下資訊:

      * 使用 `Config.collectLifecycleData(this)` 或 `Config.collectLifecycleData(this, contextData)`。

      * Do **not** use `Config.collectLifecycleData()`.



