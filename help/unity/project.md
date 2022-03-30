---
description: 建設iOS項目
keywords: Unity
solution: Experience Cloud Services
title: 建置專案
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# 建置專案{#building-your-project}

## iOS

為iOS構建時，將建立Xcode項目。 預設情況下， `ADBMobileWrapper.mm` 和  `AdobeMobileLibrary.a` 檔案將位於新項目的「庫」組中。 執行生成應用所需的以下手動步驟：

1. 將您的 `ADBMobileConfig.json` 檔案新增至專案。

   確保它是構建任何必要目標的成員。

1. 在 **[!UICONTROL 生成階段]** 頁籤，添加到以下庫的連結：

   * `SystemConfiguration.framework`
（此庫可能已連結。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>要使用SDK中的本地通知In-App消息，必須調用 `ADBMobile.EnableLocalNotifications();` 從第一個Unity Scene中的「開始」方法。

## Android

當你為Android構建時， `apk` 檔案已包括 `ADBMobileConfig.json` 檔案。 預設情況下， `AndroidManifest.xml` 檔案 `/Plugins/Android` 資料夾。

如果需要使用自己的自定義清單檔案，應添加以下更改。

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
