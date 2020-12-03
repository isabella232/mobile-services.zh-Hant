---
description: 您可以將影像檔案附加至Android通知。 新增視覺元件可大幅提升使用者與推播通知的互動。
seo-description: 您可以將影像檔案附加至Android通知。 新增視覺元件可大幅提升使用者與推播通知的互動。
seo-title: 接收豐富式推播通知
title: 接收豐富式推播通知
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 60%

---


# 接收豐富推送通知 {#receive-rich-push-notifications}

您可以將影像檔案附加至Android通知。 新增視覺元件可大幅提升使用者與推播通知的互動。

## 處理傳入的豐富推送訊息 (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

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
>包含 `onMessageReceived()` 實施的類別會處理收到的資料。

如果推送訊息包含媒體 URL，則該 URL 可用在傳遞至 `onMessageReceived()` 函式的 `RemoteMessage` 參數中。使用的鍵值為 `attachment-url`，如下列程式碼範例所示:

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
>當您設定 `NotificationCompat.BigPictureStyle` 時，可能不會顯示大型影像。為了確保一律顯示大型影像，請設定原生 `Notification.BigPictureStyle`。

## 豐富推送通知範例 {#section_6819316BEDDE45108413B541CA2BB2DC}

以下為含有影像的豐富推送通知範例:

![](assets/rich-push-notification_example.png)

For more information about rich push notifications with Android, see [Engage with Rich Notifications](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
