---
description: 此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。
keywords: phonegap
seo-description: 此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。
seo-title: PhoneGap 外掛程式
solution: Marketing Cloud,Analytics
title: PhoneGap 外掛程式
topic: 開發人員和實施
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: ht
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# PhoneGap 外掛程式{#phonegap-plug-in}

此外掛程式可讓您從 PhoneGap 專案傳送 iOS AppMeasurement 呼叫。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 建立 PhoneGap 專案

若要建立 PhoneGap 專案，請參閱 [PhoneGap](https://helpx.adobe.com/tw/experience-manager/6-4/mobile/using/phonegap.html)。

## 使用 npm 安裝外掛程式: {#section_43229E57C16944C0B51531CB92089189}

1. 執行以下命令:

   ```
   cordova plugin add adobe-mobile-services
   ```

## 手動安裝外掛程式{#section_D53BA60D488C4DB8AD2BDF90439C180A}

### 納入 AppMeasurement 資料庫

納入 AppMeasurement:

1. 將 `ADBMobile_PhoneGap.h` 和 `ADBMobile_PhoneGap.m` 拖曳至 Xcode 專案的 **[!UICONTROL Plugins]** 資料夾。
1. 完成下列設定:

   1. 選取&#x200B;**[!UICONTROL 視需要將項目複製到目標群組的資料夾中]**。
   1. 選取您要使用 AppMeasurement 程式碼的目標。

1. 將 `ADB_Helper.js` 拖曳至專案的 `www` 資料夾。
1. 在 `res/xml` 資料夾中，開啟 `config.xml` 並註冊新的外掛程式，方法是新增下列內容:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### 新增應用程式權限

AppMeasurement 資料庫需要:

1. 啟動 Xcode IDE 並開啟您的應用程式。
1. 將 **[!UICONTROL AdobeMobile]資料夾拖曳至您的專案中並完成下列設定:**

   1. 選取&#x200B;**[!UICONTROL 視需要將項目複製到目標群組的資料夾中]**。
   1. 選取&#x200B;**[!UICONTROL 為所有新增的資料夾建立群組]**。
   1. 選取您要使用 AppMeasurement 程式碼的目標，然後按一下&#x200B;**[!UICONTROL 完成]**。
   ![](assets/xcode-settings.png){width="672"}

1. 在專案目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 確認可建置應用程式且未發生非預期的錯誤。

## 實施自訂追蹤 {#section_FD102B3CDAA4492FB04E56BF17E28663}

在您想要使用追蹤的 `html` 檔案中，新增下列內容至 `<head>` 標記:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

