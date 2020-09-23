---
description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
keywords: android;library;mobile;sdk
seo-description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-title: 產品變數及其包含的銷售 eVar 與產品專屬事件
solution: Experience Cloud,Analytics
title: 產品變數及其包含的銷售 eVar 與產品專屬事件
topic: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---


# 產品變數及其包含的銷售 eVar 與產品專屬事件 {#products-variable-with-merchandising-evars-and-product-specific-events}

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
>如果您使用 *`&&products`* 變數觸發產品專屬事件，您也必須在 *`&&events`* 變數中設定該事件。如果您沒有設定事件，系統會在處理期間將其篩選掉。

