---
description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-description: 您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。
seo-title: 覆寫 ADBMobile JSON 設定路徑
solution: Marketing Cloud、Analytics
title: 覆寫 ADBMobile JSON 設定路徑
topic: 開發人員和實施
uuid: 6872a5d-7c5a-4fdc-b7 bf-ad1534763 a6 a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

您可以在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。

`Config.overrideConfigStream(configInput)` 此方法可讓您在應用程式啓動時指定不同 `ADBMobile.json` 設定檔案的路徑。This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

使用不同的路徑呼叫此方法，會造成一次性的設定檔案覆寫，直到關閉應用程式為止。

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

