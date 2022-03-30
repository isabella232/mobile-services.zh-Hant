---
description: 以下為 iOS 資料庫所提供的方法清單。
solution: Experience Cloud Services,Analytics
title: 設定方法
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 100%

---

# 設定方法 {#configuration-methods}

以下為 iOS 資料庫所提供的方法清單。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。

* **setAppExtensionType**

   設定 Adobe Mobile SDK 以確認目前執行的擴充功能類型。

   設定為下列任一值：
   * `ADBMobileAppExtensionTypeRegular` - 擴充功能與容納應用程式搭配。
   * `ADBMobileAppExtensionTypeStandAlone` - 擴充功能並未與容納應用程式搭配。

   >[!TIP]
   >
   >此方法&#x200B;**「僅」**&#x200B;在您的應用程式具有擴充功能，或為獨立擴充功能時，才可使用。如需詳細資訊，請參閱下方的 *ADBMobileAppExtensionType*。

   * 此方法的語法如下：

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **版本**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 此方法的語法如下：

      ```objective-c
      +(NSString*) version;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法：

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 此方法的語法如下：

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。

   設定為下列其中一值：

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   傳回目前使用者的期限值。預設值為 `0`。

   * 此方法的語法如下：

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   傳回自動產生的訪客識別碼。這是 Adobe 伺服器產生的應用程式專屬訪客 ID，此 ID 不會重複。如果產生 ID 時無法連線 Adobe 伺服器，則會使用 Apple 的 CFUUID 來產生。值會在初次啟動時產生並儲存，此後便一律使用此值。此 ID 會在應用程式升級時保留、在標準應用程式備份程序期間儲存及還原，並在解除安裝時移除。

   >[!TIP]
   >
   >如果您的應用程式從 Experience Cloud 3.x 升級至 4.x SDK，應用程式會擷取先前的訪客 ID (自訂或自動產生) 並將其儲存為自訂使用者識別碼。如需詳細資訊，請參閱下方的 `userIdentifier` 列。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `nil`，且會使用追蹤識別碼。

   * 此方法的語法如下：

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   若已設定自訂識別碼，將會傳回使用者識別碼。如果未設定自訂識別碼，則會傳回 `nil`。預設值為 `nil`。

   >[!TIP]
   >
   >如果您的應用程式從 Experience Cloud 3.x 升級至 4.x SDK，應用程式會擷取先前的訪客 ID (自訂或自動產生) 並將其儲存為自訂使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。

   若為全新安裝的 4.x SDK，則使用者識別碼為 `nil`，直到設定完成為止。

   * 此方法的語法如下：

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 此方法的語法如下：

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `NO`。

   * 此方法的語法如下：

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   將偵錯記錄偏好設定設為 `debug`。

   * 此方法的語法如下：

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法旨在用於在背景中註冊接收通知的應用程式，且只有當應用程式於背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 此方法的語法如下：

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   >[!TIP]
   >
   >叫用此方法的慣用位置位於 `application:didFinishLaunchingWithOptions:`。

   * 此方法的語法如下：

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   可讓您在收集生命週期量度時傳遞其他資料。

   您必須從應用程式的進入點呼叫此方法。若適用，您的 AppDelegate 類別中可能會包含下列兩種方法其中之一或兩者皆包含 `application:didFinishLaunchingWithOptions:` 和/或 `applicationWillEnterForeground:`。

   >[!IMPORTANT]
   >
   >任何透過 `collectLifecycleDataWithAdditionalData:` 傳遞至 SDK 的資料將會由 SDK 保存在 `NSUserDefaults`。SDK 會拆解任何不屬於 `NSDictionary` 或 `NSString` 類型之 `NSNumber` 參數的值。若要使用 `collectLifecycleDataWithAdditionalData:`，您必須有 **SDK 4.4 版**&#x200B;或更新版本。

   * 此方法的語法如下：

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   此 API 可暫停生命週期資料的收集作業。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   >[!IMPORTANT]
   >
   >在 `applicationDidEnterBackground` 委派方法中，您必須先呼叫 `pauseCollectingLifecycleData` 方法。
   >
   >提供 API 是為了緩解搭載 iOS 13 之 iPhone7/7s 或舊版裝置上作業長度量度異常的問題。這是因為 iOS 13 發生了某些未知變更，使得應用程式在背景中運作時，iOS 並未預留充足的時間讓背景工作完成。

   * 此方法的語法如下：

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   可讓您在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔。應用程式會使用另一個設定，直到關閉為止。

   >[!IMPORTANT]
   >
   >若要使用 `overrideConfigPath`，您必須有 SDK 4.2 版或更新版本。

   * 此方法的語法如下：

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   設定用於推送通知的裝置代號。

   >[!IMPORTANT]
   >
   >此方法只應在 `application:didRegisterForRemoteNotificationsWithDeviceToken:` 方法中使用。

   * 此方法的語法如下：

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   在 SDK 中設定 IDFA。如果已於 SDK 設定 IDFA，系統會在生命週期中傳送 IDFA。您也可在「訊號」(回傳) 中存取 IDFA。

   >[!TIP]
   >
   >「只有」****&#x200B;在您使用廣告服務時，才能從 Apple API 擷取 IDFA。若您擷取了 IDFA 卻不當使用，您的應用程式可能會遭到拒絕。
   >
   >如果您的應用程式需要 IDFA，請查看 [Apple 文件](https://developer.apple.com/documentation/adsupport)，查詢使用者的廣告追蹤偏好設定並擷取 IDFA 值。
   >
   >您必須在 iOS 14 以上版本的系統中實作新的[應用程式追蹤透明度框架](https://developer.apple.com/documentation/apptrackingtransparency)，才能成功擷取 IDFA 值。
   * 此方法的語法如下：

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType 列舉 {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```
