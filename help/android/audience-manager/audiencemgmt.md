---
description: 您可傳送訊號並從對象管理中擷取訪客區段。
keywords: android;資料庫;行動;sdk
seo-description: 您可傳送訊號並從對象管理中擷取訪客區段。
seo-title: Audience Manager 設定
solution: Marketing Cloud,Analytics
title: Audience Manager 設定
topic: 開發人員和實施
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager 設定{#audience-manager-configuration}

您可傳送訊號並從 Audience Manager 中擷取訪客區段。

## 設定應用程式內容 {#section_37CAE496FF894FCA821F7760605574CA}

**(必要)** 只要主要活動的 `onCreate()` 方法中包含 `setContext()` 方法，就必須呼叫後者。

以下是此方法的範例程式碼:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您已在實施 Analytics 或 Target 時新增此方法呼叫，便不需要再次新增。
