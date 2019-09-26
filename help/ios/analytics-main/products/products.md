---
description: 您無法透過處理規則設定產品變數。在 iOS 4.x SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定產品。
seo-description: 您無法透過處理規則設定產品變數。在 iOS 4.x SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定產品。
seo-title: 產品變數
solution: Marketing Cloud,Analytics
title: 產品變數
topic: 開發人員和實施
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

您無法透過處理規則設定產品變數。在 iOS 4.x SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定產品。

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

例如:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* 是直接在影像要求上設定的，而其他變數則設為內容資料. 所有內容資料變數都必須透過處理規則對應:

![](assets/map-products.png)

您無須使用處理規則對應&#x200B;*`products`*&#x200B;變數，因為變數是由 SDK 直接在影像要求上設定的。
