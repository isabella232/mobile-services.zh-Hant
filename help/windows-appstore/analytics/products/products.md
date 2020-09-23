---
description: 無法使用處理規則來設定產品變數。 在行動SDK中，您必須在內容資料參數中使用特殊語法，才能直接在伺服器呼叫上設定產品。
seo-description: 無法使用處理規則來設定產品變數。 在行動SDK中，您必須在內容資料參數中使用特殊語法，才能直接在伺服器呼叫上設定產品。
seo-title: 產品變數
solution: Experience Cloud,Analytics
title: 產品變數
topic: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 13%

---


# 產品變數{#products-variable}

無法使用處理規則來設定產品變數。 在行動SDK中，您必須在內容資料參數中使用特殊語法，才能直接在伺服器呼叫上設定產品。

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

例如：

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* 是直接在影像要求上設定的，而其他變數則設為內容資料.所有上下文資料變數必須使用處理規則進行對應：

![](assets/products-procrules.png)

您不需要使用處理規 *`products`* 則來對應變數，因為它是由SDK直接在影像要求上設定。
