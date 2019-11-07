---
description: 處理規則不支援事件序列化。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
keywords: android;資料庫;行動;sdk
seo-description: 處理規則不支援事件序列化。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud,Analytics
title: 事件序列化
topic: 開發人員和實施
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 事件序列化 {#event-serialization}

處理規則不支援事件序列化。在行動 SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。

```java
cdata.put("&&events", "event1:12341234");
```

例如:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

