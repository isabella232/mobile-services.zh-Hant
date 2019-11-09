---
description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。
keywords: android;資料庫;行動;sdk
seo-description: 適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。
seo-title: 適用於 Experience Cloud 解決方案的 Android SDK 4.x
solution: Marketing Cloud,Analytics
title: 適用於 Experience Cloud 解決方案的 Android SDK 4.x
topic: 開發人員和實施
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# 適用於 Experience Cloud 解決方案的 Android SDK 4.x{#android-sdk-x-for-experience-cloud-solutions}

適用於 Experience Cloud 解決方案的 Android SDK 4.x 可讓您測量原生 Android 應用程式、在應用程式中提供目標式內容，以及透過對象管理運用與收集對象資料。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>您必須有 Adobe Analytics Mobile Marketing 附加元件 SKU，才能讓 Mobile Services 存取行動裝置贏取、深層連結、地理位置以及行動裝置傳訊功能。如需詳細資訊，請聯絡您的 Adobe CSM。

>[!IMPORTANT]
>
>雖然您可在使用者介面中設定功能，但您還必須下載產生的設定檔案，並將該檔案新增到 SDK 中，這些功能才會發揮作用。如需如何下載和設定 SDK 的詳細資訊，請參閱[核心實施與生命週期](/help/android/getting-started/dev-qs.md)。

SDK 支援以下版本的 Android:

* 4.6.0 或較早版本支援 Android 2.2(API 8) - Android 5.1.1 (API 22)
* 4.6.1 或較早版本支援 Android 2.3(API 9) 或更高版本

一些要記住的資訊:

* 在 4.2 版或更新版本中，所有點撃現在會透過 HTTP POST 傳送。

   這樣做對已收集或報告的資料沒有影響，但您需要使用支援檢查 POST 資料的封包分析器來檢視點撃。

* 如果您從上一個版本升級，請參閱 [4.x 移轉指南](/help/android/getting-started/migration-v3.md)。

## Adobe Mobile 使用者文件 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供的使用者介面，將 Adobe Experience Cloud 適用於行動應用程式的各項行動行銷功能整合在一起。若要深入了解 使用者介面以及閱讀使用者文件，請參閱 [Adobe Mobile Services](https://marketing.adobe.com/resources/help/zh_TW/mobile/)。

## 發行說明 {#section_F8181DC052D44DD2A99AB40A41F6792C}

如需 Experience Cloud 發行版本的最新資訊，請參閱 [Experience Cloud 發行說明](https://marketing.adobe.com/resources/help/zh_TW/whatsnew/)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>Adobe Bloodhound 已於 **2017 年 4 月 30 日**&#x200B;起停止服務。自 2017 年 5 月 1 日起，不再提供額外的增強功能、額外工程支援，或 Adobe Expert Care 支援。