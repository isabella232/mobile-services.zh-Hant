---
description: 此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。
keywords: phonegap
seo-description: 此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。
seo-title: PhoneGap 外掛程式
solution: Marketing Cloud,Analytics
title: PhoneGap 外掛程式
topic: 開發人員和實施
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap plug-in{#phonegap-plug-in}

此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

若要建立PhoneGap專案，請參 [閱PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html)。

## 使用 npm 安裝外掛程式: {#section_43229E57C16944C0B51531CB92089189}

1. 執行以下命令:

   ```
   cordova plugin add adobe-mobile-services
   ```

## 手動安裝外掛程式 {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### 包含AppMeasurement程式庫

納入 AppMeasurement:

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. 完成下列設定:

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. 選取您要使用 AppMeasurement 程式碼的目標。

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### 新增應用程式權限

AppMeasurement 資料庫需要:

1. 啟動 Xcode IDE 並開啟您的應用程式。
1. 將 **[!UICONTROL AdobeMobile]資料夾拖曳至您的專案中並完成下列設定:**

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Select **[!UICONTROL Create groups for any added folders]**.
   1. Select the targets where you want to use AppMeasurement code and click **[!UICONTROL Finish]**.
   ![](assets/xcode-settings.png){width="672"}

1. 在專案目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 確認可建置應用程式且未發生非預期的錯誤。

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

