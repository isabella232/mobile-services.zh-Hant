---
description: 處理規則不支援事件序列化。在行動SDK中，您必須在內容資料參數內使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
solution: Experience Cloud,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 31%

---

# 事件序列化{#event-serialization}

處理規則不支援事件序列化。在行動SDK中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。

```js
cdata["&&events"] = "event1:12341234";
```

例如：

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
