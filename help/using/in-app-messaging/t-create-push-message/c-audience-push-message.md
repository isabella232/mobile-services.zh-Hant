---
description: 您可以定義和設定推送訊息的對象選項，包含日期範圍選項、Analytics 區段和自訂區段。
keywords: 行動
seo-description: 您可以定義和設定推送訊息的對象選項，包含日期範圍選項、Analytics 區段和自訂區段。
seo-title: 對象定義並設定推送訊息的對象區段
solution: Marketing Cloud,Analytics
title: Audience  Define and Configure Audience Segments for Push Messages
topic: 量度
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# Audience: push messages{#audience-define-and-configure-audience-segments-for-push-messages}

您可以定義和設定推送訊息的對象選項，包含日期範圍選項、Analytics 區段和自訂區段。

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

建立推送訊息的對象區段後，該區段便會與一個或多個應用程式的使用者建立關聯，因為報表套裝或虛擬報表套裝可能會包含一個或多個應用程式的資料。如需虛擬報表套裝的詳細資訊，請參閱 [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

在 Adobe Mobile Services 中，行銷人員只會在個平台推送一個應用程式。如果行銷人員嘗試推送至含有來自多個應用程式的使用者的區段時，便會顯示警告訊息，通知他們繼續操作的話，可能會引致嚴重的推送失敗，也有可能會導致使用者列入黑名單。如果您遇到推送失敗，請參閱&#x200B;*解決推送失敗*，位置在: [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

若要使用區段定義中的 Audience Manager 資料，請參閱 [Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html)。

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

如果您選取的對象區段包含多個應用程式的使用者，您可能會看到下列警報：

![multiple app name](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>版本號碼是可選的。

最多會移除 6 組版本編號以及 5 組套件 ID 編號。

例如:

* `Bea[rd]cons 1.0 (123)` 將顯示為 `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` 將顯示為 `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` 將顯示為 `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` 將顯示為 `Bea[rd]cons (.6)`

若要繼續將推送訊息傳送至列出的應用程式，請選取&#x200B;**「是，我要繼續。」** check box and click **[!UICONTROL Send]**.

## 最佳作法

以下是一些值得記住的最佳實踐：

* 為了減少混淆狀況，請&#x200B;**避免**&#x200B;定義含有來自多個應用程式資料的行動應用程式虛擬報表套裝。
* **每次**&#x200B;要傳送推送訊息時，都使用唯一的應用程式 ID 做為對象區段的一部分。此舉可確保推送訊息傳送至&#x200B;**只**&#x200B;隸屬一個應用程式的對象區段。

### 範例

以下一些範例能協助您瞭解如何正確定義區段:

**正確做法**: 行銷人員會針對一個應用程式的 iOS 和 Android 版本提供推送憑證，例如 Adobe Photoshop。行銷人員可能會將推送通知傳送至橫跨兩個平台的使用者區段。

**錯誤做法**: 行銷人員會針對一個應用程式的 iOS 和 Android 版本提供推送憑證，例如 Adobe Photoshop。如果行銷人員建立推送通知，並在最近 30 天內推送至&#x200B;*所有作用中使用者的區段*，只有 Adobe Photoshop iOS 和 Android 應用程式的使用者會收到推送通知，而所有 Adobe Illustrator iOS 和 Android 應用程式的使用者都會列入黑名單。如需更多詳情，請參閱&#x200B;*解決推送訊息失敗*&#x200B;中的範例，位置在:[疑難排解推送訊息](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md)。

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. 前往「對象」頁面以取得新的推播訊息。

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * **[!UICONTROL 「預估選擇加入對象」]**&#x200B;是指符合 Adobe Analytics 區段的裝置數量&#x200B;**及**&#x200B;選擇加入的裝置數量。

      您可以檢視所選區段中，選擇收到訊息以及將會收到推送訊息的預計使用者人數。應用程式使用者的總人數會顯示在預計值下方，無論其選擇加入狀態為何。

   * **[!UICONTROL 「總計」]是指符合 Adobe Analytics 區段的裝置數量。**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      這代表 SDK 已針對「推送訊息選擇加入」的 evar 傳送 `True` 值。

   * 即使裝置有有效的裝置Token，除非Adobe Analytics已設定選擇加入標幟，否則訊息不會推送至裝置。

   * 如需疑難排解推送訊息的詳細資料，請參閱下列內容:

      * [iOS中的推送訊息](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Push messaging in Android](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. 在下列欄位輸入資訊:

   * **[!UICONTROL 期間為]**

      輸入用於預計對象的時間範圍。從&#x200B;**[!UICONTROL 「於此期間」]下拉式清單中選取一個選項:**

   * **[!UICONTROL 「最近」]**&#x200B;可讓您選取相對於排定推送訊息之時間的時間範圍 (例如最近 7 天、最近 30 天或最近 60 天)。

      舉例來說，如果您選取最近 30 天並排程在 10 月 31 日推送訊息，則預計對象會是 10 月 31 日前 30 天選擇收到推送訊息的使用者人數。

   * **[!UICONTROL 「固定範圍」]**&#x200B;可讓您挑選預計對象範圍的開始和結束日期，以選取固定範圍。

      以前一個例子為例，如果您選取開始於 10 月 1 日且結束於 10 月 15 日的時間範圍，但排程在 10 月 31 日推送訊息，則預計對象會是在您指定之固定時間範圍 (10 月 1 日到 10 月 15 日) 內選擇收到推送訊息的使用者人數。

   * **[!UICONTROL Analytics 區段]**

      從下拉式清單中選取現有的Adobe Analytics區段。 For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL 自訂區段]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. 例如，下列自訂區段會鎖定位於加州 (美國) 區域內，使用執行 iOS 之行動電話的使用者。
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
