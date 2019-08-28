---
description: 以下為 iOS 資料庫所提供的方法清單。
seo-description: 以下為 iOS 資料庫所提供的方法清單。
seo-title: 設定方法
solution: Marketing Cloud、Analytics
title: 設定方法
topic: 開發人員和實施
uuid: 623c7b07-fbb3-4d39-a5 c4-e64 fec4 ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

以下為 iOS 資料庫所提供的方法清單。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。

* **setAppExtensionType**

   進行 Adobe Mobile SDK 設定以確定目前執行的延伸功能類型。

   設定為下列其中一值:
   * `ADBMobileAppExtensionTypeRegular` - 擴充功能與容納應用程式整合。
   * `ADBMobileAppExtensionTypeStandAlone` - 擴充功能不會與容納應用程式搭售。
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

   * 以下是此方法的語法:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **版本**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 以下是此方法的語法:

      ```objective-c
      +(NSString*) version;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法:

   * `ADBMobilePrivacyStatusOptIn` - 點擊會立即傳送。
   * `ADBMobilePrivacyStatusOptOut` - 點擊會被捨棄。
   * `ADBMobilePrivacyStatusUnknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 以下是此方法的語法:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。

   設定為下列其中一值:

   * `ADBMobilePrivacyStatusOptIn` - 點擊會立即傳送。
   * `ADBMobilePrivacyStatusOptOut` - 點擊會被捨棄。
   * `ADBMobilePrivacyStatusUnknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   傳回目前使用者的期限值。預設值為 `0`。

   * 以下是此方法的語法:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   傳回自動產生的訪客識別碼。這是由 Adobe 伺服器所產生的應用程式專屬唯一訪客 ID。如果產生 ID 時無法連線至 Adobe 伺服器，則會改由透過 Apple 的 CFUUID 產生 ID。此值會在初次啟動時產生，然後儲存以供後續使用。此 ID 會在應用程式升級時保留、在標準應用程式備份程序期間儲存並還原，以及在解除安裝時移除。

   >[!TIP]
   >
   >如果您的應用程式升級從Experience Cloud3.x升級至4.x SDK，則會擷取先前的自訂或自動產生的訪客ID並儲存為自訂的使用者識別碼。如需詳細資訊，請參閱下方的 `userIdentifier` 列。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `nil`，且會使用追蹤識別碼。

   * 以下是此方法的語法:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   若已設定自訂識別碼，將會傳回使用者識別碼。如果未設定自訂識別碼，則會傳回 `nil`。預設值為 `nil`。

   >[!TIP]
   >
   >如果您的應用程式升級從Experience Cloud3.x到4.x SDK，會擷取先前的自訂或自動產生的訪客ID並儲存為自訂的使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。

   若為全新安裝的 4.x SDK，則使用者識別碼為 `nil`，直到設定完成為止。

   * 以下是此方法的語法:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的語法:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `NO`。

   * 以下是此方法的語法:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   將偵錯記錄偏好設定設為 `debug`。

   * 以下是此方法的語法:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法的目的是用於在背景中註冊接收通知的應用程式，且只有當應用程式在背景時，才應從執行的程式碼呼叫。

   * 以下是此方法的語法:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   >[!TIP]
   >
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

   * 以下是此方法的語法:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   可讓您在收集生命週期量度時傳遞其他資料。

   您必須從應用程式的登入點呼叫此方法。Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. SDK 會拆解任何不屬於 `NSDictionary` 或 `NSString` 類型之 `NSNumber` 參數的值。To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * 以下是此方法的語法:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   可讓您在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。應用程式會使用另一個設定，直到關閉為止。

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

   * 以下是此方法的語法:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   設定用於推送通知的裝置代號。

   >[!IMPORTANT]
   >
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

   * 以下是此方法的語法:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   在 SDK 中設定 IDFA。如果 SDK 中已設定 IDFA，則 IDFA 會在生命週期中傳送。您亦可在「訊號」(回傳) 中存取 IDFA。

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. 若您擷取了 IDFA 卻不當使用，您的應用程式可能會遭到拒絕。

   * 以下是此方法的語法:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
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

