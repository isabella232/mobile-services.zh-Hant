---
description: 您可在 Android 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。
seo-description: 您可在 Android 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。
seo-title: 接收豐富推送通知
title: 接收豐富推送通知
uuid: 4a0340a6-666b-49b6-907a-9afc966dfda
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

您可在 Android 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

如果應用程式在前景中執行，則會由延伸 `FirebaseMessagingService` 類別的應用程式來處理推送訊息，且會透過下列方式在資訊清單檔案中宣告:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>包含 `onMessageReceived()` 實作的類別會處理收到的資料。

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. 使用的鍵值為 `attachment-url`，如下列程式碼範例所示:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. 為了確保一律顯示大型影像，請設定原生 `Notification.BigPictureStyle`。

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

以下為含有影像的豐富推送通知範例:

![](assets/rich-push-notification_example.png)

如需 Android 豐富推送通知的詳細資訊，請參閱[與豐富通知互動](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html)。
