---
audience: end-user
user-guide-title: Mobile Services iOS 指南
breadcrumb-title: iOS指南
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 99%

---


# Mobile Services iOS 指南 {#ios}

+ [適用於 Experience Cloud 解決方案的 iOS SDK 4.x](overview.md)
+ [發行說明](rel-notes.md)
+ 入門 {#getting-started-ios}
   + [快速入門概述](getting-started/getting-started.md)
   + [開始之前](getting-started/requirements.md)
   + [核心實施與生命週期](getting-started/dev-qs.md)
   + [處理規則與內容資料](getting-started/proc-rules.md)
   + [Swift 整合](getting-started/swift-integration.md)
   + [移轉至 4.x iOS 資料庫](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [設定概述](configuration/configuration.md)
   + [ADBMobile JSON 設定](configuration/json-config/json-config.md)
   + [覆寫 ADBMobile JSON 設定路徑](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [設定方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [生命週期量度](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics 概述](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作](analytics-main/timed-actions.md)
   + [訪客期限值](analytics-main/lifetime-value.md)
   + Products 變數 {#products-variable}
      + [Products 變數](analytics-main/products/products.md)
      + [Products 變數及其包含的銷售 eVar 與產品專屬事件](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳 {#postbacks}
      + [回傳概述](analytics-main/postback/postback.md)
      + [回傳範例](analytics-main/postback/postback-example.md)
      + [PII 回傳](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics 方法](analytics-main/analytics-methods.md)
+ 贏取 {#acquisition-ios}
   + [贏取概述](acquisition-main/acquisition-main.md)
   + [行動應用程式贏取](acquisition-main/acquisition.md)
   + [贏取方法](acquisition-main/c-acquisition-methods.md)
   + 追蹤深層連結 {#tracking-deep-links}
      + [追蹤深層連結](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [追蹤第三方延期的深層連結](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [測試行銷連結贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試 V3 贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ 傳訊 {#messaging-ios}
   + [傳訊概述](messaging-main/messaging-main.md)
   + 應用程式內傳訊 {#in-app-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [應用程式內傳訊疑難排解](messaging-main/messaging/in-apps-ts.md)
   + 推送訊息 {#push-messaging}
      + [推送訊息](messaging-main/push-messaging/push-messaging.md)
      + [利用深層連結實施推送訊息](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [接收豐富推送通知](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [疑難排解推送訊息](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概述](location/location.md)
   + [地理位置與地標](location/geo-poi.md)
   + [iBeacon 追蹤](location/ibeacon.md)
+ Target {#target-ios}
   + [Target 概述](target-main/target-main.md)
   + [Target 方法](target-main/c-target-methods.md)
   + [iOS 中的預先擷取選件內容](target-main/c-mob-target-prefetch-ios.md)
   + [在 iOS 裝置上預覽目標](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud 概述](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service 方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager 方法](amm/aam-methods.md)
+ 使用 tvOS 實施 Apple TV {#apple-tv-implementation-tvos-ios}
   + [使用 tvOS 實施 Apple TV](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [適用於 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS 延伸功能實施 {#ios-ext}
   + [iOS 延伸功能實施](ios-ext/ios-ext.md)
   + [獨立擴充功能實施](ios-ext/c-stand-alone-extension-implementation.md)
+ [使用 WatchOS 2 進行 Apple Watch 實施](apple-watch-implementation-watchkit.md)
+ iOS SDK 參考 {#sdk-reference-ios}
   + [iOS SDK 參考](reference/reference.md)
   + [應用程式 ID](reference/app-ids.md)
   + [應用程式和行動網站間的訪客追蹤](reference/hybrid-app.md)
   + [iOS 裝置版本](reference/device-versions.md)
+ 隱私權與一般資料保護規範{#privacy-gdpr-ios}
   + [隱私權與一般資料保護規範](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [擷取儲存的識別碼](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [設定使用者的選擇狀態](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 外掛程式 {#phonegap-ios}
   + [PhoneGap 外掛程式](phonegap/phonegap.md)
   + [PhoneGap 外掛程式方法](phonegap/phonegap-methods.md)
