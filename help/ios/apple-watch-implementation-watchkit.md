---
description: 從 WatchOS 2 開始，您的 WatchKit 延伸功能將會在 Apple Watch 裝置上執行。在此環境中執行的應用程式皆須使用 WatchConnectivity 架構，以與其容納 iOS 應用程式共用資料。
seo-description: 從 WatchOS 2 開始，您的 WatchKit 延伸功能將會在 Apple Watch 裝置上執行。在此環境中執行的應用程式皆須使用 WatchConnectivity 架構，以與其容納 iOS 應用程式共用資料。
seo-title: 使用 WatchOS 2 進行 Apple Watch 實施
solution: Marketing Cloud、Analytics
title: 使用 WatchOS 2 進行 Apple Watch 實施
topic: 開發人員和實施
uuid: 9498467e-db5 e-411e-a00 e-d19841 f485 de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

從WatchOS開始，您的WatchKit延伸模組可在Apple Watch上執行。Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>從 `AdobeMobileLibrary` v4.6.0開始 `WatchConnectivity` 支援。

## 入門 {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>確定您具有至少下列目標的專案：
>
>* 容納應用程式
>* WatchKit 應用程式
>* WatchKit 延伸功能
>



如需有關開發 WatchKit 應用程式的詳細資訊，請參閱 [Watch 應用程式架構](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)。

## 設定包含的應用程式 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

在您的 Xcode 專案中完成以下步驟:

1. 將 `AdobeMobileLibrary` 資料夾拖曳到專案中。
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. 在容納應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 在實施 `UIApplicationDelegate` 通訊協定的類別中，新增 `WCSessionDelegate` 通訊協定。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. 在應用程式委派類別的實施檔案中，匯入 `AdobeMobileLibrary`。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` 在 `ADBMobile` 程式庫中被呼叫，會傳回一個布林值，指出字典是否用於依 `ADBMobile` 程式庫進行消費。如果其傳回 `No`，則訊息不會從 Adobe SDK 啟動。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 設定WatchKit擴充功能 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. 在 WatchKit 延伸功能目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. 在延伸功能委派類別的實施檔案中，匯入 `AdobeMobileLibrary`。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. 在延伸功能委派的 `applicationDidFinishLaunching` 中，初始化 SDK 的 Watch 應用程式。

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` 在 `ADBMobile` 程式庫中被呼叫，會傳回一個布林值，指出字典是否用於依 `ADBMobile` 程式庫進行消費。如果其傳回 `NO`，則訊息不會從 Adobe SDK 啟動。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 其他資訊 {#section_7BCDB5CF0D424DCA97883753D1881233}

請記住以下資訊:

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* 由於 WatchKit 應用程式會在 Watch 上執行，因此應用程式會在 `a.AppID` 中正確回報其名稱。
* 在 WatchOS2 應用程式中不會觸發任何生命週期呼叫。

