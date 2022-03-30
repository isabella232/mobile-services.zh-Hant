---
description: 無法使用處理規則設定產品變數。在 iOS 4.x SDK 中，您必須在內容資料參數中使用特殊語法，才能直接在伺服器呼叫上設定產品。
solution: Experience Cloud Services,Analytics
title: 產品變數
topic-fix: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
exl-id: c945add4-5358-44f6-b445-554b0df056c1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 100%

---

# Products 變數 {#products-variable}

無法使用處理規則設定產品變數。在 iOS 4.x SDK 中，您必須在內容資料參數中使用特殊語法，才能直接在伺服器呼叫上設定產品。

若要設定 *`products`* 變數，請將內容資料索引鍵設為 `"&&products"`，並使用針對 *`products`* 變數定義的語法來設定值:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

例如：

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

*`products`* 是直接在影像要求上設定的，而其他變數則設為內容資料。必須使用處理規則對應所有內容資料變數：

![](assets/map-products.png)

您不必使用處理規則對應 *`products`* 變數，因為變數是由 SDK 直接在影像要求上設定。
