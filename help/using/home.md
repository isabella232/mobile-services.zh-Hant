---
description: Adobe Mobile Services 的技術文件
seo-description: 本指南概述 Adobe Mobile Services 的技術文件和自助說明，此服務將 Adobe Experience Cloud 行動應用程式的行動行銷功能整合在一起，方便您瞭解並改善使用者與行動應用程式的互動。
seo-title: Adobe Mobile Services
solution: Experience Cloud, Analytics, Experience Cloud
title: Adobe Mobile Services
uuid: e86a77c9-4ff1-403f-a5a1-4afbdc4e6f68
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 100%

---


# Adobe Mobile Services {#adobe-mobile-services}

本指南概述 Adobe Mobile Services 的技術文件和自助說明，此服務將 Adobe Experience Cloud 行動應用程式的行動行銷功能整合在一起，方便您瞭解並改善使用者與行動應用程式的互動。

>[!IMPORTANT]
>
>您必須有 Adobe Analytics Mobile Marketing 附加元件 SKU，才能讓 Mobile Services 存取行動裝置贏取、深層連結、地理位置以及行動裝置傳訊功能。如需詳細資訊，請聯絡您的 Adobe CSM。

## 宣佈終止支援 4x SDK

在 2020 年 9 月 30 日之後，客戶可以繼續下載和使用第 4 版 SDK，但是將不提供客戶服務支援，亦無法存取論壇。Adobe Experience Platform Mobile SDK (先前稱為 v5) 將專門支援即將推出的 Adobe Experience Cloud 功能。

請參閱終止支援[常見問題](https://aep-sdks.gitbook.io/docs/version-4-sdk-end-of-support-faq)以瞭解更多資訊。

建議您在可行時，移轉至新的 Experience Platform Mobile SDK。

## 新版 Adobe Experience Cloud SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> 如果您使用 Adobe Experience Platform Mobile SDK 搭配 Adobe Launch，您&#x200B;**必須**&#x200B;同時安裝 Adobe Analytics Mobile Services 擴充功能，方可使用應用程式內訊息、推播通知或贏取連結之類的 Adobe Mobile Services 功能。如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

>[!IMPORTANT]
>
>雖然您可在使用者介面中設定功能，但您還必須下載產生的設定檔案，並將該檔案新增到 SDK 中，這些功能才會發揮作用。如需下載和設定 SDK 的詳細資訊，請參閱本頁的 *SDK 文件*&#x200B;區段。

如需最新發行說明，請參閱 [Experience Cloud 發行說明](https://docs.adobe.com/content/help/zh-Hant/release-notes/experience-cloud/current.html)。

## 熱門主題 {#section_AFFBC9EDDE5B4E4493A7C2896121A773}

以下是本指南中的幾個熱門主題：

* [快速入門](/help/using/gs/gs.md)
* [正在登入](/help/using/gs/gs-signin.md)
* [角色與權限](/help/using/gs/c-mob-roles-and-permissions.md)
* [行動量度](/help/using/gs/metrics/metrics.md)
* [傳訊](/help/using/in-app-messaging/in-app-messaging.md)
* [贏取](/help/using/acquisition-main/acquisition-main.md)
* [位置](/help/using/location/c-location-overview.md)
* [常問的問題 - Mobile Services](/help/using/faq-mobile.md)

## 開發人員

以下是可協助開發人員的連結:

* [下載行動 SDK 和工具](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md)
* [Developer](https://docs.adobe.com/content/help/zh-Hant/analytics/implementation/home.html)

## 社群資源

以下是其他資源：

* [Experience Cloud 論壇](https://forums.adobe.com/community/experience-cloud)
* [Adobe Marketing Cloud 社群](https://helpx.adobe.com/tw/marketing-cloud.html?promoid=KAWSE)
* [Idea Exchange](https://forums.adobe.com/community/experience-cloud/analytics-cloud/analytics)
* [Adobe 培訓和教學課程](https://helpx.adobe.com/tw/learning.html?promoid=KAUDK)
* [精選解決方案中心](https://www.adobe.com/tw/marketing-cloud.html)

## SDK 文件 {#section_3A500233347C4305AB545E298A827CEA}

除了使用者指南，您還可下載軟體開發套件 (SDK)，其中涵蓋自訂套件，包括您需要用來在 Adobe Mobile 中設定應用程式的設定檔案預先填入版本。

提供適用於下列平台的原生程式庫：

* [適用於 Experience Cloud 解決方案的 Android SDK 4.x](/help/android/overview.md)
* [適用於 Experience Cloud 解決方案的 iOS SDK 4.x](/help/ios/overview.md)
* [iOS 和 Android 4.x SDK 適用的 Unity 外掛程式](/help/unity/get-started.md)
* [適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件](/help/xamarin/get-started.md)
* [適用於 Experience Cloud 解決方案的 Universal Windows Platform SDK 4.x](/help/universal-windows/overview.md)
* [Windows 8.1 通用應用程式商店](/help/windows-appstore/overview.md)

   * [適用於 Experience Cloud 解決方案 4.x SDK 的 Windows Visual Studio 延伸模組](/help/windows-appstore/extensions/win-vse-4x.md)

* [適用於 Experience Cloud 解決方案的 BlackBerry 10 SDK 4.x](/help/blackberry/overview.md)

## Adobe Mobile 快速入門網路研討會 {#section_420EA66F39FE44B9B531ADF5F5465543}

請觀看 *Adobe Mobile 快速入門*&#x200B;網路研討會。([播放](https://adobe.ly/PsxCFn))

[  ![](assets/webinar.png) ](https://adobe.ly/PsxCFn)
