---
description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-title: 覆寫ADBMobile JSON設定路徑
solution: Marketing Cloud、Analytics
title: 覆寫ADBMobile JSON設定路徑
topic: 開發人員和實施
uuid: 0d1be674-c 634-a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。

`ADBMobile overrideConfigPath:filePath` 此方法可讓您在應用程式啓動時指定不同 `ADBMobile.json` 設定檔案的路徑。您必須在 `applicationDidFinishLaunchingWithOptions` 方法中呼叫此方法，且此呼叫必須在任何其他 Experience Cloud SDK 呼叫 (例如 `collectLifecycleData`) 前發生。

當您以不同的路徑呼叫此方法時，會發生一次性覆寫設定檔案，直到應用程式關閉為止。

例如:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

