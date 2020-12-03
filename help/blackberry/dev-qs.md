---
title: 開發人員快速入門
seo-title: Adobe Mobile Services的BlackBerry開發人員快速入門
description: BlackBerry開發人員快速入門手冊可協助您瞭解實作Adobe Mobile Services專用BlackBerry程式庫的程式。
seo-description: BlackBerry開發人員快速入門手冊可協助您瞭解實作Adobe Mobile Services專用BlackBerry程式庫的程式。
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# 開發人員快速入門

這些資訊可協助您瞭解實作BlackBerry程式庫的程式。

## 取得SDK

**SDK需要BlackBerry 10或更新版本。**

解壓縮下載的SDK後，確認檔案夾中存在下列檔 `AdobeMobile` 案：

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

## 將SDK新增至您的專案

1. 在您的專案上按一下滑鼠右鍵，然後選 **[!UICONTROL 取「設定]** >新 **[!UICONTROL 增資料庫」]**。
1. 選擇「 **[!UICONTROL 外部庫]** 」，然後單 **[!UICONTROL 擊「下一步」]**。
1. 按一 **[!UICONTROL 下]** 「裝置程式庫」欄 **[!UICONTROL 位旁的「瀏覽]** 」。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 在資料夾 `Device-Debug` 中，選擇並 `libADBMobileShared.so` 按一下「 **[!UICONTROL 開啟」]**。
1. 按一 **[!UICONTROL 下]** 「模擬器程式庫」欄位旁 **[!UICONTROL 的「瀏覽]** 」。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 在資料夾 `Device-Debug` 中，選擇並 `libADBMobileShared.so` 按一下「 **[!UICONTROL 開啟」]**。
1. 按一 **[!UICONTROL 下]** 「包含檔案夾」欄 **[!UICONTROL 位旁的「新增]** 」。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 將資料 `public` 夾新增至您的內容。
1. 在檔案 `ADBMobile-4.0.0BETA-BlackBerry` 夾中，有一個名 `.json` 為的配置檔案 `ADBMobileConfig.json`。

   將該檔案複製至專案的根目錄。
1. 在您的專案上按一下滑鼠右鍵，然後選取「重新 **[!UICONTROL 整理」]**。

   檔案 `.json` 現在應該會顯示在您的專案 **[!UICONTROL 總管中]**。
1. 開啟專 `bar-descriptor.xml` 案的檔案。
1. 在視窗底部選取「資產」 **[!UICONTROL 標籤]** 。
1. 確認已選 **[!UICONTROL 取（所有設定）]** ，然後按一下視窗「資產」區段中的「新增檔案 **[!UICONTROL 」(Add Files]****** )。
   >[!TIP]
   >
   >QNX Momentics IDE中有一個錯誤，有時會阻止顯示這些按鈕。 如果您看不到按鈕，請調整視窗大小，直到它們出現為止。

1. 按一下「 **[!UICONTROL 工作區]**」。
1. 在您的專 `ADBMobileConfig.json` 案中尋找檔案，然後按一下「 **[!UICONTROL 確定」]**。

您的應用程式可使用，從程式庫匯 `adobeMobileLibrary.jar` 入類別／介面 `#include <ADBMobile.hpp>`。

## 新增應用程式權限 

在 `bar-descriptor.xml` 項目目錄中，添加一行 `<permission>access_internet</permission>`，或在QNX Momentics IDE中，選擇「應用程式」頁籤權限部分上的「Internet ******** 」框。

## 更新配 `ADBMobileConfig.json` 置檔案

檔案 `ADBMobileConfig.json` 包含全域SDK設定。 您需要更新一些值才能開始使用。

The following is an example of an `ADBMobileConfig.json` file:

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

您至少必須更新 `rsids` 和參 `server` 數。 如需詳細資訊，請參 [閱Adobe Mobile類別和方法參考](/help/blackberry/methods.md)。

您現在可以在BlackBerry 10應用程式中實作Analytics。
