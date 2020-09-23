---
description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
keywords: mobile
seo-description: Adobe Mobile Services 的常見問題及解答，以及功能的一般說明。
seo-title: 常見問題
solution: Experience Cloud,Analytics
title: 常見問題
topic: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 54%

---


# 常問的問題 {#frequently-asked-questions}

下表包含 Adobe Mobile Services 的常見問題清單:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### 您是否經常使用SDK進行更新？

是的，我們會不斷更新，以取得功能最豐富、符合標準且安全的SDK。 我們通常每個月都會發行新版本。 這些SDK更新是直接插入的替換程式（針對4x版），可協助您輕鬆實作。 如需更新的詳細資訊，請參閱我們的 [發行說明](https://docs.adobe.com/content/help/zh-Hant/release-notes/experience-cloud/current.html)。

### 我應該使用什麼 SDK 版本?

我們目前的SDK版本為4.11版。如需詳細資訊，請參閱我們的 [發行說明](https://docs.adobe.com/content/help/zh-Hant/release-notes/experience-cloud/current.html)。

### 可以在哪裡下載 SDK?

如需下載個別行動平台的 SDK，請前往[管理應用程式設定](/help/using/c-manage-app-settings/c-manage-app-settings.md)區段。

### 如何配置 SDK?

建立新應用程式報表套裝之後，請瀏覽至「管理應用程式設定」，並在應用程式資訊頁面上設定所有必要選項。在儲存您的配置後，從「管理應用程式設定」頁面的底部下載必要的 SDK。SDK 會預先設定您已儲存的選項，可在 SDK 封裝內的 `ADBMobileConfig.json` 檔案中找到。如果您在「管理應用程式設定」頁面上變更任何 SDK 設定，請確保重新下載 SDK 檔案或更新包含必要變更的 `ADBMobileConfig.json` 檔案。

### Adobe Mobile SDK是否支援iOS的IPv6?

Adobe Mobile SDK使用標準iOS和Android網路堆疊。 針對 iOS，SDK 使用 NSURLSession (iOS 7+ 版) 及 NSURLConnection (iOS 7 或更新版本)，與 IPv6 完全相容。已建立或使用其自有網路堆疊的開發人員需要檢閱是否有其他和緩考量。以下是來自 Apple 的額外資訊:

*如果您使用高層級網路 API (例如 NSURLSession 和 CFNetwork 架構) 撰寫用戶端應用程式並依名稱連接，則不需變更應用程式的任何項目即可搭配 IPv6 地址使用。* 如需詳細資訊，請參閱[支援 IPv6 DNS64/NAT64 網路](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 什麼是生命週期度量？

生命週期量度是「現成可用」的量度，當SDK首次在您的應用程式中實作時，會自動收集這些量度。 如需詳細資訊，請參閱[生命週期量度 (Android)](/help/android/metrics.md) 和[生命週期量度 (iOS)](/help/ios/metrics.md)。

### 如何疑難排解處理規則?

如需詳細資訊，請參 [閱處理規則提示與秘訣](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)。

### 我可以將分析資料傳送至多個報表套裝嗎？

是。SDK提供傳送資料至多個Adobe Analytics報表套裝的能力。 若要使用影像要求來在多個報表套裝中擷取資料，請在 檔案內&#x200B;**[!UICONTROL 分析]**&#x200B;區段下的 **[!UICONTROL rsids 欄位中設定多個報表套裝 ID，並以逗號分隔且請勿包含空格。]**`ADBMobileConfig.json`如需詳細資訊，請參閱 [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)。

### Mobile瀏覽與啟動有何不同？

當使用者第一次開啟應用程式或在離開應用程式超過指定逾時值後返回應用程式時，SDK會測量啟動。 **[!UICONTROL 檔案中的]** lifecycleTimeout`ADBMobileConfig.json` 欄位內，一般逾時為 5 分鐘 (300 秒)。瀏覽是Adobe Analytics在伺服器端的計算，以SDK傳送的第一個和最後一個資料點擊為基礎，而不超過瀏覽逾時。 通常，報表套裝的作業逾時設定為30分鐘。 雖然造訪是來自傳統的網頁分析，但這些點擊仍能提供使用者如何進入和退出應用程式的寶貴見解。

## 傳訊 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 推播通知是否有大小或其他限制？

推播通知訊息的字元上限為140個字元。 傳送或排程通知的次數或傳送通知的頻率沒有限制。

### 您是否支援推播通知的自訂負載？

是的，我們提供可能以JSON編碼的自訂推播裝載。 Android和iOS負載分別限制為4KB和2KB。 這些負載會透過推播或本機通知傳送至應用程式。 如需詳細資訊，請參閱[體驗: 推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 應用程式內訊息是否有大小限制？

在Adobe Mobile Services中建立的已發佈和作用中應用程式內訊息會裝載在伺服器上，每個應用程式報表套裝的大小限制為15MB。 雖然此限制適用於使用Adobe代管的訊息內容和資源，但應用程式內訊息在其他主機或應用程式內可參照的資源沒有限制。

### 我是否可將自己的HTML用於應用程式內訊息？

是的，我們支援您應用程式內訊息的自訂HTML。 如需詳細資訊，請參閱[體驗: 應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

### 我可以使用哪些觸發器來傳送推播通知或應用程式內訊息？

行銷人員可選擇傳送的任何Analytics資料或事件作為觸發器，以顯示應用程式內訊息。 應用程式內訊息會使用裝置本機發生的觸發器。 如果選擇多個觸發器，所有觸發器都必須發生在相同的點擊中，才會顯示訊息。 如需詳細資訊，請參閱[體驗: 應用程式內訊息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

會使用既存的 Adobe Analytics 區段或可建立在已收集之歷史 Analytics 資料上的自訂區段來傳送推送訊息。如需詳細資訊，請參閱[體驗: 推送訊息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 為什麼我輸入的應用程式內、推送或行銷連結名稱出現錯誤?

您無法在使用相同上層報表套裝或 VRS 的多個應用程式中使用相同的應用程式內訊息、推送訊息或行銷連結名稱。若要解決此問題，請針對應用程式內訊息、推送訊息或行銷連結名稱輸入其他名稱。

## 位置 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 我可以擁有的特定地標 (POI) 是否有所限制?

沒有特定限制，但為求理想效能以及使用者裝置的記憶體限制之故，我們建議您建立或者上傳最多 5000 個特定地標。

## 贏取 {#section_B37F1129CD5843E890D0E54179455357}

### 我可以將促銷活動歸因於應用程式內活動嗎？

是。Adobe Mobile Services可協助您建立行銷技巧，以協助促銷並推動應用程式的流量，並將贏取促銷活動與應用程式內分析和轉換聯繫起來。 如需詳細資訊，請參閱[贏取](/help/using/acquisition-main/acquisition-main.md)。

### 如何設定連結來贏取及追蹤新的應用程式使用者?

您可以建立行銷連結，將使用者路由至從 Apple App Store 和 Google Play 下載應用程式。這些連結會成為創造成功下載事件的得力助手。如需詳細資訊，請參閱[行銷連結建立器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。