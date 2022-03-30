---
description: 幫助您實施Android生命週期指標的資訊。 自動為iOS收集生命週期度量。
keywords: 沙馬林
solution: Experience Cloud Services
title: 實施生命週期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# 實施生命週期 {#implement-lifecycle}

此資訊有助於您實施Android的生命週期指標。

>[!TIP]
>
>自動為iOS收集生命週期度量。

有關在實施生命週期後移動庫可以自動測量的度量和維度，請參見 [生命週期度量](/help/ios/metrics.md)。

## iOS

在iOS，生命週期度量被自動收集。

## Android

在主活動中，為Android SDK設定應用程式上下文。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

在每個活動中，實施生命週期調用。

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
