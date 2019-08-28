---
description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。
keywords: Android；資料庫；行動；sdk
seo-description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。
seo-title: 適用於 Experience Cloud 解決方案的 Android SDK 4.x
solution: Marketing Cloud、Analytics
title: 適用於 Experience Cloud 解決方案的 Android SDK 4.x
topic: 開發人員和實施
uuid: 56f1ff41-0365-41dd-bdde-245c823 dff07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。

>[!IMPORTANT]
>
>必須有Adobe Analytics Mobile Marketing Add-on SKU，才能讓Mobile Services存取行動裝置收購、深層連結、地理位置和行動訊息功能。如需詳細資訊，請聯絡您的Adobe CSM。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

>[!IMPORTANT]
>
>我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 [Launch](https://launch.adobe.com/)。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

>[!IMPORTANT]
>
>雖然您可以設定UI中的功能，但這些功能將無法運作，直到您下載產生的組態檔並將此檔案新增至SDK為止。如需下載和設定SDK的詳細資訊，請參閱 [核心實作與生命週期](/help/android/getting-started/dev-qs.md)。

SDK 支援以下版本的 Android:

* 4.6.0 或較早版本支援 Android 2.2(API 8) - Android 5.1.1 (API 22)
* 4.6.1 或較早版本支援 Android 2.3(API 9) 或更高版本

一些要記住的資訊:

* 在 4.2 版或更新版本中，所有點撃現在會透過 HTTP POST 傳送。

   這對收集或報告的資料沒有影響，但您必須使用支援檢查POST資料以檢視點擊的封包分析器。

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供的使用者介面，將 Adobe Experience Cloud 適用於行動應用程式的各項行動行銷功能整合在一起。若要深入了解使用者介面以及閱讀使用者文件，請參閱 [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/)。

## 發行說明 {#section_F8181DC052D44DD2A99AB40A41F6792C}

如需 Experience Cloud 發行版本的最新資訊，請參閱 [Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 自 2017 年 5 月 1 日起，不再提供額外的增強功能、額外工程支援，或 Adobe Expert Care 支援。
