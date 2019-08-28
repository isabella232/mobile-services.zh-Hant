---
description: 此範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-description: 此範例為產品變數及其包含的銷售 eVar 與產品專屬事件。
seo-title: 產品變數及其包含的銷售 eVar 與產品專屬事件
solution: Marketing Cloud、Analytics
title: 產品變數及其包含的銷售 eVar 與產品專屬事件
topic: 開發人員和實施
uuid: 94e882e4-b19 d-4c48-9dfb-331464490347
translation-type: tm+mt
source-git-commit: b630c5cf09be7fbe31018cbf50564001eb6e2a5a

---


# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

此範例為產品變數及其包含的銷售 eVar 與產品專屬事件。

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
>如果您使用 *`&&products`* 變數觸發產品特定事件，您也必須在 *`&&events`* 變數中設定該事件，否則該事件在處理期間會被過濾掉。

