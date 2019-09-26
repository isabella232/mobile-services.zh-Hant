---
description: 此資訊可協助您進行推送訊息疑難排解。
keywords: 行動
seo-description: 此資訊可協助您進行推送訊息疑難排解。
seo-title: 疑難排解推播訊息
solution: Marketing Cloud,Analytics
title: 疑難排解推播訊息
topic: 量度
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# 疑難排解推播訊息 {#troubleshooting-push-messaging}

此資訊可協助您進行推送訊息疑難排解。

## 為什麼有時候推送訊息的傳送會延遲?

下列延遲類型可能與 Mobile Services 的推送訊息有關:

* 等候 Analytics 點擊

   每個報表套裝都可設定處理傳入 Analytics 點擊的時機。預設為 1 小時。實際處理 Analytics 點擊最多可能需要 30 分鐘，但通常為 15 至 20 分鐘。例如，某個報表套裝每小時處理一次點擊。如果您將最大處理時間計為 30 分鐘，則某個傳入的點擊可能需要 90 分鐘才可供推送訊息使用。如果使用者在早上 9:01 啟動應用程式，則點擊會在早上 10:15 到 10:30 之間，於 Mobile Services 使用者介面中顯示為新的唯一使用者。

* 等候推送服務

   推播服務（APNS或FCM）可能不會立即傳送訊息。 雖然此情形不常見，但曾發生過 5 至 10 分鐘延遲的現象。在「訊息」頁面中，您可按一下訊息的&#x200B;**「檢視」**&#x200B;連結，以確認推送訊息已傳送至推送服務。在報表中，成功傳送至推送服務的數量會列在&#x200B;**[!UICONTROL 「已發佈」]欄。**

   >[!TIP]
   >
   >推播服務不保證會傳送訊息。

   如需服務的可靠性詳細資訊，請參閱適當文件。

   * **APNS**: [服務品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**:訊 [息的期限](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## 為何我的推送訊息截斷或無法展開?

對於某些 Android 裝置，顯示訊息時，您可能需要使用 `NotificationCompat.BigTextStyle`。
