---
description: 處理規則不支援事件序列化。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
seo-description: 處理規則不支援事件序列化。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud、Analytics
title: 事件序列化
topic: 開發人員和實施
uuid: a5966d05-e218-446f-9f19-8664a84 b74 cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# 事件序列化{#event-serialization}

處理規則不支援事件序列化。在行動SDK中，您必須在上下文資料參數中使用特殊語法，直接在伺服器呼叫上設定序列化事件。

```js
cdata["&&events"] = "event1:12341234";
```

例如:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```

