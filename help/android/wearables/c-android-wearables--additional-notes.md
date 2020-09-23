---
description: 以下是一些資訊，可協助您設定Android擴充功能，讓您從Android穿戴式應用程式收集資料。
seo-description: 以下是一些資訊，可協助您設定Android擴充功能，讓您從Android穿戴式應用程式收集資料。
seo-title: Android 穿戴式裝置其他附註
solution: Experience Cloud,Analytics
title: Android 穿戴式裝置其他附註
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 51%

---


# Android 穿戴式裝置: 其他附註{#android-wearables-additional-notes}

以下是一些資訊，可協助您設定Android擴充功能，讓您從Android穿戴式應用程式收集資料。

* Adobe Mobile Android可穿戴裝置擴充功能需要Android 4.4版(KitKat)或更新版本。
* 此功能中已新增一個額外內容值 `A.RunMode`，可指出資料來自容納應用程式還是延伸功能。

   * `RunMode` = `Application`

      點擊來自於手持式應用程式。

   * `RunMode` = `Extension`

      點擊來自於穿戴式裝置應用程式。

* SDK 會將手持式應用程式的 `aid`/`vid`/`visitor` `service id`/`privacy` 狀態自動同步至穿戴式應用程式，因此請勿從穿戴式應用程式呼叫 `setPrivacyStatus`/`setUserIdentifier`/`idSync`。
* [應用程式內訊息](/help/android/messaging-main/messaging/messaging.md)、[Target](/help/android/target-main/target.md) 和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 皆已在穿戴式應用程式中停用。

