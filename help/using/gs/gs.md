---
description: 此資訊可協助您瞭解及使用 Adobe Mobile Services。
keywords: mobile
seo-description: 此資訊可協助您瞭解及使用 Adobe Mobile Services。
seo-title: 快速入門
solution: Experience Cloud,Analytics
title: 快速入門
topic: Metrics
uuid: a7ae7c5a-dab8-4603-b4cd-af73a2f09f71
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 13%

---


# 入門{#getting-started}

此資訊可協助您瞭解及使用 Adobe Mobile Services。

Adobe Mobile Services由下列部分組成：

* Adobe Mobile Services 使用者介面
* Adobe Mobile SDK

對於希望以最有效的方式提高使用者參與度並證明其行動應用程式投資的投資報酬率(ROI)的企業公司，Adobe提供端對端解決方案Adobe Mobile Services，以取得並吸引應用程式使用者，並分析和最佳化其體驗。

如今，行動應用程式的版圖與智慧型手機初次啟動時大不相同。 擁有行動應用程式將客戶與品牌聯繫已不夠；如今，您必須跨通道打造連貫、吸引人的客戶體驗，並將行動應用程式當做策略性觸點，以吸引最忠誠、高價值的客戶。 但是，讓這些使用者與您的應用程式互動需要引人入勝的內容、情境式通知、智慧個人化以及整合式應用程式分析等。

## Adobe Mobile Services 使用者介面 {#mobile-services-ui}

下列瀏覽器支援Mobile Services UI:

* Google Chrome（最新的兩個版本）
* Mozilla Firefox（最新的兩個版本）
* Apple Safari（最新的兩個版本）
* Microsoft Edge（最新的兩個版本）

Adobe Mobile Services 可透過以下方式提高行動應用程式的互動率:

### 贏取

在 *Acquire中*，您會使用付費、擁有和免費的媒體來推動使用者在頂尖應用程式商店中下載應用程式。 使用Adobe Mobile Services，您可以加速應用程式使用者贏取程式。

Adobe Mobile Services提供使用者贏取工作流程，包括贏取追蹤和深層連結，可衡量通道在贏取應用程式使用者時的成效。 使用行銷連結追蹤使用者來自哪些管道，您便可洞察哪些是吸引高價值及高參與使用者最有效的贏取管道。

此外，透過深層連結，您可以直接將使用者帶入您希望他們檢視的應用程式內容，並鼓勵他們視需要安裝您的應用程式。

收購提供下列主要功能：

* 應用程式的贏取分析
* 跨應用程式商店追蹤連結
* 深入連結至應用程式
* 與廣告網路的回傳整合

如需此階段的詳細資訊，請參 [閱贏取](/help/using/acquisition-main/acquisition-main.md)。

### 分析

在「 *分析*」中，您可以瞭解消費者如何使用行動應用程式，以及他們轉換或回來的原因。

有了Adobe Analytics，您就可以深入瞭解使用者如何下載、安裝和開啟應用程式。 您也可以測量並分析應用程式內容和UI、進行世代分析、路徑分析和流失。 借助Adobe Analytics，您可以使用中央資料存放區來通知您的行銷決策，並減少組織內的行銷資料孤島。

您可以使用Adobe Audience Manager以豐富的資料豐富受眾細分，提供更情境化的個人化體驗。

*Analyze* 提供下列主要功能：

* 應用程式參與分析
* 路徑和漏斗分析
* 世代與留存分析
* 位置分析
* 廣泛的裝置與平台支援

如需您可執行和分析客戶之報表的詳細資訊，請參閱 [報表](/help/using/usage/usage.md)。

### 參與

在 *Engage*&#x200B;中，您可以使用相關的推播通知和應用程式內訊息與使用者溝通。 透過定位的推播通知和應用程式內訊息，您可以確保使用者繼續返回您的應用程式。 透過Analytics的區段支援，您可以將推播通知定位至會回應並提升其轉換傾向的使用者區段。

*Engage* 提供下列主要功能：

* 推播通知由分析區段觸發。
* 即時分析、警報和新選件／內容會觸發應用程式內訊息。
* 瞭解檢視、點進率和下遊行為

### Adobe Mobile 訊息

您可以使用推播和應用程式內通知與使用者通訊。 推播通知會透過裝置上的作業系統傳送，而應用程式內訊息則會在使用者主動與應用程式互動時在應用程式中傳送。 應用程式內訊息通常可包含多種其他格式，例如快顯視窗和插播式訊息。

在Adobe Mobile中，您可以設定下列類型的訊息：

**推播通知**（出現在您的應用程式外）提供下列功能：

