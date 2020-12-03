---
description: 在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 adb_deeplink 鍵值的推送裝載中。
seo-description: 在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 adb_deeplink 鍵值的推送裝載中。
seo-title: 使用深層連結實作推送訊息
title: 使用深層連結實作推送訊息
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 93%

---


# 利用深層連結實施推送訊息 {#implement-push-messaging-with-deep-linking}

在您於 Adobe Mobile Services 使用者介面中設定深層連結 URL 後，此 URL 會位於含有 `adb_deeplink` 鍵值的推送裝載中。

1. 在 AppDelegate 中，您可以取回深層連結 URL，然後於下列位置中自行處理:

   * 在 `application:didFinishLaunchingWithOptions`:

      如果推送點進發生時，應用程式並未運作，您可以從 `launchOptions` 取得推送裝載，深層連結 URL 即位於 `adb_deeplink` 鍵值旁的裝載字典中。

   * 遠端通知的委派方法

      在`didReceiveRemoteNotification:` 應用程式或 `didReceiveRemoteNotification:fetchCompletionHandler:` 應用程式中，您可以使用 `adb_deeplink` 索引鍵存取 `userInfo` 字典以取得 URL。

   * `UNUserNotificationCenter` 的委派方法

      在 `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` 方法中，您可以透過 `adb_deeplink` 索引鍵中的 `userInfo` 字典取得推送裝載。

例如:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

