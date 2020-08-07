---
description: 本主題說明如何開始使用Mobile解決方案4.x SDK的Xamarin元件。
keywords: Xamarin
seo-description: 本主題說明如何開始使用Mobile解決方案4.x SDK的Xamarin元件。
seo-title: Experience Cloud Solutions 4.x SDK的Xamarin元件
solution: Marketing Cloud,Developer
title: Experience Cloud Solutions 4.x SDK的Xamarin元件
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主題說明如何開始使用Mobile解決方案4.x SDK的Xamarin元件。

Last Updated: **January 10, 2019**

## 快速入門 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK不再可在Xamarin Components Store或NuGet Gallery中使用。 若要下載Xamarin元件，請前往 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

將ADBMobile元件匯入Xamarin.Android專案：

1. 開啟您的Xamarin專案
1. 開啟「 **[!UICONTROL 參照]** 」(References **[!UICONTROL )對話框，然後按一下「]** .Net元件」(Net Assembly)頁籤。
1. 從 `ADBMobile.XamarinAndroidBinding.dll` lib/ **[!UICONTROL Android檔案夾中選取]** 。
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. 新增下列項目的權限：

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

將ADBMobile元件匯入Xamarin.iOS專案：

1. 開啟您的Xamarin專案。
1. 開啟「 **[!UICONTROL 參照]** 」(References **[!UICONTROL )對話框，然後按一下「]** .Net元件」(Net Assembly)頁籤。
1. 從 `ADBMobile.XamarinIOSBinding.dll` lib/ios- **[!UICONTROL unified資料夾中選擇]** 。
1. 將檔案 `ADBMobileConfig.json` 新增至專案。
