---
description: 您可以建立和管理地標，藉此定義地理位置，以便用於關聯、使用應用程式內訊息定位等等。從「地標」傳送點擊時，地標就會附加至該點擊。
keywords: 行動
seo-description: 您可以建立和管理地標，藉此定義地理位置，以便用於關聯、使用應用程式內訊息定位等等。從「地標」傳送點擊時，地標就會附加至該點擊。
seo-title: 管理地標
solution: Marketing Cloud、Analytics
title: 管理地標
topic: 量度
uuid: 7b362534-54fb-43a3-b6 b2-dfc8 f45 ff7 c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

您可以建立和管理POI，這可讓您定義地理位置，以便用於關聯、使用應用程式內訊息定位等等。在POI中傳送點擊時，POI會附加至點擊。

在使用「位置」之前，請先確認下列需求：

* 您必須擁有 Analytics—Mobile Apps 或 Analytics Premium。
* 您必須啟用此應用程式的&#x200B;**[!UICONTROL 位置報表]。**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. 在「管理地標」頁面上，當您按一下 **[!UICONTROL 「儲存」]**&#x200B;時，變更會封裝為 **[!UICONTROL 「地標]** 」清單，而即時應用程式的組態檔案則會更新。只要應用程式使用更新的SDK和配置，並搭配遠端POI URL，儲存也會更新應用程式中應用程式中的點清單。

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

若要使用位置，請完成下列任務：

1. 按一下應用程式的名稱，前往其「管理應用程式設定」頁面。
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![步驟結果](assets/poi.png)

1. 輸入下列每個欄位中的資訊：

   * **[!UICONTROL 地標名稱]**

      輸入&#x200B;**[!UICONTROL 位置地標]名稱。**

      這可以是城市、國家或地區的名稱。您也可以在特定位置附近建立&#x200B;**[!UICONTROL 地標]，例如體育館或企業。**

   * **[!UICONTROL 緯度]**

      Type the latitude of the **[!UICONTROL Point of Location]**. 您可從其他來源找到這項資訊，包括網際網路。

   * **[!UICONTROL 經度]**

      Type the longitude of the **[!UICONTROL Point of Location]**. 您可從其他來源找到這項資訊，包括網際網路。

   * **[!UICONTROL 半徑 (公尺)]**

      輸入&#x200B;**[!UICONTROL 地標]涵蓋的半徑 (公尺)。**&#x200B;例如，如果您為科羅拉多州丹佛(Denver)、科羅拉多市(Colorado)建立POI，可以指定足夠大的半徑來加入丹佛(Denver)和周邊區域，但排除Colorado Springs。

   * **[!UICONTROL 地圖圖示]**

      選取將顯示在 [「概述](/help/using/location/c-location-overview.md) 」和 [「地圖」](/help/using/location/c-map-points.md) 報表上的圖示。

1. 視需要新增其他POI。

   建議您新增不超過5,000個POI。如果新增的地標超過 5,000 個，地標仍可儲存，但會收到警告訊息提醒您最佳實務作法是低於 5,000 個地標。

1. 按一下&#x200B;**[!UICONTROL 儲存]**。

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
