---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 實施生命週期
solution: Marketing Cloud，開發人員
title: 實施生命週期
uuid: 7ff2c194-569c-42a6-922d-dcr2 aa9 eb8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 實施生命週期{#implement-lifecycle}

如需在實施生命週期後由行動程式庫自動測量的度量和維度的詳細資訊，請參閱 [iOS中Android](/help/android/metrics.md) 或 [生命週期中的生命週期度量](/help/ios/metrics.md)。

## iOS

生命週期度量會自動收集在iOS中。

## Android

在 Unity 指令碼中，設定 Android SDK 的應用程式內容。Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

若要收集生命週期度量，請新增下列程式碼至所有場景指令碼:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

