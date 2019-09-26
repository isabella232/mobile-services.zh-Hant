---
description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-title: 覆寫ADBMobile JSON設定路徑
solution: Marketing Cloud,Analytics
title: Override the ADBMobile JSON config path
topic: 開發人員和實施
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. 您必須在 `applicationDidFinishLaunchingWithOptions` 方法中呼叫此方法，且此呼叫必須在任何其他 Experience Cloud SDK 呼叫 (例如 `collectLifecycleData`) 前發生。

When you call this method with a different path, a one-time override of the configuration file occurs until the application is closed.

例如:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

