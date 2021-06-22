---
description: 此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。
keywords: android;資料庫;行動;sdk
seo-description: 此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。
seo-title: PhoneGap 外掛程式概述
solution: Experience Cloud,Analytics
title: PhoneGap 外掛程式概述
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 97%

---

# PhoneGap 外掛程式概述 {#phonegap-plug-in}

此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。若要建立 PhoneGap 專案，請參閱 [PhoneGap](https://helpx.adobe.com/tw/experience-manager/6-4/mobile/using/phonegap.html)。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 使用 npm 安裝外掛程式 {#section_43229E57C16944C0B51531CB92089189}

執行以下命令：

```java
cordova plugin add adobe-mobile-services
```

## 手動安裝外掛程式 {#section_EA1FD59C484D44878AB509954DEE6037}

## 納入外掛程式

1. 將 `ADBMobile_PhoneGap.java` 檔案拖曳至 `src` 資料夾。

   若要移動此檔案，請按一下&#x200B;**[!UICONTROL 確定]**。

1. 將 `ADB_Helper.js` 檔案拖曳至包含 `index.html` 檔案的資料夾

   若要移動此檔案，請按一下&#x200B;**[!UICONTROL 確定]**。

1. 在 `res/xml` 資料夾中，開啟 `config.xml` 檔案並註冊新的外掛程式，方法是新增下列內容:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例如，若您的封裝名稱為 `com.example.phonegaptest`，您的 `android-package` 值將如下:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## 納入 AppMeasurement 資料庫

1. 若要下載 AppMeasurement 資料庫，請參閱[取得 SDK](/help/android/getting-started/dev-qs.md)。
1. 將 `adobeMobileLibrary.jar` 檔案拖曳至 `src` 資料夾。

   若要移動此檔案，請按一下&#x200B;**[!UICONTROL 確定]**。

1. 按一下右鍵`adobeMobileLibrary.jar`檔案，然後選擇&#x200B;**[!UICONTROL 添加為庫]**。
1. 視專案需求而定，輸入資料庫的名稱、層級及位置。
1. 將 `ADBMobileConfig.json` 檔案拖曳至應用程式根目錄中的 `assets` 資料夾。
1. 確認您已選取根應用程式，而&#x200B;**不是**&#x200B;某個應用程式中的應用程式。

   若要移動此檔案，請按一下&#x200B;**[!UICONTROL 確定]**。

## 新增應用程式權限 

AppMeasurement 資料庫需要下列權限，才能傳送資料及記錄離線追蹤呼叫:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

若要新增這些權限，請在應用程式專案目錄的 `AndroidManifest.xml` 檔案中新增下列行:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

啟用應用程式內傳訊:

更新 AndroidManifest.xml 以宣告全螢幕活動並啟用訊息通知處理常式:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

如果您在 Adobe Mobile Services 中建立訊息時選取模式配置，請選取下列其中一種主題:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

例如:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## 實施自訂追蹤 {#section_FD102B3CDAA4492FB04E56BF17E28663}

在您想要使用追蹤的 `html` 檔案中，新增下列內容至 `<head>` 標籤:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
