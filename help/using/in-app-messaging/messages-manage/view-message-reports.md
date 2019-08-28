---
description: 您可以檢視應用程式內和推送訊息的訊息報表。
keywords: 行動
seo-description: 您可以檢視應用程式內和推送訊息的訊息報表。
seo-title: 檢視訊息報表
solution: Marketing Cloud、Analytics
title: 檢視訊息報表
topic: 量度
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

您可以檢視應用程式內和推送訊息的訊息報表。

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   如需建立嚴格篩選的詳細資訊，請參閱 [新增嚴格篩選](/help/using/usage/reports-customize/t-sticky-filter.md)。

>[!TIP]
>
>視您檢視的訊息類型而定，報表可能會有所不同。

## In-app messages {#section_90B79BA58E8141F78538C187EB1BF8C7}

如果您檢視的是應用程式內訊息的報表，報表外觀會類似於下圖:

![報表訊息](assets/report_message.png)

### 應用程式內訊息量度

以下是應用程式內訊息可用的度量清單：

* **[!UICONTROL 曝光(在]**&#x200B;觸發訊息時)。

* **[!UICONTROL 當使用者]**&#x200B;按下警報或全螢幕訊息 **[!UICONTROL 上的「點進」]** 按鈕，以及使用者從本機通知開啓應用程式時，按一下即可。

* **[!UICONTROL 取消]**，當使用者按下警報上的 **[!UICONTROL 「取消」]** 按鈕或全螢幕訊息時。

* **[!UICONTROL 參與比率]**&#x200B;是Adobe Analytics的計算度量，是點進次數除以印象數目的結果。

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

如果您檢視的是推送訊息的報表，報表外觀會類似於下圖:

![推送訊息](assets/report_message_push.png)

頂端圖表顯示開啟訊息的使用者人數。

### 推送訊息量度

以下是推送訊息可用的度量清單：

* **[!UICONTROL 時間]**

   從 Mobile Services 推送訊息至裝置的時間。

* **[!UICONTROL 狀態]**

   訊息狀態，可用狀態為：

   * **[!UICONTROL 已取消]**
   * **[!UICONTROL 已排程]**
   * **[!UICONTROL 執行中]**
   * **[!UICONTROL 已執行]**

* **[!UICONTROL 已發佈]**

   裝置Token成功傳送到Apple推送通知服務/Firebase Cloud Messaging(APNS/FCM)，以便傳送訊息給使用者裝置。

* **[!UICONTROL 顯示]**

   裝置Token的數目未成功傳送至APNS/FCM。失敗的一些可能原因：

   * pushID 無效

   * 指定要推送的推送平台(APNS、FCM等等)不適用於工作的應用程式。例如，平台可能會收集 iOS 推送代碼，但並未配置 APNS 服務。

   * 訊息可能因為推送服務未正確設定或 Mobile Services 系統故障而傳送失敗。
   >[!IMPORTANT]
   >
   >如果您遇到異常大量的失敗，請檢查推送服務配置。如果推送服務的配置看起來正確，請聯絡 Adobe 客戶服務。

* **[!UICONTROL 列入黑名單]**

   不再有效傳送至APNS或FCM的裝置Token數目。這通常表示裝置已解除安裝應用程式，或使用者變更其接收訊息的選擇加入設定。Android 和 iOS 不同之處在於代號列入黑名單的時間。Android 代號會立即顯示在列入黑名單計數中。iOS 代號最初會顯示為已發佈，但會根據來自 APNS 的回饋在後續訊息中顯示為列入黑名單。
