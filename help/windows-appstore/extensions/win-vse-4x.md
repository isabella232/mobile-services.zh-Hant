---
description: 此延伸模組使您能以更輕鬆的方式新增 Experience Cloud 解決方案 4.x Windows SDK 的參考至您的專案。
seo-description: 此延伸模組使您能以更輕鬆的方式新增 Experience Cloud 解決方案 4.x Windows SDK 的參考至您的專案。
seo-title: 適用於Experience cloud解決方案4.x SDK的Windows Visual studio擴充功能
solution: Marketing Cloud,Analytics
title: 適用於Experience cloud解決方案4.x SDK的Windows Visual studio擴充功能
topic: 開發人員和實施
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此延伸模組使您能以更輕鬆的方式新增 Experience Cloud 解決方案 4.x Windows SDK 的參考至您的專案。

## 從GitHub安裝程式庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 下載 Windows 通用 SDK。
1. 在本機解壓縮下載檔案。
1. Double-click the ADBMobileWindowsStoreVSIX.vsix or ADBMobileWindowsPhoneVSIX.vsix file to open the installer.

1. Select Global Location and install the library.****

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟您的 Windows 8.1 或 Windows Phone 8.1 專案。
1. 開啟「參考管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在Windows 8.1 **[!UICONTROL 或]** Windows Phone 8.1的「擴充功能」標籤上，找到並選取 **[UICONTROL Adobe Mobile SDK]**。
1. 按一下&#x200B;**[!UICONTROL 「確定」]以儲存。**

   Adobe Mobile SDK將會新增至您的專案，如果尚未新增Adobe Mobile SDK，也會新增 **[UICONTROL Microsoft Visual C++ Runtime]** 。

1. In the Configuration Manager, select a Platform type, and begin testing your app.

