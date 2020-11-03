---
description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。
seo-description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。
seo-title: 追蹤深層連結
solution: Experience Cloud,Analytics
title: 追蹤深層連結
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# 追蹤深層連結{#tracking-deep-links}

您可以使用此資訊，在行動應用程式中利用 Adobe Mobile iOS SDK 追蹤深層連結和延期的深層連結。

如需有關行銷人員如何在他們的應用程式中使用深層連結的詳細資訊，請參閱 Mobile Services 文件中的[贏取](/help/ios/acquisition-main/acquisition.md)一節。

## 追蹤深層連結

1. 新增 SDK 至您的專案，並實作生命週期量度。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔案至您的專案*。
1. 註冊應用程式以處理應用程式間通訊或支援通用連結。

   如需詳細資訊，請參閱[應用程式間通訊](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10)或[支援通用連結](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

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

如果連結中包含附有 `a.deeplink.id` 標籤的索引鍵以及使用者自行產生的非空對應數值，則 Adobe Mobile SDK 可剖析附加至任何深層或通用連結之資料的索引鍵/值組。若連結包含 `a.deeplink.id` 鍵值和值，所有附加至連結之資料的鍵值和值組都會經過剖析、附加至生命週期點擊，然後傳送至 Adobe Analytics。

此外，您也可以選擇將下列其中一或多組保留的索引鍵 (搭配使用者產生的值) 附加至深層或通用連結:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

這些鍵值皆為預先對應的變數，用於在 Adobe Analytics 中報告。如需對應與處理規則的詳細資訊，請參閱[處理規則和內容資料](/help/ios/getting-started/proc-rules.md)。

### 追蹤延期的深層連結

1. 註冊 Adobe 資料回撥。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. 在 `AdobeDataCallback` 內處理 `ADBMobileDataEventDeepLink`。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## 深層連結公開資訊 {#section_44600E9AA68D4A53AA0C14BD86CC5284}

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

