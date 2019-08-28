---
description: 以下資訊可協助您在 Android 裝置上往返舊版贏取促銷活動連結。
keywords: Android；資料庫；行動；sdk
seo-description: 以下資訊可協助您在 Android 裝置上往返舊版贏取促銷活動連結。
seo-title: 測試舊版贏取
solution: Marketing Cloud、Analytics
title: 測試舊版贏取
topic: 開發人員和實施
uuid: bb7ace96-68eb-4f43-b3 cf-af80730 b9
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

以下資訊可協助您在 Android 裝置上往返舊版贏取促銷活動連結。

如果行動應用程式尚未在 Google Play 上架，您可以選擇任一行動應用程式，作為建立促銷活動連結時的目的地。這只會影響贏取伺服器將您重新導向的應用程式 (在您點擊贏取連結後)，而不會影響測試贏取連結的能力。查詢字串參數會傳遞至 Google Play 商店，然後在安裝時傳遞至應用程式，作為促銷活動廣播的一部分。往返行動應用程式贏取測試需要模擬此廣播類型。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. 這樣即可確保應用程式首次啟動時，與促銷活動查詢字串參數關聯的初始生命週期量度可以順利傳送。

1. 在 Mobile Services 使用者介面中，產生舊版贏取促銷活動 URL。

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. 將裝置與電腦連接，然後啟動 ADB 殼層，再啟動裝置上的應用程式。
1. 使用下列格式傳送廣播:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. 完成下列步驟:
   1. 將 `com.example.adobetesttapp.com` 替換為應用程式的反向 DNS 項目。
   1. 將接收器參考更新為應用程式中促銷活動追蹤接收器位置的參考。
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

若廣播成功，系統會顯示類似下方的回應:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

您也會看到一則傳送至 Adobe 資料收集伺服器的影像要求。若 SDK 等候了完整的反向連結逾時期間 (即您在步驟 1 中的設定)，且影像要求並未包含促銷活動參數，則此廣播失敗。
