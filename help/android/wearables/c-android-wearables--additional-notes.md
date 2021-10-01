---
description: 以下提供的一些資訊可協助您設定 Android 延伸功能，讓您從 Android 穿戴式裝置應用程式收集資料。
solution: Experience Cloud,Analytics
title: Android 穿戴式裝置其他附註
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Android 穿戴式裝置: 其他附註{#android-wearables-additional-notes}

以下提供的一些資訊可協助您設定 Android 延伸功能，讓您從 Android 穿戴式裝置應用程式收集資料。

* Adobe Mobile Android Wearables 延伸功能須使用 Android 4.4 (KitKat) 或更高版本。
* 此功能中已新增一個額外內容值 `A.RunMode`，可指出資料來自容納應用程式還是延伸功能。

   * `RunMode` = `Application`

      點擊來自於手持式應用程式。

   * `RunMode` =  `Extension`

      點擊來自於穿戴式裝置應用程式。

* SDK 會將手持式應用程式的 `aid`/`vid`/`visitor` `service id`/`privacy` 狀態自動同步至穿戴式應用程式，因此請勿從穿戴式應用程式呼叫 `setPrivacyStatus`/`setUserIdentifier`/`idSync`。
* [應用程式內訊息](/help/android/messaging-main/messaging/messaging.md)、[Target](/help/android/target-main/target.md) 和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 皆已在穿戴式應用程式中停用。
