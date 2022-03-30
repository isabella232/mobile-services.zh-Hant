---
description: 可由移動庫自動測量的度量度量和維度
keywords: Unity
solution: Experience Cloud Services
title: 實施生命週期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# 實施生命週期{#implement-lifecycle}

有關在實施生命週期後移動庫可以自動測量的度量和維度的詳細資訊，請參見 [Android生命週期度量](/help/android/metrics.md) 或 [iOS生命週期](/help/ios/metrics.md)。

## iOS

生命週期度量在iOS自動收集。

## Android

在Unity指令碼中，您為Android SDK設定了應用程式上下文。 將以下代碼添加到 `Awake()` FIRST場景的函式：

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

要收集生命週期度量，請將以下代碼添加到所有場景指令碼中：

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
