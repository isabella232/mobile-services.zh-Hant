---
description: 您無法透過處理規則設定產品變數。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以在伺服器呼叫上設定產品。
keywords: Android；資料庫；行動；sdk
seo-description: 您無法透過處理規則設定產品變數。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以在伺服器呼叫上設定產品。
seo-title: 產品變數
solution: Marketing Cloud、Analytics
title: 產品變數
topic: 開發人員和實施
uuid: f4484022-cb8 b-4dea-9209-1a110 ba607 df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

您無法透過處理規則設定產品變數。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以在伺服器呼叫上設定產品。

To set the *products* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *products* variable:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

例如:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

*產品* 變數會在影像要求上設定，而其他變數則設為上下文資料。所有內容資料變數都必須透過處理規則對應:

![](assets/map-products.png)

您無須使用處理規則對應&#x200B;*產品* 變數，因為此變數是由SDK直接在影像要求上設定的。
