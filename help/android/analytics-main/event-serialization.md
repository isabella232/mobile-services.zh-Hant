---
description: 處理規則不支援事件序列化。在 Mobile SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
keywords: android;資料庫;行動;sdk
seo-description: 處理規則不支援事件序列化。在 Mobile SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
seo-title: 事件序列化
solution: Experience Cloud,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# 事件序列化 {#event-serialization}

處理規則不支援事件序列化。在 Mobile SDK 中，您必須在內容資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。

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
