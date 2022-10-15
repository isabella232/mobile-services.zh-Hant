---
description: 回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 Mobile Services 將自訂資料傳送至第三方目的地。
title: 設定回傳
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
exl-id: 99b27f16-303a-4853-bfdb-2066a53867bf
source-git-commit: dbe3af75010fbf5195a3f93fc43cb696aaa32b65
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# 設定回傳 {#configure-postbacks}

回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用相同的觸發器和您使用的特性來顯示應用程式內訊息，您便可以設定 Mobile Services 將自訂資料傳送至第三方目的地。

>[!IMPORTANT]
>
>若要使用回傳功能，您必須安裝 4.6 版或更新版本的 SDK。

1. 按一下所需應用程式的名稱，前往「管理應用程式設定」頁面，然後按一下右上方的&#x200B;****「管理回傳」。
2. 按一下&#x200B;**[!UICONTROL 建立回傳]**。
3. 在欄位中輸入下列資訊：

   * **[!UICONTROL 回傳類型]**

      選擇&#x200B;**[!UICONTROL 自訂]**。未來將會提供範本。

   * **[!UICONTROL 名稱]**

      指定回傳的描述性名稱。

   * **[!UICONTROL URL]**

      指定有效的端點 URL (包含 GET 要求需要的合適查詢參數)。您可從傳送資料的目地方 (廣告伺服器或您自己的端點) 取得此 URL。例如 `https://example.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL 內容變數]**

      反白顯示 URL 部分並從下拉式清單中選取所需的內容變數。您也可以將上下文變數插入 URL 中，而 URL 會將所有範本變數取代為點擊的值。

   * **[!UICONTROL 新增貼文內文]**

      例如，可指定張貼要求上的其他張貼內容。如果您指定張貼內容文字，請指定張貼內容的內容類型。例如, `application/json`.

   * **[!UICONTROL 逾時 (秒)]**

      指定要等候回傳的時間 (秒)。

   * **[!UICONTROL 觸發器]**

      指定會觸發回傳的一或多個資料標籤和條件。例如，您可選擇&#x200B;**[!UICONTROL 當機]**&#x200B;作為觸發器，選擇&#x200B;**[!UICONTROL 存在]**&#x200B;作為條件，應用程式當機時即會觸發回傳。您也可指定啟用回傳的量度。例如，您可選擇&#x200B;**[!UICONTROL 裝置名稱]**&#x200B;作為觸發器，選擇&#x200B;**[!UICONTROL 等於]**&#x200B;和 **[!UICONTROL iPhone 6 Plus]** 作為條件，應用程式在 iPhone 6 Plus 裝置上當機時即會啟用回傳。

   * **[!UICONTROL 特徵]**
   指定可以在觸發時查看訊息的使用者，選項包括&#x200B;**[!UICONTROL 工作階段長度]**、**[!UICONTROL 首次啟動日期]**&#x200B;和&#x200B;**[!UICONTROL 應用程式 ID]**。

4. 按一下&#x200B;**[!UICONTROL 「儲存」]**&#x200B;建立回傳，並將其新增至&#x200B;**[!UICONTROL 「管理回傳」]**&#x200B;清單。

   若要日後再啟用回傳，請執行下列任一項動作：

   * 在&#x200B;**[!UICONTROL 管理回傳]**&#x200B;清單中，選取回傳旁邊的核取方塊，然後按一下&#x200B;**[!UICONTROL 啟用選取的項目]**。
   * 按一下「**[!UICONTROL 儲存並啟動]**」，儲存變更並立即啟用回傳。
