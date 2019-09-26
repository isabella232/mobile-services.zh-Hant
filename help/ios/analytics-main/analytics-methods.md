---
description: 以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。
seo-description: 以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。
seo-title: 分析方法
solution: Marketing Cloud,Analytics
title: 分析方法
topic: 開發人員和實施
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

以下為 iOS 資料庫所提供的 Adobe Analytics 方法清單。

SDK目前支援多個Adobe Experience cloud解決方案，包括Analytics、Target、Audience manager和Adobe Experience Platform Identity Service。 Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。如果 `state` 空白，在報表中會顯示為 *app name app version (build)*。如果在報表中看到此值，請務必在每個 `state` 呼叫中設定 `trackState`。

   >[!TIP]
   >
   >這是唯一會增加頁面檢視次數的追蹤呼叫。

   * 以下是此方法的語法:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   追蹤應用程式中的動作。Actions that you want to measure, such as , , , and other metrics, occur in your app.`logons``banner taps``feed subscriptions`

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   擷取分析追蹤識別碼。

   * 以下是此方法的語法:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   追蹤於背景發生的動作，可抑制生命週期事件於特定狀況下觸發。

   >[!TIP]
   >
   >This method should only be called in code that runs while your app is in the background.

   * 以下是此方法的語法:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   傳送目前的 x 和 y 座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供為參數的位置是否在您的任何 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   追蹤使用者何時進入信標鄰近地區。

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 以下是此方法的語法:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Adds `amount` to the user's lifetime value.

   * 以下是此方法的語法:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   以名稱 `action` 啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   傳遞 `data` 以更新與指定 `action` 關聯的內容資料。傳遞的 `data` 會附加至該動作的現有資料，如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   結束計時動作。If you provide `block`, you will have access to the final time values and be able to manipulate `data` prior to sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

   * 以下是此方法的語法:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * 以下是此方法的範例程式碼:

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

   * 以下是此方法的語法:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Requires SDK 4.1. Regardless of how many hits are currently queued, forces the library to send all hits in the offline queue.

   * 以下是此方法的語法:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 以下是此方法的語法:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   清除離線佇列中的所有點擊。

   >[!CAUTION]
   >
   >手動清除佇列時請小心。 此程序無法回復。

   * 以下是此方法的語法:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   追蹤推送訊息點進。

   >[!IMPORTANT]
   >
   >此方法不會增加頁面檢視。

   * 以下是此方法的語法:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * 以下是此方法的範例程式碼:

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
