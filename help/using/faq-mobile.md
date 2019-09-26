---
description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
keywords: 行動
seo-description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
seo-title: 常見問題
solution: Marketing Cloud,Analytics
title: 常見問題
topic: 量度
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 常問的問題 {#frequently-asked-questions}

The following table contains a list of frequently asked questions for Adobe Mobile Services:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### 您是否經常更新 SDK?

是，我們經常進行更新，致力於為您提供功能最豐富、標準相容且安全的 SDK。我們通常每個月推出一個新版本。這些 SDK 更新為簡易替換元件 (適用於 4x 版)，可協助您輕鬆實作。如需深入了解我們更新的詳細資訊，請參閱我們的[版本資訊](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)。

### 我應該使用什麼 SDK 版本?

我們目前的 SDK 為 4.11 版。如需詳細資訊，請參閱我們的[版本資訊](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)。

### 可以在哪裡下載 SDK?

The SDKs for individual mobile platforms may be downloaded by visiting the Manage App Settings section.[](/help/using/c-manage-app-settings/c-manage-app-settings.md)

### 如何配置 SDK?

建立新的應用程式報表套裝後，請導覽至「管理應用程式設定」，並在應用程式資訊頁面上設定所有必要的選項。 在儲存您的配置後，從「管理應用程式設定」頁面的底部下載必要的 SDK。The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Adobe Mobile SDK 是否支援 iOS 適用的 IPv6?

Adobe Mobile SDK 使用標準 iOS 和 Android 網路堆疊。對於iOS,SDK會使用完全符合IPv6的NSURLSession（iOS 7+版）和NSURLConnection（iOS 7和更新版本）。 已建立或使用自己網路堆疊的開發人員可能會想要檢視是否有其他減輕負擔的考量。 Here is some additional information from Apple:

*如果您使用高階網路API（例如NSURLSession和CFNetwork架構）編寫用戶端應用程式，並依名稱連線，則您不需要變更任何項目，就能讓應用程式使用IPv6位址。* For more information see, [Supporting IPv6 DNS64/NAT64 Networks](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 生命週期量度是什麼?

生命週期量度是「即時可用」量度，當 SDK 首次實作於您的應用程式中時會自動收集這些量度。For more information, see Lifecycle Metrics (Android) and Lifecycle Metrics (iOS).[](/help/android/metrics.md)[](/help/ios/metrics.md)

### 如何疑難排解處理規則?

如需詳細資訊，請參閱[處理規則的提示和訣竅](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)。

### 可以將我的分析資料傳送至多個報表套裝嗎?

是。SDK 能傳送資料至多個 Adobe Analytics 報表套裝。若要使用影像要求來在多個報表套裝中擷取資料，請在 檔案內&#x200B;**[!UICONTROL 分析]區段下的****rsids[!UICONTROL 欄位中設定多個報表套裝 ID，並以逗號分隔且請勿包含空格。]**`ADBMobileConfig.json`For more information, see ADBMobile JSON Config.[](/help/ios/configuration/json-config/json-config.md)

### 行動造訪與啟動有何不同?

當使用者首次開啟應用程式，或在離開應用程式超過指定的逾時值後返回應用程式時，會依 SDK 測量啟動。The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. 造訪數是由 Adobe Analytics 在不超過造訪逾時下，根據 SDK 所傳送的第一個和最後一個資料點擊在伺服器端進行的計算。一般而言，報表套裝的作業逾時是設定為 30 分鐘。儘管造訪數來自傳統網頁分析，這些造訪數仍可讓您洞察使用者如何進入及離開您的應用程式。

## 傳訊 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 推送通知是否有大小或其他限制?

推送通知訊息有 140 個字元的限制。可傳送或排程的通知數或是通知傳送頻率並沒有限制。

### 是否支援推送推知的自訂裝載?

是，我們提供可以 JSON 編碼的自訂推送裝載。Android 和 iOS 裝載分別限制為 4KB 及 2KB。這些裝載會透過推送或本機通知傳送至應用程式。如需詳細資訊，請參閱 [體驗：推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 這些大小限制是否關於應用程式內訊息?

Adobe Mobile Services 中所建立的已發佈和使用中應用程式內訊息託管於具有每個應用程式報表套裝 15MB 大小限制的伺服器。儘管此限制套用於使用 Adobe 託管的訊息內容和資源，但對於應用程式內訊息在其他主機或應用程式內的主機上可能會參照的資源則沒有限制。

### 我可以針對應用程式內訊息使用自有的 HTML 嗎?

是，我們支援應用程式內訊息的自訂 HTML。For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### 我可以使用哪些觸發器來傳送推送通知或應用程式內訊息?

行銷人員可以選擇任何 Analytics 資料或傳送作為顯示應用程式內訊息之觸發器的事件。應用程式內訊息會使用於裝置上本機發生的觸發器。如果選擇多個觸發器，所有觸發器必需發生在相同點擊中，訊息才會顯示。如需詳細資訊，請參閱[體驗: 應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

會使用既存的 Adobe Analytics 區段或可建立在已收集之歷史 Analytics 資料上的自訂區段來傳送推送訊息。如需詳細資訊，請參閱[體驗: 推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 我輸入的應用程式內、推播或行銷連結名稱為何發生錯誤？

您無法在使用相同上層報表套裝或 VRS 的多個應用程式中使用相同的應用程式內訊息、推送訊息或行銷連結名稱。若要解決此問題，請為應用程式內訊息、推播訊息或行銷連結輸入其他名稱。

## 位置 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 我可以擁有多少份興趣點(POI)有限制嗎？

沒有特定限制，但為求理想效能以及使用者裝置的記憶體限制之故，我們建議您建立或者上傳最多 5000 個特定地標。

## 贏取 {#section_B37F1129CD5843E890D0E54179455357}

### 我可以將行銷活動歸為應用程式內活動嗎?

是。Adobe Mobile Services 可協助您建立行銷訣竅，有助於促銷及促進您應用程式的流量，並將贏取行銷活動緊密關聯應用程式內分析和轉換。如需詳細資訊，請參閱 [贏取](/help/using/acquisition-main/acquisition-main.md).

### 如何設定連結來贏取及追蹤新的應用程式使用者?

You can create Marketing Links that route users to download applications from the Apple App Store and Google Play. 這些連結會成為創造成功下載事件的得力助手。如需詳細資訊，請參閱 [行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).