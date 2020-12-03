---
description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。
seo-description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。
seo-title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
solution: Experience Cloud,Analytics
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---


# 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此擴充功能可讓您更輕鬆地在專案中新增Experience Cloud Solutions 4.x Windows SDK的參考。

## 從GitHub安裝程式庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從 [GitHub下載Windows Universal SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 將下載的檔案解壓縮至本機。
1. 連按兩下 **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** 檔案以開啟安裝程式。
1. 選擇 **[!UICONTROL 全局位置]** ，然後安裝庫。

## 新增專案參照 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟您的Windows 10專案。
1. 開啟「參考管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在「延伸 **[!UICONTROL 功能]** 」標籤上，找到並選 **[!UICONTROL 取Adobe Mobile SDK]**。
1. 按一 **[!UICONTROL 下「確定]** 」以儲存它。

   Adobe Mobile SDK將會新增至您的專案。 如果 **[!UICONTROL Microsoft Visual C++ Runtime]** Package尚未新增，此套件也將新增至您的專案。

1. 在「設定管理員」中，選取平台類型並開始測試您的應用程式。

