---
description: 以下提供的一些資訊可協助您設定 Android 延伸功能，讓您從 Android 穿戴式裝置應用程式收集資料。
seo-description: 以下提供的一些資訊可協助您設定 Android 延伸功能，讓您從 Android 穿戴式裝置應用程式收集資料。
seo-title: Android可穿戴裝置附加註意事項
solution: Marketing Cloud,Analytics
title: Android可穿戴裝置附加註意事項
topic: 開發人員和實施
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

以下提供的一些資訊可協助您設定 Android 延伸功能，讓您從 Android 穿戴式裝置應用程式收集資料。

* Adobe Mobile Android 穿戴式裝置延伸功能須使用 Android 4.4 (KitKat) 或更高版本。
* 此功能中已新增一個額外內容值 `A.RunMode`，可指出資料來自容納應用程式還是延伸功能。

   * `RunMode` = `Application`

      點擊來自掌上型應用程式。

   * `RunMode` = `Extension`

      這款可穿戴應用打響了。

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [可穿戴式應用程式會停用應用程式內訊息](/help/android/messaging-main/messaging/messaging.md)、 [Target](/help/android/target-main/target.md)和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 。

