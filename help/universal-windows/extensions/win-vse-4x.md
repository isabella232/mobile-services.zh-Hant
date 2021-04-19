---
description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud解決方案4.x Windows SDK的參考。
seo-description: 本擴充功能可讓您更輕鬆地在專案中新增Experience Cloud解決方案4.x Windows SDK的參考。
seo-title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
solution: Experience Cloud,Analytics
title: 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---

# 適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此擴充功能可讓您更輕鬆地在專案中加入Experience Cloud解決方案4.x Windows SDK的參考。

## 從GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}安裝程式庫

1. 從[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)下載Windows Universal SDK。
1. 將下載的檔案解壓縮至本機。
1. 連按兩下&#x200B;**[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]**&#x200B;檔案以開啟安裝程式。
1. 選擇&#x200B;**[!UICONTROL 全局位置]**&#x200B;並安裝庫。

## 新增專案{#section_00C14FE9243D4330BE1F4BB56FCF08B1}的參考

1. 開啟您的Windows 10專案。
1. 開啟「參考管理器」(Reference Manager)對話框。

   ![](assets/ref_manager.png)

1. 在&#x200B;**[!UICONTROL Extensions]**&#x200B;標籤上，找到並選取&#x200B;**[!UICONTROL Adobe行動SDK]**。
1. 按一下&#x200B;**[!UICONTROL 確定]**&#x200B;保存。

   AdobeMobile SDK將會新增至您的專案。 如果&#x200B;**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;套件尚未新增，此套件也會新增至您的專案。

1. 在「設定管理員」中，選取平台類型並開始測試您的應用程式。
