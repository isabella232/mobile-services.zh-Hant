---
description: 您可傳送訊號並從對象管理中擷取訪客區段。
keywords: Android；資料庫；行動；sdk
seo-description: 您可傳送訊號並從對象管理中擷取訪客區段。
seo-title: Audience Manager組態
solution: Marketing Cloud、Analytics
title: Audience Manager組態
topic: 開發人員和實施
uuid: f68d5b2e-fa2 c-4db6-98ad-d1855 a2 c45 ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

您可以從Audience Manager傳送訊號並擷取訪客區段。

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(必要)**`setContext()` 在主要活動的 `onCreate()` 方法中，一次必須呼叫方法。

以下是此方法的範例程式碼:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您在實施Analytics或Target時新增此方法呼叫，則不需要再次新增此方法。
