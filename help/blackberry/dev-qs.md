---
title: 開發人員快速入門
seo-title: BlackBerry開發人員快速入門Adobe Mobile Services
description: BlackBerry開發人員快速入門指南可協助您瞭解實作Adobe Mobile Services的BlackBerry程式庫的程序。
seo-description: BlackBerry開發人員快速入門指南可協助您瞭解實作Adobe Mobile Services的BlackBerry程式庫的程序。
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# 開發人員快速入門

此資訊可協助您瞭解實施 BlackBerry 程式庫的程序。

## 取得 SDK

**本 SDK 需要 BlackBerry 10 或更新版本。**

將下載的 SDK 解壓縮後，確認下列檔案存在於 `AdobeMobile` 資料夾中:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## 新增 SDK 至您的專案

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Select **[!UICONTROL External library]** and click **[!UICONTROL Next]**.
1. 按一下&#x200B;**[!UICONTROL 「裝置程式庫」]欄位旁的****「瀏覽」[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. 按一下&#x200B;**[!UICONTROL 「模擬器程式庫」]欄位旁的****「瀏覽」[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. 按一下&#x200B;**[!UICONTROL 「Include 資料夾」]欄位旁的****「新增」[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Add the `public` folder to your includes.
1. `ADBMobile-4.0.0BETA-BlackBerry` 在資料夾中，有一 `.json` 個設定檔案 `ADBMobileConfig.json`。

   複製該檔案至專案的根目錄中。
1. Right-click on your project and select **[!UICONTROL Refresh]**.

   `.json` 檔案現在應該會顯示在 **[!UICONTROL 您的專案總管]**&#x200B;中。
1. 開啟專案的 `bar-descriptor.xml` 檔案。
1. 在視窗底部選取&#x200B;**[!UICONTROL 「資產」]標籤。**
1. 確認已選取&#x200B;**[!UICONTROL 「(全部設定)」]**，然後按一下視窗&#x200B;**[!UICONTROL 「資產」]區段中的**「新增檔案」**。**
   >[!TIP]
   >
   >QNX Momentics IDE中有個錯誤，有時會阻止這些按鈕出現。如果您看不到按鈕，請調整視窗大小，直到顯示為止。

1. 按一下 **[!UICONTROL 工作區]**。
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## 新增應用程式權限

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

該 `ADBMobileConfig.json` 檔案包含全域 SDK 設定。您必須更新一些值以便開始執行。

以下是 `ADBMobileConfig.json` 檔案的範例:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

You must at least update the `rsids` and `server` parameters. 如需詳細資訊，請參閱 [Adobe Mobile類別和方法參考](/help/blackberry/methods.md)。

現在您可以在 BlackBerry 10 應用程式中實施 Analytics。
