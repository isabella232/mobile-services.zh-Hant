---
description: 此擴充功能可讓您透過更簡單的方式，在專案中新增Experience Cloud解決方案4.x Windows SDK的參考。
solution: Experience Cloud,Analytics
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此擴充功能可讓您透過更簡單的方式，在專案中新增Experience Cloud解決方案4.x Windows SDK的參考。

## 從GitHub安裝程式庫 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 從[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)下載Windows通用SDK。
1. 將下載的檔案解壓縮至本機。
1. 連按兩下ADBMobileWindowsStoreVSIX.vsix或ADBMobileWindowsPhoneVSIX.vsix檔案以開啟安裝程式。

1. 選擇&#x200B;**[!UICONTROL 全局位置]**&#x200B;並安裝庫。

## 新增參考至您的專案 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 開啟Windows 8.1或Windows Phone 8.1專案。
1. 開啟「參考管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在Windows 8.1或Windows Phone 8.1的&#x200B;**[!UICONTROL 擴充功能]**&#x200B;標籤上，找到並選取&#x200B;**[!UICONTROL Adobe行動SDK]**。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以保存它。

   AdobeMobile SDK將會新增至您的專案，如果尚未新增，也會新增&#x200B;**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;套件。

1. 在Configuration Manager中，選取平台類型，然後開始測試您的應用程式。
