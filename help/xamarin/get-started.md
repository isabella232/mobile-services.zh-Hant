---
description: 本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件
keywords: Xamarin
seo-description: 本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件
seo-title: Experience Cloud Solutions 4.x SDK的Xamarin元件
solution: Marketing Cloud,Developer
title: Experience Cloud Solutions 4.x SDK的Xamarin元件
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件

最近更新日期: **2019 年 1 月 10 日**

## 快速入門 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Xamarin Components Store或NuGet Gallery中不再提供Adobe Mobile SDK。 若要下載 Xamarin 元件，請前往 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

將ADBMobile元件匯入Xamarin.Android專案：

1. 開啟您的Xamarin專案

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/Android folder.`ADBMobile.XamarinAndroidBinding.dll`****

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 新增下列項目的權限:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. If you are using In-app messaging, add the following activity and receiver :

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. If you are using acquisition, add the following receiver :

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

將ADBMobile元件匯入Xamarin.iOS專案：

1. 開啟您的Xamarin專案。
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/ios-unified folder.`ADBMobile.XamarinIOSBinding.dll`****

1. 新增 `ADBMobileConfig.json` 檔案至專案。


