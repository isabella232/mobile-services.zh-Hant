---
description: Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。
seo-description: Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。
seo-title: 推送訊息
solution: Marketing Cloud,Analytics
title: 推送訊息
topic: 開發人員和實施
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# 推送訊息 {#push-messaging}

Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您輕鬆回報因點進推送訊息而開啟您應用程式的使用者。

若要使用推送訊息，您&#x200B;**必須**&#x200B;有 SDK 4.6 版或更新版本。

>[!IMPORTANT]
>
>請勿在應用程式內手動設定 Experience Cloud ID。這樣會建立新的唯一使用者，且因其選單加入狀態將不會收到推送訊息。例如，使用者已選擇加入在您的應用程式中接收推送訊息記錄。登入後，若您在應用程式內手動設定 ID，便會建立新的唯一使用者，且未選擇加入接收推送訊息。這個新使用者不會收到您的推送訊息。
>
>不支援將您的應用程式移動到新的報表套裝。若您移轉到新報表套裝，推送設定可能會損毀，且訊息可能無法傳送。

## 啟用推送訊息 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>如果您的應用程式已設定透過 Firebase Cloud Messaging (FCM) 傳訊，即可能已完成以下部分步驟。

1. 確認 `ADBMobileConfig.json` 檔案包含推送訊息必需的設定。

   `"marketingCloud"` 物件必須有針對推送訊息設定的 `"org"` 屬性。

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

1. 您必須使用 `Config.setPushIdentifier(final String registrationId)` 方法，將註冊 ID/代號傳遞至 SDK。

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. 在 `collectLifecycleData` 方法中傳遞活動以啟用報告。

   以下為啟用推送點進報告的需求:

   * 在 `FireBaseMessageService` 實施中，包含訊息資料 (透過 RemoteMessage 物件傳遞至 `onMessageReceived` 方法) 的套件物件必須在點進上新增至用來開啟目標活動的目的。您可以透過 `putExtras` 方法完成這項操作。如需詳細資訊，請參閱 [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))。
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 在點進的目標活動中，活動必須以 `collectLifecycleData` 呼叫傳遞至 SDK。

      請記住以下資訊:

      * 使用 `Config.collectLifecycleData(this)` 或 `Config.collectLifecycleData(this, contextData)`。

      * **請勿**&#x200B;使用 `Config.collectLifecycleData()`。



