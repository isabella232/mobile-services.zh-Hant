---
product: 行動服務
audience: 終端使用者
user-guide-title: Mobile Services Android說明
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android說明{#android}

+ [適用於 Experience Cloud 解決方案的 Android SDK 4.x](overview.md)
+ [發行說明](rel-notes.md)
+ 入門{#getting-started-android}
   + [入門](getting-started/getting-started.md)
   + [開始之前](getting-started/requirements.md)
   + [核心實作與生命週期](getting-started/dev-qs.md)
   + [處理規則和上下文資料](getting-started/proc-rules.md)
   + [移轉至 Android 4.x 資料庫](getting-started/migration-v3.md)
+ 設定{#configuration-android}
   + [組態概觀](configuration/configuration.md)
   + [ADBMobile JSON config檔案](configuration/json-config/json-config.md)
   + [覆寫ADBMobile JSON設定路徑](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [設定方法](configuration/methods.md)
+ [生命週期度量](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics概觀](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作](analytics-main/timed-actions.md)
   + [訪客期限值](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [產品變數](analytics-main/products/products.md)
      + [包含銷售eVar和產品特定事件的產品變數](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳{#postbacks}
      + [回傳概述](analytics-main/postbacks/postbacks.md)
      + [回傳範例](analytics-main/postbacks/postback-example.md)
      + [PII 回傳](analytics-main/postbacks/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 贏取{#acquisition-android}
   + [收購概觀](acquisition-main/acquisition-main-android.md)
   + [行動應用程式收購](acquisition-main/acquisition.md)
   + [收購方法](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [追蹤深層連結](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [追蹤第三方延遲的深層連結](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [測試行銷連結贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試V贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [疑難排解贏取測試](acquisition-main/troubleshoot-acquisition-testing.md)
+ 傳訊{#messaging-android}
   + [訊息總覽](messaging-main/messaging-main-android.md)
   + 應用程式內傳訊{#inapp-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [疑難排解應用程式內傳訊](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [推播訊息](messaging-main/push-messaging/push-messaging.md)
      + [使用深層連結實作推播訊息](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [接收豐富的推播通知](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [疑難排解推送訊息](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置{#location}
   + [位置概觀](location/location.md)
   + [地理位置和興趣點](location/geo-poi.md)
   + [信標追蹤](location/beacon.md)
+ Target{#target-android}
   + [Target總覽](target-main/target-main.md)
   + [目標設定](target-main/target.md)
   + [Target方法](target-main/c-target-methods.md)
   + [預先擷取 Android 中的選件內容](target-main/c-mob-target-prefetch-android.md)
   + [在 Android 裝置上預覽目標](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloud概觀](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID組態](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service方法](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Manager總覽](audience-manager/audience-manager.md)
   + [Audience Manager組態](audience-manager/audiencemgmt.md)
   + [Audience Manager方法](audience-manager/c-audience-manager-methods.md)
+ 穿戴式裝置{#wearables-android}
   + [穿戴式總覽](wearables/wearables.md)
   + [Android穿戴式裝置：快速入門](wearables/android-wearable.md)
   + [Android穿戴式裝置：其他附註](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK參考概觀](/help/android/reference/reference.md)
   + [應用程式 ID](/help/android/reference/app-ids.md)
   + [在應用程式和行動網頁之間追蹤訪客](/help/android/reference/hybrid-app.md)
   + [Android Widget](/help/android/reference/widgets.md)
+ 隱私權與一般資料保護規範{#gdpr-privacy-android}
   + [隱私權與GDPR總覽](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [擷取儲存的識別碼](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [設定使用者的選擇狀態](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 外掛程式{#phonegap-android}
   + [PhoneGap增效模組概觀](phonegap/phonegap.md)
   + [PhoneGap增效模組方法](phonegap/phonegap-methods.md)
