---
description: 使用 iOS SDK 來實施對第三方延期的深層連結的追蹤。
title: 追蹤協力廠商延期的深層連結
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
exl-id: c6d2ec6e-cd2a-4670-96e9-cb5e09f7cc10
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 90%

---

# 追蹤第三方延期的深層連結 {#tracking-third-party-deferred-deep-links}

使用 iOS SDK 來實施對第三方延期的深層連結的追蹤。

## 傳統 Adobe Mobile SDK 深層連結 {#section_D114FA1EB9664EAA82E036A990694B26}

Adobe Mobile SDK 目前支援的深層連結可讓應用程式開發人員呼叫 `trackAdobeDeepLink` API，並傳遞深層連結 URL (設定期間在 Adobe Mobile Services 中產生的指紋識別器 URL)。SDK 會偵測指紋識別器，以取得贏取資料並將其附加至安裝/啟動分析呼叫內容資料，作為生命週期的一部分。此外，SDK 也會從深層連結 URL 參數中附加深層連結資料。如需深層連結的詳細資訊，請參閱[追縱深層連結](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md)。

## Facebook 深層連結 {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

廣告創作者可以在 Facebook 中刊登廣告作為深層連結。使用者按一下 Facebook 中的廣告時，會直接在應用程式中前往感興趣的資訊。深層連結&#x200B;**並非**&#x200B;指紋識別器 URL。然而，在廣告設定期間，您可以選擇提供協力廠商深層連結 URL。使用Experience CloudMobile SDK和服務的應用程式開發人員應在此欄位中輸入Mobile Services設定的指紋識別器URL。 如果所有項目皆已正確設定，則 Facebook SDK 會在應用程式安裝或啟動後，將此 URL 傳遞至應用程式。

## 設定SDK {#section_834CD3109175432B8173ECB6EA7DE315}

1. 設定 Facebook SDK.

   如需詳細資訊，請參閱以下頁面:

   * [Facebook iOS SDK 新手指南](https://developers.facebook.com/docs/ios/getting-started)
   * [深層連結設定](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. 若要設定 SDK，請呼叫 `trackAdobeDeepLink`，並將 URL 傳遞至 SDK:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >請確認深層連結 URL 擁有名稱為 `a.deeplink.id` 的索引鍵。如果 URL 缺少 `a.deeplink.id` 參數，則不會在內容資料中附加任何 URL 參數。

如果應用程式依上述方式設定，則目前的 AMSDK 版本將會正常運作，且會將深層連結資料正確附加至安裝/啟動分析呼叫中。

## 啟用範例應用程式中的功能 {#section_64C15E269E89424B8E3D029F88094620}

1. 註冊 URL 結構。

   請確定您已註冊 URL 結構，這與深層連結 URL 相同。

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. 連結 Facebook SDK。

   ![Facebook 資產](assets/link-fb-sdk.jpg)

1. 編輯 `AppDelegate`。

   1. 匯入標題。

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. 新增延期深層連結的處理常式。

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. 呼叫 `trackAdobeDeepLink` API 並將深層連結 URL 傳遞至 SDK。

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```
