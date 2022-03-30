---
description: 此擴展為您提供了在項目中添加Experience Cloud解決方案4.x Windows SDK的參考的簡單方法。
solution: Experience Cloud Services,Analytics
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此擴展提供了一種更簡便的方法，可在項目中添加Experience Cloud解決方案4.x Windows SDK的引用。

## 從GitHub安裝庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從下載Windows通用SDK [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 在本地解壓縮下載的檔案。
1. 按兩下 **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** 檔案以開啟安裝程式。
1. 選擇 **[!UICONTROL 全局位置]** 並安裝庫。

## 向項目添加引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟Windows 10項目。
1. 開啟「參照管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在 **[!UICONTROL 擴展]** 頁籤，查找並選擇 **[!UICONTROL AdobeMobileSDK]**。
1. 按一下 **[!UICONTROL 確定]** 來拯救它。

   AdobeMobileSDK將添加到您的項目中。 如果 **[!UICONTROL MicrosoftVisual C++運行時]** 尚未添加包，此包也將添加到您的項目中。

1. 在Configuration Manager中，選擇一個平台類型並開始測試您的應用。