* 透過相關的推播通知，推動重新參與。
* 建立、細分訊息，並傳送訊息給已下載品牌應用程式並透過選擇加入接受以接收推播通知的客戶。
* 是由應用程式商店伺服器端傳送，而非從行動應用程式傳送。

For more information about creating push notifications, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

**應用程式內通知** ，提供下列功能：

* 在使用者處於應用程式工作階段時，引導他們執行特定動作。
* 其他格式（警報、全螢幕）是因為訊息是由應用程式傳送，而非推播傳送網路。
* 由即時分析觸發。
* 允許跨促銷應用程式和產品。
* 鼓勵使用者離開應用程式商店評分。
* 提供即時和位置式訊息

如需建立應用程式內訊息的詳細資訊，請 [參閱「建立應用程式內訊息」](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。

### 最佳化

在「 *最佳化*」中，您可以最佳化轉換（訂閱、商務、廣告收入等）並改善客戶維繫率。 最佳化應用程式中的使用者體驗，可協助您個人化內容，以提高投資報酬率和轉化率。

如需有關測試和 Adobe Target 的詳細資訊，請前往 [Adobe Target](https://docs.adobe.com/content/help/zh-Hant/target/using/target-home.html)。

### 地理定位

行動裝置可讓您在消費者與應用程式互動時，先知其所在位置，或透過GPS定位讓其在背景執行。 借助地理定位，Adobe Target可讓您在鄰近地區重要的時候，提供量身打造、相關的內容、優惠或訊息。 您可以定位在某個興趣點的定義半徑內或在iBeacon附近以及具有相關推播通知的使用者。

Adobe Target for Mobile應用程式現在可充份運用Adobe Analytics提供的增強細分與報告功能。 這表示Adobe Target可運用Analytics中所有關鍵應用程式量度，以利用這些量度進行定位和個人化；此外，它還能更深入地報告測試成功，讓行銷人員更瞭解這些「如果」的問題——這些問題的答案可能會避免應用程式行銷人員面臨顯示應用程式投資回報的壓力。 應用程式整合的Analytics/Target提供整合的方案，代表市場上最強穩的應用程式參與解決方案。

如需有關位置的詳細資訊，請參閱下列內容:

* [Mobile Services 使用者指南中的位置](/help/using/location/c-location-overview.md)
* Android SDK 指南中的[位置一節](/help/android/location/location.md)
* iOS SDK 指南中的[位置一節](/help/ios/location/location.md)

## Adobe Mobile SDK {#mobile-services-sdk}

Adobe 提供端對端行動行銷解決方案，可提升客戶在所有行動領域的參與率。只要使用一個SDK，您就可以存取Adobe Analytics、Adobe Campaign和Adobe Audience Manager的功能，這可降低管理多個不同SDK的技術成本。

Adobe Mobile SDK提供下列功能：

* 端對端行動互動

   您可以使用一個輕量型且整合的Adobe Mobile SDK，跨平台衡量和最佳化應用程式。
* 贏取新客戶並提供引人入勝的微型瞬間

   * 透過針對性的推播通知（包括支援豐富式媒體和應用程式內傳訊），讓使用者一次又一次地回到您的應用程式。
   * 使用深層連結，將應用程式使用者直接帶入您想要的內容。

* 衡量並最佳化體驗以提高投資報酬率

   您可以深入瞭解應用程式生命週期度量，包括漏斗分析（下載、安裝、開啟）、動作（包括作業長度、當機、信標和訊息互動）。
* 全面

   * 廣泛支援領先的行動作業系統和跨平台開發工具。
   * 在智慧型手機、平板電腦、可穿戴裝置和OTT(Over-the-top)主控台上提供廣泛的裝置支援。

* 整合

   * 單一SDK適用於多種解決方案（Analytics、Campaign和Audience Manager），可縮短開發人員的建置時間和工作量。
   * 收集「基準」應用程式生命週期量度只需要一行程式碼。
   * 隨著行動策略的發展，您可以輕鬆啟動Adobe Experience Cloud功能，以取得、分析並吸引使用者。

* 快速輕量型

   * 將傳送資料至Adobe伺服器和協力廠商系統的裝置處理負載降到最低。
   * 檔案小巧可將送出至應用程式商店的應用程式套件大小降到最低。

For more information about the Adobe Mobile SDKs, see [Android SDK 4.x for Experience Solutions](https://docs.adobe.com/content/help/zh-Hant/mobile-services/android/overview.html) and [iOS SDK 4.x for Experience Cloud Solutions](https://docs.adobe.com/content/help/zh-Hant/mobile-services/ios/rel-notes.html).
