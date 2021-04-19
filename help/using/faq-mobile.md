---
description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
keywords: 行動
seo-description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
seo-title: 常見問題
solution: Experience Cloud,Analytics
title: 常見問題
topic-fix: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
exl-id: d7dfc36e-56f0-498a-ad50-93fee90cb6ff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 100%

---

# 常問的問題 {#frequently-asked-questions}

下表包含 Adobe Mobile Services 的常見問題清單:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### 是否會經常更新 SDK？

是，我們會經常進行更新，致力於為您提供功能最豐富、符合標準且安全的 SDK。我們通常每個月推出一個新版本。這些 SDK 更新為簡易替換元件 (適用於 4x 版)，可協助您輕鬆實作。如需深入了解我們更新的詳細資訊，請參閱我們的[版本資訊](https://docs.adobe.com/content/help/zh-Hant/release-notes/experience-cloud/current.html)。

### 我應該使用什麼 SDK 版本?

我們目前的 SDK 為 4.11 版。如需詳細資訊，請參閱我們的[版本資訊](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)。

### 可以在哪裡下載 SDK?

如需下載個別行動平台的 SDK，請前往[管理應用程式設定](/help/using/c-manage-app-settings/c-manage-app-settings.md)區段。

### 如何配置 SDK?

建立新應用程式報表套裝之後，請瀏覽至「管理應用程式設定」，並在應用程式資訊頁面上設定所有必要選項。在儲存您的配置後，從「管理應用程式設定」頁面的底部下載必要的 SDK。SDK 會預先設定您已儲存的選項，可在 SDK 封裝內的 `ADBMobileConfig.json` 檔案中找到。如果您在「管理應用程式設定」頁面上變更任何 SDK 設定，請確保重新下載 SDK 檔案或更新包含必要變更的 `ADBMobileConfig.json` 檔案。

### Adobe Mobile SDK 是否針對 iOS 支援 IPv6？

Adobe Mobile SDK 使用標準 iOS 和 Android 網路堆疊。針對 iOS，SDK 使用 NSURLSession (iOS 7+ 版) 及 NSURLConnection (iOS 7 或更新版本)，與 IPv6 完全相容。已建立或使用其自有網路堆疊的開發人員需要檢閱是否有其他和緩考量。以下是來自 Apple 的額外資訊:

*如果您使用高層級網路 API (例如 NSURLSession 和 CFNetwork 架構) 撰寫用戶端應用程式並依名稱連接，則不需變更應用程式的任何項目即可搭配 IPv6 地址使用。* 如需詳細資訊，請參閱[支援 IPv6 DNS64/NAT64 網路](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 生命週期量度是什麼？

生命週期量度是「即時可用」量度，當 SDK 首次實作於您的應用程式中時會自動收集這些量度。如需詳細資訊，請參閱[生命週期量度 (Android)](/help/android/metrics.md) 和[生命週期量度 (iOS)](/help/ios/metrics.md)。

### 如何疑難排解處理規則?

如需詳細資訊，請參閱[處理規則的提示和訣竅](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)。

### 可以將我的分析資料傳送至多個報表套裝嗎？

是。SDK 能傳送資料至多個 Adobe Analytics 報表套裝。若要使用影像要求來在多個報表套裝中擷取資料，請在 檔案內&#x200B;**[!UICONTROL 分析]**&#x200B;區段下的 **[!UICONTROL rsids 欄位中設定多個報表套裝 ID，並以逗號分隔且請勿包含空格。]**`ADBMobileConfig.json`如需詳細資訊，請參閱 [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)。

### Mobile 造訪次數與啟動次數有何不同？

當使用者首次開啟應用程式，或在離開應用程式超過指定的逾時值後返回應用程式時，SDK 就會測量啟動次數。**[!UICONTROL 檔案中的]** lifecycleTimeout`ADBMobileConfig.json` 欄位內，一般逾時為 5 分鐘 (300 秒)。造訪次數是由 Adobe Analytics 在不超過造訪逾時下，根據 SDK 所傳送的第一個和最後一個資料點擊在伺服器端進行的計算。一般而言，報表套裝的工作階段逾時會設定為 30 分鐘。儘管造訪次數來自傳統網頁分析，這些點擊仍可讓您洞察使用者如何進入及離開您的應用程式。

## 傳訊 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 推播通知是否有大小或其他限制？

推送通知訊息有 140 個字元的限制。可能會傳送或排程的通知數或通知傳送頻率並無限制。

### 是否支援推播通知的自訂裝載？

是，我們提供以 JSON 編碼的自訂推播裝載。Android 和 iOS 裝載分別限制為 4KB 及 2KB。這些裝載會透過推送或本機通知傳送至應用程式。如需詳細資訊，請參閱[體驗: 推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 應用程式內訊息是否有大小限制？

Adobe Mobile Services 中所建立的已發佈和使用中應用程式內訊息，託管於具有每個應用程式報表套裝 15MB 大小限制的伺服器。儘管此限制套用於使用 Adobe 託管的訊息內容和資源，但對於應用程式內訊息在其他主機或應用程式內的主機上可能會參照的資源則沒有限制。

### 我可以針對應用程式內訊息使用自有的 HTML 嗎？

是，我們針對應用程式內訊息支援自訂 HTML。如需詳細資訊，請參閱[體驗: 應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

### 我可以使用哪些觸發器來傳送推播通知或應用程式內訊息？

行銷人員可以選擇任何 Analytics 資料或傳送作為觸發器的事件，以顯示應用程式內訊息。應用程式內訊息會使用於裝置上本機發生的觸發器。如果選擇多個觸發器，所有觸發器必須發生在相同點擊中，訊息才會顯示。如需詳細資訊，請參閱[體驗: 應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

會使用既存的 Adobe Analytics 區段或可建立在已收集之歷史 Analytics 資料上的自訂區段來傳送推送訊息。如需詳細資訊，請參閱[體驗: 推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 為什麼我輸入的應用程式內、推送或行銷連結名稱出現錯誤?

您無法在使用相同上層報表套裝或 VRS 的多個應用程式中使用相同的應用程式內訊息、推送訊息或行銷連結名稱。若要解決此問題，請針對應用程式內訊息、推送訊息或行銷連結名稱輸入其他名稱。

## 位置 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 我可以擁有的特定地標 (POI) 是否有所限制?

沒有特定限制，但為求理想效能以及使用者裝置的記憶體限制之故，我們建議您建立或者上傳最多 5000 個特定地標。

## 贏取 {#section_B37F1129CD5843E890D0E54179455357}

### 我可以將行銷活動歸因於應用程式內活動嗎？

是。Adobe Mobile Services 可協助您建立行銷訣竅，有助於促銷及促進您應用程式的流量，並將贏取行銷活動與應用程式內分析和轉換關聯。如需詳細資訊，請參閱[贏取](/help/using/acquisition-main/acquisition-main.md)。

### 如何設定連結來贏取及追蹤新的應用程式使用者?

您可以建立行銷連結，將使用者路由至從 Apple App Store 和 Google Play 下載應用程式。這些連結會成為創造成功下載事件的得力助手。如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。
