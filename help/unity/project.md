---
description: 建立iOS專案
keywords: Unity
solution: Experience Cloud
title: 建置專案
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# 建置專案{#building-your-project}

## iOS

當您為iOS建立時，會建立Xcode專案。 預設情況下，`ADBMobileWrapper.mm`和`AdobeMobileLibrary.a`檔案將位於新項目的「庫」組中。 執行下列建立應用程式所需的手動步驟：

1. 將您的 `ADBMobileConfig.json` 檔案新增至專案。

   確保它是構建任何必要目標的成員。

1. 在專案的&#x200B;**[!UICONTROL 建置階段]**&#x200B;標籤中，新增下列程式庫的連結：

   * `SystemConfiguration.framework`
（此程式庫可能已連結。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>若要使用SDK的「本機通知應用程式內訊息」，您必須從第一個Unity場景的「開始」方法呼叫`ADBMobile.EnableLocalNotifications();`。

## Android

當您建立Android版本時，`apk`檔案已將`ADBMobileConfig.json`檔案包含在正確位置。 預設情況下，也會使用`/Plugins/Android`資料夾中的`AndroidManifest.xml`檔案。

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
