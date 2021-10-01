---
description: 您可以在 Android 應用程式中提供目標式內容。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud,Analytics
title: Target 設定
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 100%

---

# Target 設定 {#target-configuration}

您可以在 Android 應用程式中提供目標式內容。

## 設定應用程式內容 {#section_37CAE496FF894FCA821F7760605574CA}

**(必要)** 只要主要活動的 `onCreate()` 方法中包含 `setContext()` 方法，就必須呼叫後者。

例如:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您在實施 Analytics 或 Audience Management 時已新增此方法呼叫，便不需要再次新增。
