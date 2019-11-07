---
description: '此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
seo-description: '此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
seo-title: 核心實施與生命週期
solution: Marketing Cloud,Analytics
title: 核心實施與生命週期
topic: 開發人員和實施
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: ht
source-git-commit: 4db9781e6e1e75a04d9715a41c5a32c10ede1bf4

---


# 核心實施與生命週期 {#core-implementation-and-lifecycle}

此資訊可協助您實施 iOS 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。

## 下載 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>若要下載 SDK，您&#x200B;**必須**&#x200B;使用 iOS 6 或更新版本。

**先決條件**

下載 SDK 之前，請完成[核心實施與生命週期](/help/ios/getting-started/requirements.md)的&#x200B;*建立報表套裝*&#x200B;中的步驟，以設定開發報表套裝和下載預先填入版本的設定檔案。

若要下載 SDK:

1. 下載並解壓縮 `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` 檔案，然後確認您有下列軟體元件:

   * `ADBMobile.h`，此元件為用於 iOS AppMeasurement 的 Objective-C 標頭檔案。
   * `ADBMobileConfig.json`，此元件為根據您應用程式自訂的 SDK 設定檔案。
   * `AdobeMobileLibrary.a`，此元件為已啟用位元碼的大型二進位檔，其中包含 iOS 裝置 (armv7、armv7s、arm64) 和模擬器 (i386 和 x86_64) 適用的資料庫組建。

      當預期目標為 iOS 應用程式時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_Extension.a`，此元件為已啟用位元碼的大型二進位檔，其中包含 iOS 裝置 (armv7、armv7s、arm64) 和模擬器 (i386 和 x86_64) 適用的資料庫組建。

      當預期目標為 iOS 延伸功能時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_Watch.a`，此元件為已啟用位元碼的大型二進位檔，其中包含 Apple Watch 裝置 (armv7k) 和模擬器 (i386 和 x86_64) 適用的資料庫組建。

      當預期目標為 Apple Watch (watchOS 2) 延伸功能應用程式時，應連結此大型二進位檔。

   * `AdobeMobileLibrary_TV.a`，此元件為已啟用位元碼的大型二進位檔，其中包含新 Apple TV 裝置 (arm64) 和模擬器 (x86_64) 適用的資料庫組建。

      當預期目標為 Apple TV (tvOS) 應用程式時，應該連結此大型二進位檔。

>[!IMPORTANT]
>
>如果您在 Adobe Mobile Services 使用者介面以外的地方下載 SDK，則必須手動設定 `ADBMobileConfig.json` 檔案。如果您是初次使用 Analytics 和 Mobile SDK，請參閱[開始之前](/help/ios/getting-started/requirements.md)，以設定開發報表套裝和下載預先填入版本的設定檔案。

## 新增 SDK 和設定檔案至您的專案 {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動 Xcode IDE 並開啟您的應用程式。
1. 在「專案導覽器」中，拖曳 `AdobeMobileLibrary` 資料夾，並將其放置在您的專案下。
1. 請確認下列項目:

   * 已選取&#x200B;**[!UICONTROL 「需要時複製項目」]核取方塊。**
   * **[!UICONTROL 已選取「建立群組」]**。
   * 未選取&#x200B;**[!UICONTROL 「新增至目標」]區段中的任何核取方塊。**
   ![](assets/step_3.png)

1. 按一下&#x200B;**[!UICONTROL 完成]**。
1. 在&#x200B;**[!UICONTROL 專案導覽器]**&#x200B;中，選取 **[!UICONTROL`ADBMobileConfig.json`]**。
1. 在&#x200B;**[!UICONTROL 檔案檢查工具]**&#x200B;中，將 JSON 檔案新增至將使用 Adobe SDK 之專案中的任何目標。

   ![](assets/step_4.png)

1. 在&#x200B;**[!UICONTROL 專案導覽器]**&#x200B;中，完成下列步驟:

   1. 按一下您的應用程式。
   1. 在&#x200B;**[!UICONTROL 「一般」]**&#x200B;標籤上，選取您的目標並連結&#x200B;**[!UICONTROL 「連結架構」]和**「資料庫」]區段中必要的架構和資料庫。**[!UICONTROL **
   * **iOS 應用程式目標**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
      * `CoreLocation.framework` (選擇性，但需要地理位置追蹤功能）
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
   > 在相同的目標中連結多個 `AdobeMobileLibrary*.a` 檔案，將會導致非預期行為或建置失敗。

1. 確認可建置應用程式且未發生錯誤。

## 實施生命週期量度 {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>不論是否呼叫 `collectlifecycledata`，iOS 都會傳送生命週期資訊；`collectlifecycledata` 只是在應用程式啟動序列早期啟動生命週期的方法。

啟用生命週期後，每當您的應用程式啟動時，就會傳送一次點擊以測量啟動數、升級數、工作階段數、參與使用者數，以及其他[生命週期量度](/help/ios/metrics.md)。

在 `application:didFinishLaunchingWithOptions` 中新增 `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` 呼叫:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### 納入其他資料與生命週期呼叫

若要納入其他資料與生命週期量度呼叫，請使用 `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>任何透過 `collectLifecycleDataWithAdditionalData:` 傳遞至 SDK 的資料都會由 SDK 保存在 `NSUserDefaults` 中。SDK 會拆解不屬於 `NSDictionary` 或 `NSString` 類型之 `NSNumber` 參數的值。

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
