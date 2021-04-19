---
description: 您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。
seo-description: 您可以在應用程式啟動時，載入另一個 ADBMobile JSON 設定檔案。
seo-title: 覆寫 ADBMobile JSON 設定路徑
solution: Experience Cloud,Analytics
title: 覆寫 ADBMobile JSON 設定路徑
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
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
