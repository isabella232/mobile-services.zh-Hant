---
description: 無法使用處理規則設定產品變數。 在移動SDK中，必須在上下文資料參數中使用特殊語法來直接在伺服器調用中設定產品。
solution: Experience Cloud Services,Analytics
title: Products 變數
topic-fix: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
exl-id: 0575236c-9858-4bf9-a2ce-6e2667d58ddd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 7%

---

# Products 變數 {#products-variable}

無法使用處理規則設定產品變數。 在移動SDK中，必須在上下文資料參數中使用特殊語法來直接在伺服器調用中設定產品。

設定 *`products`* 變數，將上下文資料鍵設定為 `"&&products"`，並使用為*定義的語法設定值`products` 變數：

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

的 *`products`* 直接在影像請求上設定，其它變數則設定為上下文資料。 必須使用處理規則映射所有上下文資料變數：

![](assets/products-procrules.png)

你不需要把 *`products`* 變數，因為它是SDK直接在映像請求上設定的。

## Products 變數及其包含的銷售 eVar 與產品專屬事件 {#section_685D53AD3D064F9A8E225F995A9BA545}

示例 *`products`* 具體包括促銷電子廣告和產品活動。

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>如果使用 *`&&products`* 變數，還必須在 *`&&events`* 變數，否則在處理期間過濾出事件。
