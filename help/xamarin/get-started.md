---
description: 本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件
keywords: Xamarin
seo-description: 本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件
seo-title: Experience Cloud解決方案4.x SDK的Xamarin元件
solution: Marketing Cloud，開發人員
title: Experience Cloud解決方案4.x SDK的Xamarin元件
uuid: e7a48107-bd0 e-47d6-b49 c-dfdance189 ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的適用的 Xamarin 元件

最近更新日期: **2019 年 1 月 10 日**

## 快速入門 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK已不再提供於Xamarin Components Store或Nubet Gallery中。若要下載 Xamarin 元件，請前往 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

將ADBMobile元件匯入Xamarin. Android專案：

1. 開啓您的Xamarin專案

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. `ADBMobile.XamarinAndroidBinding.dll` 從 **[!UICONTROL lib/Android]** 資料夾中選取。

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 新增下列項目的權限:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 如果您使用應用程式內傳訊，請新增下列活動和接收器：

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 如果您使用贏取，請新增下列接收器：

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

將ADBMobile元件匯入Xamarin. iOS專案：

1. 開啓您的Xamarin專案。
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. `ADBMobile.XamarinIOSBinding.dll` 從 **[!UICONTROL lib/ios-統一]** 資料夾中選取。

1. 新增 `ADBMobileConfig.json` 檔案至專案。


