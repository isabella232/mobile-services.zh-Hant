---
description: 在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 adb_deeplink 鍵值的推送裝載中。
seo-description: 在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 adb_deeplink 鍵值的推送裝載中。
seo-title: 使用深層連結實作推送訊息
title: 使用深層連結實作推送訊息
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 75%

---


# 利用深層連結實施推送訊息 {#implement-push-messaging-with-deep-linking}

在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 adb_deeplink 鍵值的推送裝載中。

您可以呼叫 `FirebaseMessagingService` 中的 `remoteMessage.getData().get("adb_deeplink")` 以取得 URL。

>[!TIP]
>
>您可以根據裝載是否含有深層連結 URL 來定義不同的目的。

1. 完成下列其中一項作業:

   * 如果推送裝載中&#x200B;**有**&#x200B;深層連結 URL，請利用此 URL 建立 `ACTION_VIEW` 目的。

      當使用者按一下推播訊息時，會觸發深層連結。

   * 如果深層連結URL **不在推播** ，請建立會開啟您其中一個活動的方式。

## 範例

以下為延伸 `FirebaseMessagingService` 類別的範例實施:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
