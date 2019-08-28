---
product: 行動服務
audience: 終端使用者
user-guide-title: Mobile Services iOS說明
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS說明 {#ios}

+ [適用於 Experience Cloud 解決方案的 iOS SDK 4.x](overview.md)
+ [發行說明](rel-notes.md)
+ 入門 {#getting-started-ios}
   + [快速入門概觀](getting-started/getting-started.md)
   + [開始之前](getting-started/requirements.md)
   + [核心實作與生命週期](getting-started/dev-qs.md)
   + [處理規則和上下文資料](getting-started/proc-rules.md)
   + [Swift整合](getting-started/swift-integration.md)
   + [移轉至4.x iOS程式庫](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [組態概觀](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [覆寫ADBMobile JSON設定路徑](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [設定方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [生命週期度量](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics概觀](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作](analytics-main/timed-actions.md)
   + [訪客期限值](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [產品變數](analytics-main/products/products.md)
      + [包含銷售eVar和產品特定事件的產品變數](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳 {#postbacks}
      + [回傳概述](analytics-main/postback/postback.md)
      + [回傳範例](analytics-main/postback/postback-example.md)
      + [PII回傳](analytics-main/postback/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 贏取 {#acquisition-ios}
   + [收購概觀](acquisition-main/acquisition-main.md)
   + [行動應用程式收購](acquisition-main/acquisition.md)
   + [收購方法](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [追蹤深層連結](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [追蹤第三方延遲的深層連結](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [測試行銷連結贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試V贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ 傳訊 {#messaging-ios}
   + [訊息總覽](messaging-main/messaging-main.md)
   + 應用程式內傳訊 {#in-app-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [應用程式內傳訊疑難排解](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [推播訊息](messaging-main/push-messaging/push-messaging.md)
      + [使用深層連結實作推播訊息](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [接收豐富的推播通知](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [疑難排解推送訊息](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概觀](location/location.md)
   + [地理位置和興趣點](location/geo-poi.md)
   + [iBeacon 追蹤](location/ibeacon.md)
+ Target {#target-ios}
   + [Target總覽](target-main/target-main.md)
   + [Target方法](target-main/c-target-methods.md)
   + [iOS 中的預先擷取選件內容](target-main/c-mob-target-prefetch-ios.md)
   + [在 iOS 裝置上預覽目標](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud概觀](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager方法](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [使用TvOS實施Apple TV](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [適用於 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS擴充功能實作](ios-ext/ios-ext.md)
   + [獨立的擴充功能實作](ios-ext/c-stand-alone-extension-implementation.md)
+ [使用WatchOS進行Apple Watch實施](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK參考](reference/reference.md)
   + [應用程式 ID](reference/app-ids.md)
   + [在應用程式和行動網頁之間追蹤訪客](reference/hybrid-app.md)
   + [iOS裝置版本](reference/device-versions.md)
+ 隱私權與一般資料保護規範{#privacy-gdpr-ios}
   + [隱私權與一般資料保護規範](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [擷取儲存的識別碼](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [設定使用者的選擇狀態](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 外掛程式 {#phonegap-ios}
   + [PhoneGap增效模組](phonegap/phonegap.md)
   + [PhoneGap增效模組方法](phonegap/phonegap-methods.md)
