---
description: 以下範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud,Analytics
title: 產品變數及其包含的銷售 eVar 與產品專屬事件
topic-fix: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
exl-id: 2ede6341-3068-4423-a509-c0ec3a2db5e8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Products 變數及其包含的銷售 eVar 與產品專屬事件 {#products-variable-with-merchandising-evars-and-product-specific-events}

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
