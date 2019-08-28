---
description: 此資訊有助您執行 Android 的生命週期量度。針對 iOS，系統會自動收集生命週期量度。
keywords: Xamarin
seo-description: 此資訊有助您執行 Android 的生命週期量度。系統會自動收集 iOS 的生命週期量度。
seo-title: 實作生命週期
solution: Marketing Cloud，開發人員
title: 實作生命週期
uuid: 6dcCC12e-8b57-4231-9c74-d47 bc0 ac93 ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

此資訊可協助您實作Android的生命週期度量。

>[!TIP]
>
>系統會自動收集 iOS 的生命週期量度。

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

在iOS中，會自動收集生命週期度量。

## Android

在主要活動中，設定Android SDK的應用程式內容。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

在每個活動中，實施生命週期呼叫。

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
