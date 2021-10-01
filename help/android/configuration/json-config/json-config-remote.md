---
description: 您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。
solution: Experience Cloud,Analytics
title: 覆寫 ADBMobile JSON 設定路徑
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# 覆寫 ADBMobile JSON 設定路徑 {#override-the-adbmobile-json-config-path}

您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。

`Config.overrideConfigStream(configInput)` 方法可讓您在應用程式啟動時，將路徑指定至不同的 `ADBMobile.json` 設定檔案。必須在任何其他 Experience Cloud SDK 呼叫前呼叫此方法 (在 `Config.collectLifecycleData()` 前)，通常是在您首次載入活動的 `onCreate` 方法中。

使用不同的路徑呼叫此方法，會造成一次性的設定檔案覆寫，直到關閉應用程式為止。

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
