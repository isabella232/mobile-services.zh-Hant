---
description: 此資訊可協助您進行推送訊息疑難排解。
keywords: 行動
solution: Experience Cloud,Analytics
title: 疑難排解推送訊息
topic-fix: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
exl-id: dda84d30-2a7b-496c-b8f3-3bd6b97076aa
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 100%

---

# 疑難排解推送訊息 {#troubleshooting-push-messaging}

此資訊可協助您進行推送訊息疑難排解。

## 為什麼有時候推送訊息的傳送會延遲?

下列延遲類型可能與 Mobile Services 的推送訊息有關:

* **等候 Analytics 點擊**

   每個報表套裝都可設定處理傳入 Analytics 點擊的時機。預設為 1 小時。實際處理 Analytics 點擊最多可能需要 30 分鐘，但通常為 15 至 20 分鐘。

   例如，報表套裝每小時會處理點擊一次。當您將處理時間最長 30 分鐘納入考量，傳入的點擊最久可能需要 90 分鐘才能供推播訊息使用。如果使用者在早上 9:01 啟動應用程式，則點擊會在早上 10:15 到 10:30 之間，於 Mobile Services 使用者介面中顯示為新的唯一使用者。

* **等候推送服務**

   推播服務 (APNS 或 GCM) 可能不會立即送出訊息。雖然此情形不常見，但曾發生過 5 至 10 分鐘延遲的現象。在「訊息」頁面中，您可按一下訊息的「檢視」連結，以確認推送訊息已傳送至推送服務。在報表中，成功傳送至推送服務的數量會列在「已發佈」欄。

   >[!TIP]
   >
   >推送服務無法保證訊息一定會傳送出去。如需服務的可靠性詳細資訊，請參閱適當文件。
   >
   >* **APNS**：[服務品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [訊息的生命週期](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## 我要如何更新 Apple 推播服務憑證？

傳送推播訊息需有效的推播服務憑證。Mobile Services 會在憑證接近到期或到期時通知您。如果您收到此通知，請完成下列步驟以更新憑證:

1. 按一下&#x200B;**[!UICONTROL 管理應用程式設定]**。
2. 若要刪除目前的憑證，請捲動至&#x200B;**[!UICONTROL 推送服務]**&#x200B;並按一下&#x200B;**[!UICONTROL 刪除]**。
3. 設定並測試新憑證。

   如需詳細資訊，請參閱[啟用推播訊息的必要條件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. 按一下&#x200B;**[!UICONTROL 「儲存」]**。

## 為什麼無法在 iOS 模擬器中看到我的推播訊息？

iOS 模擬器不支援推播訊息。
