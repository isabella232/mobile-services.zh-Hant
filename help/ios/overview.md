---
description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-description: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。
seo-title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
solution: Experience Cloud,Analytics
title: 適用於 Experience Cloud 解決方案的 iOS SDK 4.x
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: ht
source-git-commit: c7400359bc19150926a67b991ba219a7fa187442
workflow-type: ht
source-wordcount: '530'
ht-degree: 100%

---


# 適用於 Experience Cloud 解決方案的 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

適用於 Experience Cloud 解決方案的 iOS SDK 4.x 可讓您測量原生 Apple iPhone 和 iPad 應用程式、在應用程式內提供目標式內容，以及透過 Audience Manager 運用與收集對象資料。

>[!IMPORTANT]
>
>自 4.21.0 版起，iOS SDK 的最低版本需求為 Xcode 12。如果您使用 Cocoapod 管理應用程式的相依性，Adobe SDK 便需搭配 Cocoapod 1.10.0 以上版本使用。

如果使用 4.21.0 或更新版本，請參閱文件並留意下列變更：

* 只要提到二進位程式庫檔案，就應改用其 XCFramework 加以取代：
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` > `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` > `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` > `AdobeMobileTV.xcframework`
* 如果在專案中手動新增 Adobe XCFramework，請確定其非內嵌型態。

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

必要須知：

* 支援 iOS 8 或更新版本

   若是 iOS 11 或更新版本，則&#x200B;**必須**&#x200B;使用 4.13.8 或更新版本的 SDK。

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
