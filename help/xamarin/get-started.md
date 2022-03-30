---
description: 本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的 Xamarin 元件。
keywords: 沙馬林
solution: Experience Cloud Services
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# 適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件 {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主題說明如何開始使用 Mobile 解決方案 4.x SDK 的 Xamarin 元件。

最近更新日期：**2019 年 1 月 10 日**

## 快速入門 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Xamarin Components Store 或 NuGet Gallery 已不再提供 Adobe Mobile SDK。若要下載 Xamarin 元件，請前往 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

將 ADBMobile 元件匯入您的 Xamarin.Android 專案：

1. 開啟您的 Xamarin 專案
1. 開啟&#x200B;**[!UICONTROL 「參照」]**&#x200B;對話框，然後按一下&#x200B;**[!UICONTROL 「Net 組件」]**&#x200B;索引標籤。
1. 從 **[!UICONTROL lib/Android]** 資料夾中選取 `ADBMobile.XamarinAndroidBinding.dll`。
1. 將 `ADBMobileConfig.json` 檔案新增至專案的&#x200B;**[!UICONTROL 「Assets」]**&#x200B;資料夾。
1. 為下列項目新增權限：

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 如果您正在使用應用程式內傳訊，請新增以下活動和接收器：

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 如果您正在使用贏取，請新增以下接收器：

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

將 ADBMobile 元件匯入您的 Xamarin.iOS 專案：

1. 開啟您的 Xamarin 專案。
1. 開啟&#x200B;**[!UICONTROL 「參照」]**&#x200B;對話框，然後按一下&#x200B;**[!UICONTROL 「Net 組件」]**&#x200B;索引標籤。
1. 從 **[!UICONTROL lib/ios-unified]** 資料夾中選取 `ADBMobile.XamarinIOSBinding.dll`。
1. 將您的 `ADBMobileConfig.json` 檔案新增至專案。
