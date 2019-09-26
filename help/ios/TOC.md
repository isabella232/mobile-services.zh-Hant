---
product: mobile-services
audience: 終端使用者
user-guide-title: Mobile Services iOS Help
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
   + [快速整合](getting-started/swift-integration.md)
   + [移轉至4.x iOS程式庫](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [設定概觀](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [Override the ADBMobile JSON config path](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [Configuration methods](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Lifecycle metrics](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics總覽](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作](analytics-main/timed-actions.md)
   + [訪客存留期值](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Products variable](analytics-main/products/products.md)
      + [產品變數與銷售eVar和產品特定事件](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳 {#postbacks}
      + [Postbacks overview](analytics-main/postback/postback.md)
      + [回傳範例](analytics-main/postback/postback-example.md)
      + [PII回傳](analytics-main/postback/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 贏取 {#acquisition-ios}
   + [贏取概觀](acquisition-main/acquisition-main.md)
   + [行動應用程式贏取](acquisition-main/acquisition.md)
   + [Acquisition methods](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [追蹤協力廠商延遲的深層連結](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [測試Marketing Link贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試V3贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ 傳訊 {#messaging-ios}
   + [Messaging overview](messaging-main/messaging-main.md)
   + 應用程式內傳訊 {#in-app-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [應用程式內訊息疑難排解](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [推播訊息](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [接收豐富的推播通知](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [推播訊息疑難排解](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概觀](location/location.md)
   + [地理位置與地標](location/geo-poi.md)
   + [iBeacon 追蹤](location/ibeacon.md)
+ Target {#target-ios}
   + [Target概觀](target-main/target-main.md)
   + [Target methods](target-main/c-target-methods.md)
   + [iOS 中的預先擷取選件內容](target-main/c-mob-target-prefetch-ios.md)
   + [在 iOS 裝置上預覽目標](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud overview](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager methods](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [使用tvOS實作Apple TV](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [適用於 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS擴充功能實作](ios-ext/ios-ext.md)
   + [單機擴充實作](ios-ext/c-stand-alone-extension-implementation.md)
+ [Apple watch與WatchOS 2的實作](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK reference](reference/reference.md)
   + [應用程式 ID](reference/app-ids.md)
   + [應用程式和行動網頁之間的訪客追蹤](reference/hybrid-app.md)
   + [iOS裝置版本](reference/device-versions.md)
+ 隱私權與一般資料保護規範{#privacy-gdpr-ios}
   + [隱私權與一般資料保護規範](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [檢索儲存的標識符](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [設定使用者的選擇狀態](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 外掛程式 {#phonegap-ios}
   + [PhoneGap增效模組](phonegap/phonegap.md)
   + [PhoneGap plug-in methods](phonegap/phonegap-methods.md)
