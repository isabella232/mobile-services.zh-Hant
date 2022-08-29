---
audience: end-user
user-guide-title: Mobile Services Android 指南
breadcrumb-title: Android指南
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 99%

---


# Mobile Services Android 指南{#android}

+ [適用於 Experience Cloud 解決方案的 Android SDK 4.x](overview.md)
+ [發行說明](rel-notes.md)
+ 快速入門{#getting-started-android}
   + [快速入門](getting-started/getting-started.md)
   + [開始之前](getting-started/requirements.md)
   + [核心實作與生命週期。](getting-started/dev-qs.md)
   + [處理規則與內容資料](getting-started/proc-rules.md)
   + [移轉至 Android 4.x 資料庫](getting-started/migration-v3.md)
+ 設定{#configuration-android}
   + [設定概述](configuration/configuration.md)
   + [ADBMobile JSON 設定檔案](configuration/json-config/json-config.md)
   + [覆寫 ADBMobile JSON 設定路徑](configuration/json-config/json-config-remote.md)
   + [點擊批次處理程序](configuration/hit-batching.md)
   + [設定方法](configuration/methods.md)
+ [生命週期量度](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics 概述](analytics-main/analytics-main.md)
   + [追蹤應用程式狀態](analytics-main/states.md)
   + [追蹤應用程式動作](analytics-main/actions.md)
   + [追蹤應用程式當機](analytics-main/crashes.md)
   + [計時動作 ](analytics-main/timed-actions.md)
   + [訪客期限值](analytics-main/lifetime-value.md)
   + Products 變數{#products-variable}
      + [Products 變數](analytics-main/products/products.md)
      + [Products 變數及其包含的銷售 eVar 與產品專屬事件](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回傳{#postbacks}
      + [回傳概述](analytics-main/postbacks/postbacks.md)
      + [回傳範例](analytics-main/postbacks/postback-example.md)
      + [PII 回傳](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analytics 方法 ](analytics-main/analytics-methods.md)
+ 贏取{#acquisition-android}
   + [贏取概述](acquisition-main/acquisition-main-android.md)
   + [行動應用程式贏取 ](acquisition-main/acquisition.md)
   + [贏取方法](acquisition-main/acquisition-methods.md)
   + 追蹤深層連結{#tracking-deep-links}
      + [追蹤深層連結](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [追蹤第三方延期的深層連結](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [測試行銷連結贏取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [測試 V3 贏取](acquisition-main/t-testing-version-3-acquisition.md)
   + [測試舊版贏取](acquisition-main/t-testing-acquisition.md)
   + [疑難排解贏取測試](acquisition-main/troubleshoot-acquisition-testing.md)
+ 傳訊{#messaging-android}
   + [傳訊概述](messaging-main/messaging-main-android.md)
   + 應用程式內傳訊{#inapp-messaging}
      + [應用程式內傳訊](messaging-main/messaging/messaging.md)
      + [應用程式內傳訊疑難排解](messaging-main/messaging/in-apps-ts.md)
   + 推送訊息{#push-messaging}
      + [推送訊息](messaging-main/push-messaging/push-messaging.md)
      + [利用深層連結實施推送訊息](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [接收豐富推送通知](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [疑難排解推送訊息](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置{#location}
   + [位置概述](location/location.md)
   + [地理位置與地標](location/geo-poi.md)
   + [信標追蹤](location/beacon.md)
+ Target{#target-android}
   + [Target 概述](target-main/target-main.md)
   + [Target 設定](target-main/target.md)
   + [Target 方法](target-main/c-target-methods.md)
   + [預先擷取 Android 中的選件內容](target-main/c-mob-target-prefetch-android.md)
   + [在 Android 裝置上預覽目標](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloud 概述](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID 設定](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service 方法](c-marketing-cloud/mc-methods.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Manager 概述](audience-manager/audience-manager.md)
   + [Audience Manager 設定](audience-manager/audiencemgmt.md)
   + [Audience Manager 方法](audience-manager/c-audience-manager-methods.md)
+ 穿戴式裝置{#wearables-android}
   + [穿戴式裝置概述](wearables/wearables.md)
   + [Android 穿戴式裝置: 快速入門](wearables/android-wearable.md)
   + [Android 穿戴式裝置: 其他附註](wearables/c-android-wearables--additional-notes.md)
+ Android SDK 參考{#sdk-reference-android}
   + [Android SDK 參考概述](/help/android/reference/reference.md)
   + [應用程式 ID](/help/android/reference/app-ids.md)
   + [應用程式和行動網站間的訪客追蹤](/help/android/reference/hybrid-app.md)
   + [Android Widget](/help/android/reference/widgets.md)
+ 隱私權與一般資料保護規範{#gdpr-privacy-android}
   + [隱私權與 GDPR 概述](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [擷取儲存的識別碼](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [設定使用者的選擇狀態](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 外掛程式{#phonegap-android}
   + [PhoneGap 外掛程式概述](phonegap/phonegap.md)
   + [PhoneGap 外掛程式方法](phonegap/phonegap-methods.md)
