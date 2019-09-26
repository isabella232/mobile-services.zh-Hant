---
product: mobile-services
audience: 終端使用者
user-guide-title: Mobile Services android說明
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android Help{#android}

+ [適用於 Experience Cloud 解決方案的 Android SDK 4.x](overview.md)
+ [發行說明](rel-notes.md)
+ 入門{#getting-started-android}
   + [入門](getting-started/getting-started.md)
   + [開始之前](getting-started/requirements.md)
   + [Core implementation and lifecycle](getting-started/dev-qs.md)
   + [處理規則和上下文資料](getting-started/proc-rules.md)
   + [移轉至 Android 4.x 資料庫](getting-started/migration-v3.md)
+ 設定{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config file](configuration/json-config/json-config.md)
   + [覆寫ADBMobile JSON設定路徑](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [配置方法](configuration/methods.md)
+ [生命週期度量](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作](analytics-main/timed-actions.md)
   + [訪客存留期值](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [Products variable](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳{#postbacks}
      + [Postbacks overview](analytics-main/postbacks/postbacks.md)
      + [回傳範例](analytics-main/postbacks/postback-example.md)
      + [PII 回傳](analytics-main/postbacks/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 贏取{#acquisition-android}
   + [Acquisition overview](acquisition-main/acquisition-main-android.md)
   + [Mobile app acquisition](acquisition-main/acquisition.md)
   + [Acquisition methods](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [追蹤深層連結](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracking third-party deferred deep links](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [測試Marketing Link贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試V3贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [Troubleshoot Acquisition testing](acquisition-main/troubleshoot-acquisition-testing.md)
+ 傳訊{#messaging-android}
   + [訊息總覽](messaging-main/messaging-main-android.md)
   + 應用程式內傳訊{#inapp-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [Troubleshoot in-app messaging](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [推播訊息](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [接收豐富的推播通知](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Troubleshoot push messaging](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置{#location}
   + [位置概觀](location/location.md)
   + [地理位置與地標](location/geo-poi.md)
   + [信標追蹤](location/beacon.md)
+ Target{#target-android}
   + [Target概觀](target-main/target-main.md)
   + [Target configuration](target-main/target.md)
   + [Target methods](target-main/c-target-methods.md)
   + [預先擷取 Android 中的選件內容](target-main/c-mob-target-prefetch-android.md)
   + [在 Android 裝置上預覽目標](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience cloud概觀](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID設定](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service方法](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience manager概觀](audience-manager/audience-manager.md)
   + [Audience manager設定](audience-manager/audiencemgmt.md)
   + [Audience manager方法](audience-manager/c-audience-manager-methods.md)
+ 穿戴式裝置{#wearables-android}
   + [可穿戴裝置概觀](wearables/wearables.md)
   + [Android Wearables: getting started](wearables/android-wearable.md)
   + [Android可穿戴裝置：附註](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK參考概觀](/help/android/reference/reference.md)
   + [應用程式 ID](/help/android/reference/app-ids.md)
   + [應用程式和行動網頁之間的訪客追蹤](/help/android/reference/hybrid-app.md)
   + [Android Widget](/help/android/reference/widgets.md)
+ 隱私權與一般資料保護規範{#gdpr-privacy-android}
   + [隱私權與GDPR概觀](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [檢索儲存的標識符](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Setting the user's opt status](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 外掛程式{#phonegap-android}
   + [PhoneGap外掛程式總覽](phonegap/phonegap.md)
   + [PhoneGap plug-in methods](phonegap/phonegap-methods.md)
