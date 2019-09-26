---
description: 回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 Mobile Services 將自訂資料傳送至第三方目的地。
seo-description: 回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 Mobile Services 將自訂資料傳送至第三方目的地。
seo-title: 配置回傳
title: 配置回傳
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 Mobile Services 將自訂資料傳送至第三方目的地。

>[!IMPORTANT]
>
>若要使用回傳，您必須安裝4.6 SDK或更新版本。 如需詳細資訊，請參閱 [Android - 回傳](/help/android/analytics-main/postbacks/postbacks.md)或 [iOS - 回傳](/help/ios/analytics-main/postback/postback.md)。

1. 按一下所需應用程式的名稱，前往「管理應用程式設定」頁面，然後按一下右上方的&#x200B;**「管理回傳」**。
1. Click **[!UICONTROL Create Postback]**.
1. 在欄位中輸入下列資訊:

   * **[!UICONTROL 回傳類型]**

      Choose **[!UICONTROL Custom]**. 未來將會提供範本。

   * **[!UICONTROL 名稱]**

      指定回傳的描述性名稱。

   * **[!UICONTROL URL]**

      指定有效的端點URL（視需要為GET請求提供適當的查詢參數）。 您可從傳送資料的目地方 (廣告伺服器或您自己的端點) 取得此 URL。例如 `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL 內容變數]**

      反白顯示 URL 部分並從下拉式清單中選取所需的內容變數。您也可以將上下文變數插入URL，而URL會將所有範本變數取代為點擊的值。

   * **[!UICONTROL 新增貼文內文]**

      例如，可指定張貼要求上的其他張貼內容。如果您指定貼文內文，請指定貼文內文的內容類型。 例如, `application/json`.

   * **[!UICONTROL 逾時 (秒)]**

      指定要等候回傳的時間 (秒)。

   * **[!UICONTROL 觸發器]**

      指定會觸發回傳的一或多個資料標籤和條件。For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. 您也可指定啟用回傳的量度。For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL 特徵]**
   指定可以在觸發時查看訊息的使用者，Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. 按一下&#x200B;**[!UICONTROL 「儲存」]**&#x200B;建立回傳，並將其新增至&#x200B;**「管理回傳」]清單。[!UICONTROL **

   若要日後再啟用回傳，請執行下列任一項動作:

   * Select the checkbox next to the postback in the **[!UICONTROL Manage Postbacks]** list and click **[!UICONTROL Activate Selected]**.
   * 按一下「**[!UICONTROL 儲存並啟動]」，儲存變更並立即啟用回傳。**
