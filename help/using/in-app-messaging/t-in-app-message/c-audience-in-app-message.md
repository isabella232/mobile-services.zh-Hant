---
description: 您可以設定應用程式內訊息的對象選項，包含檢視、觸發器和特徵選項。
keywords: 行動
seo-description: 您可以設定應用程式內訊息的對象選項，包含檢視、觸發器和特徵選項。
seo-title: Audience  In-App Message
solution: Marketing Cloud,Analytics
title: Audience  In-App Message
topic: 量度
uuid: 6c815d4c-7626-4cf4-9158-3f059c79317a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

您可以設定應用程式內訊息的對象選項，包含檢視、觸發器和特徵選項。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 在對象頁面的下列欄位輸入資訊:

   * **[!UICONTROL 檢視]**

      選取觸發訊息顯示的選項:

      * **[!UICONTROL 一直]**

         此選項表示訊息會在每次觸發時顯示。

      * **[!UICONTROL 一次]**

         此選項表示訊息只會在第一次觸發時顯示。

      * **[!UICONTROL 直至點進訊息]**

         此選項表示訊息會在每次觸發時顯示，直至使用者點進訊息為止。此觸發器只適用於全螢幕和警告訊息。大多數的訊息需要重新導向或使用來自網際網路的資源，因此離線時無法顯示。若要無論網絡連線一律顯示訊息，請選取&#x200B;**[!UICONTROL 「離線顯示」]核取方塊。**
   * **[!UICONTROL 觸發]**

      從下拉式清單中選取選項，然後選取條件。例如，您可從第一個下拉式清單中選取「**[!UICONTROL 已啟動]**」，然後從第二個下拉式清單中選取「**存在[!UICONTROL 」。]**&#x200B;您也可以指定自訂內容資料，觸發點擊中必須包含該資料才會顯示訊息。

      >[!IMPORTANT]
      >
      >If you select multiple triggers, for the message to display, all triggers must occur on the same hit.

   * **[!UICONTROL 特]**&#x200B;徵：您可以決定在觸發應用程式內訊息時，應該看到該訊息的對象，並篩選（分段）具有指定資料的點擊對象。 例如，您可以定義一個規則，其中的地標包含丹佛。此篩選器能讓您對在觸發時間位於地標名稱包含丹佛的客戶顯示訊息。



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>觸發器和特徵會使用從應用程式傳遞至Analytics的資料。 這些值會以內容資料、已對應之變數和量度等形式傳遞。變數是以文字為主的值，量度則是數值。

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL 「標準變數與量度」]**
* **[!UICONTROL 自訂變數]**
* **[!UICONTROL 自訂量度]**

驗證對應後，請選取適當的符合項目或邏輯運算子，藉此設定訊息的對象。

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![觸發選項](assets/custom_trigger_matcher_options.png)

The following scenarios help you determine whether to select a metric or a variable as your trigger:

### 量度

量度是數值，購買次數即是一例。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. 在&#x200B;****「對象」]標籤的&#x200B;**[!UICONTROL 「觸發器」]區段完成以下步驟:[!UICONTROL **

   1. Select a standard event such as **[!UICONTROL Launched]** and select **[!UICONTROL exists]**.
   1. 選取已對應到量度的自訂資料點來當做第二個觸發器。
   1. Under **[!UICONTROL Number]**, select a matcher option.

### 變數

變數是作為唯一識別碼的文字字串，範例包括國家、機場等。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. 在&#x200B;****「對象」]標籤的&#x200B;**[!UICONTROL 「觸發器」]區段完成以下步驟:[!UICONTROL **

   1. Select a standard event such as **[!UICONTROL Launched]** and select **[!UICONTROL exists]**.
   1. 選取已對應到變數的自訂資料點來當做第二個觸發器。
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
