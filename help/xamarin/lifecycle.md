---
description: 可協助您為Android實作生命週期量度的資訊。 系統會自動為iOS收集生命週期量度。
keywords: 沙馬林
solution: Experience Cloud
title: 實施生命週期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# 實施生命週期 {#implement-lifecycle}

此資訊可協助您為Android實作生命週期量度。

>[!TIP]
>
>系統會自動為iOS收集生命週期量度。

如需可在生命週期實施後由行動資料庫自動測量的量度和維度，請參閱[生命週期量度](/help/ios/metrics.md)。

## iOS

在iOS中，會自動收集生命週期量度。

## Android

在您的主要活動中，設定Android SDK的應用程式內容。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

在每個活動中，實作生命週期呼叫。

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
