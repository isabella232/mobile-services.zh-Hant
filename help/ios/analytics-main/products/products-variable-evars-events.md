---
description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-title: 產品變數及其包含的銷售 eVar 與產品專屬事件
solution: Experience Cloud,Analytics
title: 產品變數及其包含的銷售 eVar 與產品專屬事件
topic: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---


# 產品變數及其包含的銷售 eVar 與產品專屬事件 {#products-variable-with-merchandising-evars-and-product-specific-events}

以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>如果您使用 *`&&products`* 變數觸發產品專屬事件，您也必須在 *`&&events`* 變數中設定該事件。如果您沒有設定事件，系統會在處理期間將其篩選掉。

