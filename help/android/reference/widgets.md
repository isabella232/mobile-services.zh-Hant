---
description: 可以使用與應用程式追蹤的同一方法來追蹤 Android 介面工具集。介面工具集會與您的應用程式共用應用程式內容，因此會保留點擊順序和訪客識別。
keywords: Android；資料庫；行動；sdk
seo-description: 可以使用與應用程式追蹤的同一方法來追蹤 Android 介面工具集。介面工具集會與您的應用程式共用應用程式內容，因此會保留點擊順序和訪客識別。
seo-title: Android Widget
solution: Marketing Cloud、Analytics
title: Android Widget
topic: 開發人員和實施
uuid: 1a3718ff-967b-4c8e-ae0 b-ba15 bdbda0 a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

可以使用與應用程式追蹤的同一方法來追蹤 Android 介面工具集。介面工具集會與您的應用程式共用應用程式內容，因此會保留點擊順序和訪客識別。

下列指引將協助您追蹤 Android 介面工具集:

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* 若要追蹤介面將工具集新增至主畫面的時間，請新增 `trackState` 或 `trackEvent` 呼叫至介面工具集的 `onEnabled` 方法。

* 若要追蹤從介面工具集新增應用程式的時間，請在建立啟動應用程式的目的之前，新增 `trackState` 或 `trackEvent` 呼叫。

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

