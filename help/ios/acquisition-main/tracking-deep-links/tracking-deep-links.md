---
description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。
seo-description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。
seo-title: 追蹤深層連結
solution: Marketing Cloud,Analytics
title: 追蹤深層連結
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links{#tracking-deep-links}

您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。

如需有關行銷人員如何在他們的應用程式中使用深層連結的詳細資訊，請參閱 Mobile Services 文件中的[贏取](/help/ios/acquisition-main/acquisition.md)一節。

## 追蹤深層連結

1. 新增 SDK 至您的專案，並實作生命週期量度。

   如需詳細資訊，請 *參閱核心實作和生命週期中的「將SDK和設定檔案新*[增至專案」](/help/ios/getting-started/dev-qs.md)。
1. 註冊應用程式以處理應用程式間通訊或支援通用連結。

   For more information, see Inter-App Communications or Support Universal Links[](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10)[](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. 在 openURL 中追蹤深層連結。

   以下為追蹤深層連結的範例:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

The Adobe Mobile SDK can parse key and value pairs of data appended to any deep or Universal Link, provided that the link contains a key with a `a.deeplink.id` label and a corresponding non-null and user generated value. 若連結包含 `a.deeplink.id` 鍵值和值，所有附加至連結之資料的鍵值和值組都會經過剖析、附加至生命週期點擊，然後傳送至 Adobe Analytics。

您也可以選擇將下列一或多個保留金鑰（含使用者產生的值）附加至深層或通用連結：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

這些鍵值皆為預先對應的變數，用於在 Adobe Analytics 中報告。如需對應與處理規則的詳細資訊，請參閱[處理規則和內容資料](/help/ios/getting-started/proc-rules.md)。

### 追蹤延遲的深層連結

1. 註冊 Adobe 資料回撥。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Handle `ADBMobileDataEventDeepLink` within `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Deep link public information {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### 方法

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### 常數

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

