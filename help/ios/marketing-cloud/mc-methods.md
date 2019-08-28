---
description: 以下是iOS程式庫提供的Adobe Experience Platform Identity Service方法。
seo-description: 以下是iOS程式庫提供的Adobe Experience Platform Identity Service方法。
seo-title: Adobe Experience Platform Identity Service方法
solution: Marketing Cloud、Analytics
title: Adobe Experience Platform Identity Service方法
topic: 開發人員和實施
uuid: cdd307bc-8b7d-47a8-b77 e-00902b9 e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Adobe Experience Platform Identity Service方法 {#experience-cloud-id-service-methods}

以下是iOS程式庫提供的Adobe Experience Platform Identity Service方法。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Experience Cloud 訪客 ID 服務。

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. 如需詳細資訊，請參閱[啟用 Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。

* **`+`(nullable NSRL`*`) visitorAppendToURL：(nullable NSRL`*`) url；**

   將 Adobe 訪客資料附加至 URL 字串以與 Adobe JavaScript 資料庫搭配使用。若要使用此方法，您必須擁有Mobile SDK4.12版或更新版本。如需詳細資訊，請參閱[附加訪客 ID 協助程式功能](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)。

   >[!IMPORTANT]
   >
   >此方法可能會造成封鎖網路呼叫。請勿在具時效性的執行緒上呼叫此方法。

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`已附加訪客資訊的字串。

   * 以下是此方法的範例程式碼:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 以下是此方法的語法:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   透過 Experience Cloud ID，您可以設定與每個訪客相關聯的額外客戶 ID。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   將提供的識別碼同步至 ID 服務。在 `authState` 中以下列其中一個值傳遞:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 以下是此方法的語法:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   將提供的識別碼類型和值同步至 ID 服務。Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 以下是此方法的語法:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 以下是此方法的語法:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   擷取一連串唯讀 `ADBVisitorID` 物件。

   * 以下是此方法的語法:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **VisitOrgetURLVariablesAsync**

   此方法在4.16.0版中引入，傳回包含訪客ID服務URL變數的適當字串。如需如何使用此方法的詳細資訊，請參閱 [Adobe Experience Platform Identity Service方法](/help/ios/reference/hybrid-app.md)。

   * 以下是此方法的語法:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * 以下是此方法的範例程式碼:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID interface {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**公用方法:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

