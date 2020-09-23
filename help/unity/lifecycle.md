---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 實施生命週期
solution: Experience Cloud
title: 實施生命週期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 4%

---


# 實施生命週期{#implement-lifecycle}

如需實作生命週期後行動程式庫可自動測量的度量和維度的詳細資訊，請參閱Android中的生命週期度量 [，或iOS中](/help/android/metrics.md) 的生命週期 [](/help/ios/metrics.md)。

## iOS

生命週期度量會自動在iOS中收集。

## Android

在Unity指令碼中，您會設定Android SDK的應用程式內容。 將下列程式碼新增至FIRST `Awake()` 場景的函式：

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

若要收集生命週期度量，請將下列程式碼新增至您的所有場景指令碼：

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

