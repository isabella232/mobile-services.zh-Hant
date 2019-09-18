---
description: '此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
seo-description: '此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
seo-title: 核心實施與生命週期
solution: Marketing Cloud,Analytics
title: 核心實施與生命週期
topic: 開發人員和實施
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: tm+mt
source-git-commit: be980e0e639d5b0df3f1b6a6f91f3ad0a5efe8d7

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。

## 下載 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**先決條件**

在您下載SDK之前，請先完成 *Core實作和生命週期中建立報表套裝的步驟*[](/help/ios/getting-started/requirements.md) ，以設定開發報表套裝並下載預先填入版本的組態檔。

若要下載 SDK:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`，此元件為用於 iOS AppMeasurement 的 Objective-C 標頭檔案。
   * `ADBMobileConfig.json`，此元件為根據您應用程式自訂的 SDK 設定檔案。
   * `AdobeMobileLibrary.a`、啟用位元程式碼的二進位檔，其中包含iOS裝置(armv7、armv7s、arm64)和模擬器(i386、x86_64)的程式庫組建。

      當預期目標為 iOS 應用程式時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_Extension.a`，此元件為已啟用位元碼的大型二進位檔，其中包含 iOS 裝置 (armv7、armv7s、arm64) 和模擬器 (i386 和 x86_64) 適用的資料庫組建。

      當預期目標為 iOS 延伸功能時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_Watch.a`，此元件為已啟用位元碼的大型二進位檔，其中包含 Apple Watch 裝置 (armv7k) 和模擬器 (i386 和 x86_64) 適用的資料庫組建。

      當預期目標為 Apple Watch (watchOS 2) 延伸功能應用程式時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_TV.a`，此元件為已啟用位元碼的大型二進位檔，其中包含新 Apple TV 裝置 (arm64) 和模擬器 (x86_64) 適用的資料庫組建。

      當預期目標為 Apple TV (tvOS) 應用程式時，應該連結此大型二進位檔。

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動 Xcode IDE 並開啟您的應用程式。
1. 在「專案導覽器」中，拖曳 `AdobeMobileLibrary` 資料夾，並將其放置在您的專案下。
1. 請確認下列項目:

   * 已選取&#x200B;**[!UICONTROL 「需要時複製項目」]核取方塊。**
   * **[!UICONTROL 已選取「建立群組」]**。
   * 未選取&#x200B;**[!UICONTROL 「新增至目標」]區段中的任何核取方塊。**
   ![](assets/step_3.png)

1. Click **[!UICONTROL Finish]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. 按一下您的應用程式。
   1. 在&#x200B;**[!UICONTROL 「一般」]**&#x200B;標籤上，選取您的目標並連結&#x200B;**[!UICONTROL 「連結架構」]和**「資料庫」]區段中必要的架構和資料庫。**[!UICONTROL **
   * **iOS 應用程式目標**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **iOS 延伸功能目標**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch (watchOS 2) 目標**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV (tvOS) 目標**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. 確認可建置應用程式且未發生錯誤。

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

新增 `collectLifecycleData`/呼 `collectLifecycleDataWithAdditionalData` 叫 `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### 將其他資料加入生命週期呼叫

若要納入其他資料與生命週期量度呼叫，請使用 `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. SDK 會拆解不屬於 `NSDictionary` 或 `NSString` 類型之 `NSNumber` 參數的值。

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

與 `collectLifecycleDataWithAdditionalData` 一併傳送的其他內容資料值，必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-lifecycle.png)

系統會自動收集其他生命週期量度。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

## 後續步驟 {#section_A24DC703359D4B5C8F493D6421306FD3}

完成下列作業:

* [追蹤應用程式狀態](/help/ios/analytics-main/states.md)
* [追蹤應用程式動作](/help/ios/analytics-main/actions.md)
