---
description: 計時動作可讓您測量停留在應用程式內的時間，以及動作從開始到結束的總時間。SDK 會計算每個工作階段的時間量，以及跨工作階段的動作完成總時間。您可以利用計時動作來定義區段，並用來比較購買所需時間、通過層級、結帳流程等動作。
seo-description: 計時動作可讓您測量停留在應用程式內的時間，以及動作從開始到結束的總時間。SDK 會計算每個工作階段的時間量，以及跨工作階段的動作完成總時間。您可以利用計時動作來定義區段，並用來比較購買所需時間、通過層級、結帳流程等動作。
seo-title: 計時動作
solution: Marketing Cloud、Analytics
title: 計時動作
topic: 開發人員和實施
uuid: dbcbac5a-6345-49f6-b050-0db05292 f005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

計時動作可讓您測量停留在應用程式內的時間，以及動作從開始到結束的總時間。SDK 會計算每個工作階段的時間量，以及跨工作階段的動作完成總時間。您可以利用計時動作來定義區段，並用來比較購買所需時間、通過層級、結帳流程等動作。

系統會報告下列計時動作的量度:

* 從開始到結束期間停留在應用程式內的總秒數 (跨工作階段)
* 從開始到結束的總秒數 (時鐘時間)

選擇性回撥可讓您在計時動作完成後採取額外動作:

* 執行程式碼並新增任一邏輯 – 根據持續時間結果選擇性新增自訂邏輯。
* 新增內容資料後再傳遞持續時間。
* 取消尚未傳送的點擊和持續時間。

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期中的新增SDK和設定檔案至您的專案*[](/help/ios/getting-started/dev-qs.md)。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 呼叫 `trackTimedActionStart`，並提供計時動作名稱與選擇性內容資料。

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (選擇性) 您隨時都可以利用計時動作名稱呼叫 `trackTimedActionUpdate`，以新增其他內容資料。

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. 事件完成後，呼叫 `trackTimedActionEnd`，然後傳遞計時動作名稱與 `TimedActionBlock` (回撥)，即可查詢所有資料並計算持續時間。

   計時事件量度會儲存在行動解決方案變數中，以便自動報告。

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了計時動作名稱之外，您還可以隨著動作開始與動作更新呼叫傳送其他內容資料:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

上下文資料值必須映射至自訂變數：

![](assets/map-variable-context-ltv.png)

## 範例 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

