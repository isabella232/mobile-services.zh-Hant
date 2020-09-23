---
description: 處理規則不支援事件序列化。 在Mobile SDK中，您必須在上下文資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
keywords: android;library;mobile;sdk
seo-description: 處理規則不支援事件序列化。 在Mobile SDK中，您必須在上下文資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。
seo-title: 事件序列化
solution: Experience Cloud,Analytics
title: 事件序列化
topic: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 事件序列化 {#event-serialization}

處理規則不支援事件序列化。 在Mobile SDK中，您必須在上下文資料參數中使用特殊語法，以直接在伺服器呼叫上設定序列化事件。

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

