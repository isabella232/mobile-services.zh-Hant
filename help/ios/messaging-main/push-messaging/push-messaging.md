---
description: Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您藉由點進推播訊息，輕鬆報告已開啟您的應用程式的使用者。
solution: Experience Cloud Services,Analytics
title: 推送訊息
topic-fix: Developer and implementation
uuid: 2e2d8175-d7d0-4b6b-a14e-d419da1f9615
exl-id: 89796668-e0e7-45d2-8391-3c26a7ac8496
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---

# 推送訊息 {#push-messaging}

Adobe Mobile 和 Adobe Mobile SDK 可讓您傳送推送訊息給使用者。SDK 也可讓您藉由點進推播訊息，輕鬆報告已開啟您的應用程式的使用者。

>[!IMPORTANT]
>
>此主題中的資訊屬於可能的實施之建議。我們強烈建議您檢閱 Apple iOS 的文件，以判別最適合您應用程式的實施方式。您的實施應乃是按照您所使用的框架以及您的應用程式鎖定做為目標的 iOS 版本加以判別。

若要使用推送訊息，您&#x200B;**必須**&#x200B;有 SDK 4.6 版或更新版本。

>[!IMPORTANT]
>
>請勿在應用程式內手動設定 Experience Cloud ID。這樣會建立新的不重複使用者，且因其選擇加入狀態將不會收到推播訊息。例如，假設有某個選擇接收推播訊息的使用者登入您的應用程式。登入後，如果您在應用程式中手動設定 ID，則會建立新的不重複使用者，而未選擇接收推播訊息。這個新使用者不會收到您的推送訊息。

## 先決條件 {#section_06655ABE973743DC965897B229A2118D}

* 新增資料庫至您的專案與實施生命週期量度。

   如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。


* SDK 必須啟用 ID 服務。如需詳細資訊，請參閱[設定 SDK ID 服務選項](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)。

>[!IMPORTANT]
>
>不支援將您的應用程式移動到新的報表套裝。若您移轉到新報表套裝，推送設定可能會損毀，且訊息可能無法傳送。

## 啟用推送訊息 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

1. 確認 `ADBMobileConfig.json` 檔案包含推送訊息必需的設定。

   `"marketingCloud"` 物件必須有針對推送訊息設定的 `"org"` 屬性。

   ```objective-c
   "marketingCloud": { 
       "org": "3CE342C92046435B0A490D4C@AdobeOrg" 
   }
   ```

1. 將資料庫匯入 `AppDelegate`。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 若要判別您的應用程式需要詢問權限之設定，請檢閱[設定遠端通知支援](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/HandlingRemoteNotifications.html#//apple_ref/doc/uid/TP40008194-CH6-SW1)。

   以下是詢問使用「警示」、「徽章」、「音效」與「遠端通知」權限的可能實施的範例:

   ```objective-c
   // iOS 10 and newer 
   if (NSClassFromString(@"UNUserNotificationCenter")) { 
       UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];   
       [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
           completionHandler:^(BOOL granted, NSError * _Nullable error) { 
           if (granted) { NSLog(@"authorization given"); } 
           else { NSLog(@"authorization rejected"); } 
           if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
       }]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
       // make this class the delegate for user notification handling  
       center.delegate = self; 
   } 
   // iOS 8.0 to iOS 9.3.5 
   else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
   #pragma GCC diagnostic push 
   #pragma GCC diagnostic ignored "-Wdeprecated-declarations" 
       UIUserNotificationTypetypes = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
       UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
       [application registerUserNotificationSettings:settings]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
   } 
   // older than iOS 8.0  
   else { 
       [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound];  
   #pragma GCC diagnostic pop 
   }
   ```

1. 必須使用 ADBMobile 類別中的 `setPushIdentifier:` 方法將推送代號傳送至 SDK。

   ```objective-c
   - (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
       ... 
       [ADBMobile setPushIdentifier:deviceToken]; 
       ... 
   }
   ```

1. 若要判別適合您環境的正確實施，請前往 [UserNotifications](https://developer.apple.com/documentation/usernotifications)。

   此步驟可在使用者藉由點進推送訊息來開啟應用程式時，採用將 `userInfo` 字典傳遞至 SDK 的方式來協助您啟用推送報告功能。

   下列程式碼範例為可能的實施之範例:

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

1. 為了確保您預定的推送對象正確無誤，當使用者藉由叫用您的 `AppDelegate` 中 `applicationDidBecomeActive:` 方法的 `[ADBMobile setPushIdentifier: nil]` 以手動方式停用您的應用程式的推送訊息時，系統會通知 SDK。

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

## 範例 {#section_20BEA0D64F7C4D45A5EBEF21066E62AD}

以下範例為 `AppDelegate.m` 實施後看起來的樣子:

```objective-c
#import "AppDelegate.h" 
#import "ADBMobile.h" 
 
@implementation AppDelegate 
  
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    if (NSClassFromString(@"UNUserNotificationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
                              completionHandler:^(BOOL granted, NSError * _Nullable error) {  
            if (granted) { NSLog(@"authorization given"); } 
            else { NSLog(@"authorization rejected"); } 
            if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
        }]; 
        center.delegate = self; 
        [application registerForRemoteNotifications]; 
    } 
    else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
        UIUserNotificationType types = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
        UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
        [application registerUserNotificationSettings:settings];  
        [application registerForRemoteNotifications]; 
    } 
    else { 
        [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert| UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound]; 
#pragma GCC diagnostic pop 
    } 
 
    return YES; 
} 
 
- (void) applicationDidBecomeActive:(UIApplication *)application {  
    if (NSClassFromString(@"UNUserNotifcationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center getNotificationSettingsWithCompletionHandler:^(UNNotificationSettings * _Nonnull settings) { 
            if (settings.authorizationStatus != UNAuthorizationStatusAuthorized) {  
                [ADBMobile setPushIdentifier:nil]; 
            } 
        }]; 
    } 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
    else if ([application respondsToSelector:@selector(isRegisteredForRemoteNotifications)]) { 
        if (![application isRegisteredForRemoteNotifications]) {  
            [ADBMobile setPushIdentifier:nil]; 
        } 
    } 
    else if ([application enabledRemoteNotificationTypes] == UIRemoteNotificationTypeNone) { 
        [ADBMobile setPushIdentifier:nil]; 
    } 
#pragma GCC diagnostic pop 
} 
 
- (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
    [ADBMobile setPushIdentifier:deviceToken]; 
} 
 
- (void) application:(UIApplication *)application didFailToRegisterForRemoteNotificationsWithError:(NSError *)error { 
    [ADBMobile setPushIdentifier:nil]; 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    if (application.applicationState == UIApplicationStateInactive) {  
        [ADBMobile trackPushMessageClickThrough:userInfo];  
    } 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) {  
        if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
            [ADBMobile trackPushMessageClickThrough:userInfo]; 
        } 
    } 
 
    completionHandler(UIBackgroundFetchResultNoData); 
} 
 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
    } 
 
    completionHandler(); 
} 
 
@end
```
