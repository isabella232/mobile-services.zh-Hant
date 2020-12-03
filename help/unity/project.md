---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 建置專案
solution: Experience Cloud
title: 建置專案
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# 建置專案{#building-your-project}

## iOS

當您為iOS建立時，會建立Xcode專案。 根據預設， `ADBMobileWrapper.mm` 和 `AdobeMobileLibrary.a` 檔案將位於新專案的「資料庫」群組中。 執行下列建立應用程式所需的手動步驟：

1. 將您的 `ADBMobileConfig.json` 檔案新增至專案。

   確保它是構建任何必要目標的成員。

1. 在專案 **[!UICONTROL 的「建立階段]** 」索引標籤中，新增下列程式庫的連結：

   * `SystemConfiguration.framework`
（此程式庫可能已連結。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>若要使用SDK的「本機通知應用程式內訊息」，您必須從第一個Unity `ADBMobile.EnableLocalNotifications();` 場景的「開始」方法呼叫。

## Android

當您針對Android建立檔案時， `apk` 檔案已將檔案 `ADBMobileConfig.json` 包含在正確的位置。 依預設，也會 `AndroidManifest.xml` 使用資料夾 `/Plugins/Android` 中的檔案。

如果您需要使用您自己的自訂資訊清單檔案，應新增下列變更。

為下列項目新增權限：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

如果您正在使用應用程式內傳訊，請新增以下活動和接收器：

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
