---
description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
solution: Experience Cloud,Analytics
title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 97%

---


# 適用於 Experience Cloud 解決方案的 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。

>[!IMPORTANT]
>
>您必須有 Adobe Analytics Mobile Marketing 附加元件 SKU，才能讓 Mobile Services 存取行動裝置贏取、深層連結、地理位置以及行動裝置傳訊功能。如需詳細資訊，請聯絡您的 Adobe CSM。

>[!IMPORTANT]
>
>適用於 Experience Cloud 解決方案的 iOS SDK 4.x 現可支援 [iOS 13 和 Xcode 11](https://developer.apple.com/ios/)。為確保可順暢相容，請使用 4.x iOS SDK 的最新版本。如需最新版本的詳細資訊，請參閱[發行說明](/help/ios/rel-notes.md)。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

一些要記住的資訊:

* 支援 iOS 8 或更新版本

   若為iOS 11或更新版本， **您必須** 有SDK 4.13.8版或更新版本。

* 在本 SDK 4.2 版或更新版本中，所有點撃現在會透過 HTTP POST 傳送。

   這樣做對已收集或報告的資料沒有影響，但您需要使用支援檢查 POST 資料的封包分析器來檢視點撃。

* 如果您從上一個版本升級 (2.x 或 3.x)，請參閱 [4.x 移轉指南](/help/ios/getting-started/migration-v3.md)。

## Adobe Mobile 使用者文件 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供的新使用者介面，將 Adobe Experience Cloud 適用於行動應用程式的各項行動行銷功能整合在一起。一開始，Mobile Services 無縫整合了 Adobe Analytics、Adobe Audience Manager 和 Adobe Target 解決方案的應用程式分析和目標鎖定功能，以及 Adobe Experience Platform Identity Service。

若要深入了解 Mobile Services 使用者介面以及閱讀使用者文件，請參閱 [Adobe Mobile Services](/help/using/home.md)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>Adobe Bloodhound 已於 **2017 年 4 月 30 日**&#x200B;起停止服務。自 2017 年 5 月 1 日起，不再提供額外的增強功能、額外工程支援，或 Adobe Expert Care 支援。
