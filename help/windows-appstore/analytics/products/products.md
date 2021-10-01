---
description: 無法使用處理規則來設定產品變數。 在行動SDK中，您必須在內容資料參數內使用特殊語法，以直接在伺服器呼叫上設定產品。
solution: Experience Cloud,Analytics
title: Products 變數
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Products 變數{#products-variable}

無法使用處理規則來設定產品變數。 在行動SDK中，您必須在內容資料參數內使用特殊語法，以直接在伺服器呼叫上設定產品。

若要設定&#x200B;*`products`*&#x200B;變數，請將內容資料索引鍵設為`"&&products"`，並使用為&#x200B;*`products`*&#x200B;定義的語法來設定值：

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

*`products`* 是直接在影像要求上設定的，而其他變數則設為內容資料。必須使用處理規則對應所有內容資料變數：

![](assets/products-procrules.png)

您不需要使用處理規則對應&#x200B;*`products`*&#x200B;變數，因為變數是由SDK直接在影像要求上設定。
