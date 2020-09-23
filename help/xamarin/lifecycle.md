---
description: 協助您實作Android生命週期量度的資訊。 系統會自動收集iOS的生命週期度量。
keywords: Xamarin
seo-description: 協助您實作Android生命週期量度的資訊。 系統會自動收集iOS的生命週期度量。
seo-title: 實施生命週期
solution: Experience Cloud
title: 實施生命週期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 1%

---


# 實施生命週期 {#implement-lifecycle}

這項資訊可協助您實作Android的生命週期量度。

>[!TIP]
>
>系統會自動收集iOS的生命週期度量。

如需實施生命週期後行動程式庫可自動測量的度量和維度，請參閱生命週期 [度量](/help/ios/metrics.md)。

## iOS

在iOS中，生命週期度量會自動收集。

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
