---
description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
keywords: Android；資料庫；行動；sdk
seo-description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-title: 產品變數及其包含的銷售 eVar 與產品專屬事件
solution: Marketing Cloud、Analytics
title: 產品變數及其包含的銷售 eVar 與產品專屬事件
topic: 開發人員和實施
uuid: 64f822a0-6cf-48e7-8886-31b93d8198a3
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>如果您使用 *`&&products`* 變數觸發產品特定事件，您也必須在 *`&&events`* 變數中設定該事件。如果您沒有設定事件，系統會在處理期間將其篩選掉。

