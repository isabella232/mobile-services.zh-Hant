---
description: 以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。
seo-description: 以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。
seo-title: 'Analytics 方法 '
solution: Experience Cloud,Analytics
title: 'Analytics 方法 '
topic: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---


# Analytics 方法 {#analytics-methods}

以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。各方法會根據解決方案加上前置詞。Experience Cloud ID 方法會加上前置詞 `track`。

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

* **trackState:&#x200B;data：**

   狀態為應用程式中可用的檢視，例如 `home dashboard`、`app settings`、`cart` 等。這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。如果 `state` 空白，在報表中會顯示為 *app name app version (build)*。如果在報表中看到此值，請務必在每個 `state` 呼叫中設定 `trackState`。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data：**

   追蹤應用程式中的動作。您要測量的動作，例如`logons`、`banner taps`、`feed subscriptions`，以及在應用程式中發生的其他量度。

   >[!TIP]
   >
   >如果您的程式碼會在應用程式於背景時執行 (例如，背景資料擷取)，請改為使用 `trackActionFromBackground`。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   擷取分析追蹤識別碼。

   * 此方法的語法如下：

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data：**

   追蹤於背景發生的動作，可抑制生命週期事件於特定狀況下觸發。

   >[!TIP]
   >
   >只有當應用程式在背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 此方法的語法如下：

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data：**

   傳送目前的 x 和 y 座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供為參數的位置是否在您的任何 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data：**

   追蹤使用者何時進入信標鄰近地區。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 此方法的語法如下：

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data：**

   增加使用者期限值的 `amount`。

   * 此方法的語法如下：

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data：**

   以名稱 `action` 啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data：**

   傳遞 `data` 以更新與指定 `action` 關聯的內容資料。傳遞的 `data` 會附加至該動作的現有資料，如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic：**

   結束計時動作。如果您提供`block`，則可在傳送最後一次點擊前存取最後時間值並處理`data`。

   >[!TIP]
   >
   >如果您提供`block`，則必須傳回 `YES` 以傳送點擊。針對`block`傳遞 `nil` 會傳送最後一次點擊。

   * 此方法的語法如下：

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   傳回計時動作是否正在進行中。

   * 此方法的語法如下：

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   須使用 SDK 4.1 版。無論目前排入佇列的點擊數量多寡，都會強制資料庫傳送離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 此方法的語法如下：

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   清除離線佇列中的所有點擊。

   >[!CAUTION]
   >
   >手動清除佇列時請格外小心。此程序無法回復。

   * 此方法的語法如下：

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   追蹤推送訊息點進。

   >[!IMPORTANT]
   >
   >此方法無法遞增頁面檢視。

   * 此方法的語法如下：

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
