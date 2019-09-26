---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Building your project
solution: Marketing Cloud，開發人員
title: 建立專案
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

針對 iOS 建置專案時，會建立 Xcode 專案。依預設，`ADBMobileWrapper.mm` 和 `AdobeMobileLibrary.a` 檔案位在新專案的「程式庫」群組中。執行下列建置應用程式所需的手動步驟:

1. 新增 `ADBMobileConfig.json` 檔案至專案。

   確定它是任一目標需要之建置的成員。

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
（此程式庫可能已連結。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

針對 Android 進行建置時，`apk` 檔案已在正確位置包含 `ADBMobileConfig.json` 檔案。By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

如果您需要使用您自己的自訂資訊清單檔案，應新增下列變更。

新增下列項目的權限:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

如果您使用應用程式內傳訊，請新增下列活動和接收器：

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

如果您使用贏取，請新增下列接收器：

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
