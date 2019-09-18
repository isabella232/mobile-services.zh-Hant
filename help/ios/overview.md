---
description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
solution: Marketing Cloud,Analytics
title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
topic: 開發人員和實施
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 1070450065776fdb7d13e9b21ce62ceeee55b80e

---


# 適用於 Experience Cloud 解決方案的 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。

>[!IMPORTANT]
>
>Adobe Analytics Mobile Marketing附加元件SKU是必要項，以讓Mobile services存取行動裝置贏取、深層連結、地理位置和行動訊息功能。 如需詳細資訊，請洽詢您的Adobe CSM。

>[!IMPORTANT]
>
>Adobe Experience Platform Mobile SDK現在支援 [iOS 13和Xcode 11][https://developer.apple.com/ios/]。 為確保順暢相容，請使 [用最新版Experience Platform Mobile SDK擴充功能](https://app.gitbook.com/@aep-sdks/s/docs/resources/frequently-asked-questions/current-sdk-versions)。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

一些要記住的資訊:

* 支援 iOS 5 或更新版本

   若是 iOS 11 或更新版本，則&#x200B;**必須**&#x200B;使用 4.13.8 或更新版本的 SDK。

* 在本 SDK 4.2 版或更新版本中，所有點撃現在會透過 HTTP POST 傳送。

   這對收集或報告的資料沒有影響，但您需要使用支援檢查POST資料的封包分析器來檢視點擊。

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile 使用者文件 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供的新使用者介面，將 Adobe Experience Cloud 適用於行動應用程式的各項行動行銷功能整合在一起。一開始，Mobile服務提供Adobe Analytics、Adobe Audience Manager和Adobe Target解決方案以及Adobe Experience Platform Identity service應用程式分析和定位功能的順暢整合。

若要深入了解 Mobile Services 使用者介面以及閱讀使用者文件，請參閱 [Adobe Mobile Services](/help/using/home.md)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 自 2017 年 5 月 1 日起，不再提供額外的增強功能、額外工程支援，或 Adobe Expert Care 支援。
