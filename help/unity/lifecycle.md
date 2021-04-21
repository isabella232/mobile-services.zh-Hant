---
description: 測量行動程式庫可自動測量的度量和維度
keywords: Unity
solution: Experience Cloud
title: 實施生命週期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# 實施生命週期{#implement-lifecycle}

如需實作生命週期後行動程式庫可自動測量的度量和維度的詳細資訊，請參閱「Android中的生命週期度量」或「iOS中的生命週期」。[](/help/android/metrics.md)[](/help/ios/metrics.md)

## iOS

生命週期度量會自動在iOS中收集。

## Android

在Unity指令碼中，您會設定Android SDK的應用程式內容。 將以下代碼添加到FIRST場景的`Awake()`函式中：

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
