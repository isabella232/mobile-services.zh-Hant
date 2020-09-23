---
description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。
seo-description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。
seo-title: 適用於Experience Cloud解決方案4.x SDK的Windows Visual Studio擴充功能
solution: Experience Cloud,Analytics
title: 適用於Experience Cloud解決方案4.x SDK的Windows Visual Studio擴充功能
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。

## 從GitHub安裝程式庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從 [GitHub下載Windows Universal SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 將下載的檔案解壓縮至本機。
1. 連按兩下ADBMobileWindowsStoreVSIX.vsix或ADBMobileWindowsPhoneVSIX.vsix檔案以開啟安裝程式。

1. 選擇 **[!UICONTROL 全局位置]** ，然後安裝庫。

## 新增專案參照 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟您的Windows 8.1或Windows Phone 8.1專案。
1. 開啟「參考管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在Windows **[!UICONTROL 8.1或]** Windows Phone 8.1的「擴充功能」標籤上，找到並選取 **[!UICONTROL Adobe Mobile SDK]**。
1. 按一 **[!UICONTROL 下「確定]** 」以儲存它。

   Adobe Mobile SDK將會新增至您的專案，如果尚未新增， **[!UICONTROL Microsoft Visual C++ Runtime]** 套件也會新增。

1. 在「設定管理員」中，選取「平台」類型，然後開始測試您的應用程式。

