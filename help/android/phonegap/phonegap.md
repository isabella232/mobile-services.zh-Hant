---
description: 此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。
keywords: Android；資料庫；行動；sdk
seo-description: 此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。
seo-title: PhoneGap增效模組概觀
solution: Marketing Cloud、Analytics
title: PhoneGap增效模組概觀
topic: 開發人員和實施
uuid: c5c32357-d8 df-458a-b0 e8-e0 c56040241 d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap增效模組概觀 {#phonegap-plug-in}

此外掛程式可讓您從 PhoneGap 專案傳送 Android AppMeasurement 呼叫。若要建立PhoneGap專案，請參閱 [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html)。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

>[!IMPORTANT]
>
>我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 使用 npm 安裝外掛程式 {#section_43229E57C16944C0B51531CB92089189}

執行以下命令:

```java
cordova plugin add adobe-mobile-services
```

## 手動安裝外掛程式 {#section_EA1FD59C484D44878AB509954DEE6037}

## 納入外掛程式

1. 將 `ADBMobile_PhoneGap.java` 檔案拖曳至您的 `src` 檔案夾。

   To move this file, click **[!UICONTROL OK]**.

1. 將 `ADB_Helper.js` 檔案拖曳至包含 `index.html` 檔案的資料夾

   To move this file, click **[!UICONTROL OK]**.

1. `res/xml` 在資料夾中，開啓 `config.xml` 檔案並新增外掛程式，加入下列項目：

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例如，若您的封裝名稱為 `com.example.phonegaptest`，您的 `android-package` 值將如下:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## 加入AppMeasurement程式庫

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. 將 `adobeMobileLibrary.jar` 檔案拖曳至您的 `src` 檔案夾。

   To move this file, click **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. 視專案需求而定，輸入資料庫的名稱、層級及位置。
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. 確認您已選取根應用程式，而&#x200B;**不是**&#x200B;某個應用程式中的應用程式。

   To move this file, click **[!UICONTROL OK]**.

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

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

