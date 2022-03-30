---
description: 以下為 iOS 資料庫所提供的 Adobe Experience Platform Identity Service 方法。
solution: Experience Cloud Services,Analytics
title: Adobe Experience Platform Identity Service 方法
topic-fix: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
exl-id: 82a246fc-f679-4fa5-b9c0-dc909a7e7d93
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 96%

---

# Adobe Experience Platform Identity Service 方法 {#experience-cloud-id-service-methods}

以下為 iOS 資料庫所提供的 Adobe Experience Platform Identity Service 方法。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Experience Cloud 訪客 ID 服務。

各方法會根據解決方案加上前置詞，因此 Experience Cloud ID 方法會加上前置詞 `visitor`。如需詳細資訊，請參閱[啟用 Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。

* **`+`(nullable NSURL `*`)visitorAppendToURL:(nullable NSURL `*`)url;**

   將 Adobe 訪客資料附加至 URL 字串以與 Adobe JavaScript 資料庫搭配使用。若要使用此方法，您必須有 Mobile SDK 4.12 版或更新版本。有關詳細資訊，請參見 [將訪問者ID附加到](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/appendvisitorid.html) 在Adobe Experience Cloud身份服務文檔中。

   >[!IMPORTANT]
   >
   >此方法會造成封鎖網路呼叫。請勿在具時效性的執行緒上呼叫此方法。

   * 輸入：`URL<NSURL>`
要附加訪客資訊的必要 URL 字串。
   * `URL<NSURL>`已附加訪客資訊的字串。

   * 此方法的範例程式碼如下：

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 此方法的語法如下：

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >此方法會造成封鎖網路呼叫，且&#x200B;**不**&#x200B;應從使用者介面執行緒呼叫此方法。

* **visitorSyncIdentifiers：**

   透過 Experience Cloud ID，您可以設定與每個訪客相關聯的額外客戶 ID。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   將提供的識別碼同步至 ID 服務。在 `authState` 中以下列任一值傳遞：

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 此方法的語法如下：

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:驗證狀態：**

   將提供的識別碼類型和值同步至 ID 服務。在 `authState` 中以下列任一值傳遞：

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 此方法的語法如下：

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 此方法的語法如下：

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   擷取一連串唯讀 `ADBVisitorID` 物件。

   * 此方法的語法如下：

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   4.16.0 版導入了此方法，可傳回包含訪客 ID 服務 URL 變數的適當形式字串。如需如何使用此方法的詳細資訊，請參閱 [Adobe Experience Platform Identity Service 方法](/help/ios/reference/hybrid-app.md)。

   * 此方法的語法如下：

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * 此方法的程式碼範例如下：

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID interface {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**公用方法：**

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
