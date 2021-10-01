---
description: 從 WatchOS 2 開始，您的 WatchKit 延伸功能將會在 Apple Watch 裝置上執行。在此環境中執行的應用程式皆須使用 WatchConnectivity 架構，以與其容納 iOS 應用程式共用資料。
solution: Experience Cloud,Analytics
title: 使用 WatchOS 2 進行 Apple Watch 實施
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 100%

---

# 使用 WatchOS 2 進行 Apple Watch 實施{#apple-watch-implementation-with-watchos}

從 WatchOS 2 開始，您的 WatchKit 延伸功能可在 Apple Watch 上執行。在此環境中執行的應用程式皆須使用 `WatchConnectivity` 架構，以與其容納 iOS 應用程式共用資料。

>[!TIP]
>
>從 `AdobeMobileLibrary` 4.6.0 版開始，即支援 `WatchConnectivity`。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 快速入門 {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>確保您擁有至少具備以下目標的專案:
>
>* 容納應用程式
>* WatchKit 應用程式
>* WatchKit 延伸功能
>


如需有關開發 WatchKit 應用程式的詳細資訊，請參閱 [Watch 應用程式架構](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)。

## 設定容納應用程式 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

在您的 Xcode 專案中完成以下步驟:

1. 將 `AdobeMobileLibrary` 資料夾拖曳到專案中。
1. 確認 `ADBMobileConfig.json` 檔案為容納應用程式目標的成員。
1. 在容納應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

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
   #import "ADBMobile.h"
   ```

1. 呼叫 `ADBMobile` 資料庫之前，請在應用程式委派的 `application:didFinishLaunchingWithOptions:` 中，設定您的 `WCSession`。

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. 在您的應用程式委派中，實施 `session:didReceiveMessage:` 和 `session:didReceiveUserInfo:` 方法。

   系統會在 `ADBMobile` 資料庫中呼叫 `syncSettings:`，其會傳回布林值指示是否會由 `ADBMobile` 資料庫使用字典。如果其傳回 `No`，則訊息不會從 Adobe SDK 啟動。

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

## 設定 WatchKit 延伸功能 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. 確認 `ADBMobileConfig.json` 檔案為 WatchKit 延伸功能目標的成員。
1. 在 WatchKit 延伸功能目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. 在實施 `WKExtensionDelegate` 通訊協定的類別中，匯入 `WatchConnectivity` 並新增 `WCSessionDelegate` 通訊協定。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. 在延伸功能委派類別的實施檔案中，匯入 `AdobeMobileLibrary`。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 在延伸功能委派的 `applicationDidFinishLaunching` 中，設定您的 `WCSession`，然後再對 `ADBMobile` 資料庫進行任何呼叫。

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

1. 在您的延伸功能委派中，實施 `session:didReceiveMessage:` 和 `session:didReceiveUserInfo:` 方法。

   系統會在 `ADBMobile` 資料庫中呼叫 `syncSettings:`，其會傳回布林值指示是否會由 `ADBMobile` 資料庫使用字典。如果其傳回 `NO`，則訊息不會從 Adobe SDK 啟動。

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

* 若為 WatchKit 應用程式，`a.RunMode` 則會設為 `Extension`。
* 由於 WatchKit 應用程式會在 Watch 上執行，因此應用程式會在 `a.AppID` 中正確回報其名稱。
* 在 WatchOS2 應用程式中不會觸發任何生命週期呼叫。
