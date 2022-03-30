---
description: 無法使用處理規則設定產品變數。 在移動SDK中，必須在上下文資料參數中使用特殊語法來直接在伺服器調用中設定產品。
solution: Experience Cloud Services,Analytics
title: Products 變數
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Products 變數{#products-variable}

無法使用處理規則設定產品變數。 在移動SDK中，必須在上下文資料參數中使用特殊語法來直接在伺服器調用中設定產品。

設定 *`products`* 變數，將上下文資料鍵設定為 `"&&products"`，並使用為 *`products`*:

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

*`products`* 是直接在影像要求上設定的，而其他變數則設為內容資料。必須使用處理規則映射所有上下文資料變數：

![](assets/products-procrules.png)

你不需要把 *`products`* 變數，因為它是SDK直接在映像請求上設定的。
