---
description: 您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。
seo-description: 您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。
seo-title: 覆寫 ADBMobile JSON 設定路徑
solution: Experience Cloud,Analytics
title: 覆寫 ADBMobile JSON 設定路徑
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 100%

---


# 覆寫 ADBMobile JSON 設定路徑 {#override-the-adbmobile-json-config-path}

您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。

`ADBMobile overrideConfigPath:filePath` 方法可讓您在應用程式啟動時，將路徑指定至不同的 `ADBMobile.json` 設定檔案。您必須在 `applicationDidFinishLaunchingWithOptions` 方法中呼叫此方法，且此呼叫必須在任何其他 Experience Cloud SDK 呼叫 (例如 `collectLifecycleData`) 前發生。

使用不同的路徑呼叫此方法時，會發生一次性的設定檔案覆寫，直到關閉應用程式為止。

例如:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

