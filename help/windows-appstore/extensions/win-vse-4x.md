---
description: 此擴展為您提供了在項目中添加Experience Cloud解決方案4.x Windows SDK的參考的簡單方法。
solution: Experience Cloud Services,Analytics
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此擴展為您提供了在項目中添加Experience Cloud解決方案4.x Windows SDK的參考的簡單方法。

## 從GitHub安裝庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從下載Windows通用SDK [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 在本地解壓縮下載的檔案。
1. 按兩下ADBMobileWindowsStoreVSIX.vsix或ADBMobileWindowsPhoneVSIX.vsix檔案以開啟安裝程式。

1. 選擇 **[!UICONTROL 全局位置]** 並安裝庫。

## 向項目添加引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟Windows 8.1或Windows Phone 8.1項目。
1. 開啟「參照管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在 **[!UICONTROL 擴展]** 頁籤，找到並選擇 **[!UICONTROL AdobeMobileSDK]**。
1. 按一下 **[!UICONTROL 確定]** 來拯救它。

   AdobeMobileSDK將添加到您的項目中，如果尚未添加， **[!UICONTROL MicrosoftVisual C++運行時]** 也會添加包。

1. 在Configuration Manager中，選擇一個平台類型，然後開始測試您的應用。
