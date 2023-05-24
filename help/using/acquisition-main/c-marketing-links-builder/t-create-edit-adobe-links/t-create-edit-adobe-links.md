---
description: 您可以建立或編輯行銷連結，以提供您行動應用程式或網站的深層連結。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 建立或編輯行銷連結
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 98%

---

# 建立或編輯行銷連結{#create-or-edit-marketing-links}

{#eol}

您可以建立或編輯行銷連結，以提供您行動應用程式或網站的深層連結。如需詳細資訊，請參閱 [Apple 通用連結和 Android 應用程式連結](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. 在應用程式的左側導覽面板中，展開&#x200B;**[!UICONTROL 贏取]**，然後按一下&#x200B;**[!UICONTROL 行銷連結建立器]**。
1. 請完成以下任一操作：

   * 如需建立新的行銷連結，請按一下&#x200B;**[!UICONTROL 新建]**。
   * 如需編輯現有連結，請在&#x200B;**[!UICONTROL 「標題」]**&#x200B;欄中按一下連結的名稱。

1. 在下列欄位輸入資訊：

   * **[!UICONTROL 行銷連結名稱]**:

      (**必填)**) 為行銷連結指定描述性名稱。名稱僅顯示在 Adobe Mobile Services UI 中的行銷連結頁面上。描述性名稱可協助您或組織中的其他人員快速找到特定連結，並可提供其目的的洞察。

   * **[!UICONTROL 唯一追蹤代碼]**:

      (**必填**) 指定想要的追蹤代碼，或按一下 ![產生圖示](assets/icon_generate.png) 建立新追蹤代碼。您可以檢視詳細說明追蹤代碼使用的報告。

   * **[!UICONTROL 新增追蹤內容資料]**:

      (**選擇性**) 按一下&#x200B;**[!UICONTROL 「+」]**&#x200B;圖示，然後輸入相關資訊，以使用內容資料追蹤行銷活動。在&#x200B;**[!UICONTROL 「自訂內容資料」]**&#x200B;下拉式清單中，選取預設標籤或您自己的標籤。上下文資料用於部署行銷連結時進行報告。

      下列預設集標記可供使用:

      * **自訂上下文資料**
指定索引鍵和值。如果您新增自訂內容資料，必須建立處理規則。如需詳細資訊，請參閱 [處理規則概觀](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) (位於Adobe Analytics檔案中)。

      * **來源**
指定原始反向連結，例如「電子報」或「首頁」。

      * **媒體**
指定行銷媒體，例如「橫幅」或「電子郵件」。

      * **內容**
指定連結相關廣告的名稱或 ID。

      * **詞語**
指定廣告的付費詞語或其他搜尋詞。
1. 按一下&#x200B;**[!UICONTROL 「儲存」]**。
1. 在下列欄位輸入資訊：

   * **(必填)** 在&#x200B;**[!UICONTROL 後援 URL]** 中，指定當目的地不相符時 (例如，使用者正在使用桌面或其他不符合目的地規則的平台)，要將使用者導向至哪個 URL。
   * 在&#x200B;**[!UICONTROL 行銷連結選項]**&#x200B;中選取&#x200B;**[!UICONTROL 插入式連結]**&#x200B;或&#x200B;**[!UICONTROL 通用連結和應用程式連結]**。

      如需詳細資訊，請參閱[插入式連結](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)或 [Apple 通用連結和 Android 應用程式連結](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

   * **(條件式)** 如果選取了&#x200B;**[!UICONTROL 通用連結或應用程式連結]**，則使用者可透過&#x200B;**[!UICONTROL 自訂路徑]**，在具有查詢參數的網域後面定義 URL 路徑。如需詳細資訊，請參閱 [Apple 通用連結和 Android 應用程式連結](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. 按一下&#x200B;**[!UICONTROL 編輯插入式深層連結]**&#x200B;並設定連結。

   (**選擇性**) 如果有多個目的地，系統會根據使用者是否已安裝行動應用程式決定路由目的地。如果已安裝應用程式，則會顯示插入式登陸頁面。

   如需詳細資訊，請參閱[插入式頁面](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)。

1. 依序按一下&#x200B;**[!UICONTROL 儲存]**&#x200B;和&#x200B;**[!UICONTROL 下一步]**。
1. 在「目的地」頁面中設定連結。

   1. 按一下&#x200B;**[!UICONTROL 決策]**&#x200B;圖示 (![決策圖示](assets/icon_decision.png)) 並選取以下其中一個決策位置:

      * **[!UICONTROL 新增決策]**
      * **[!UICONTROL 新增路徑]**
   1. 如果您選取了&#x200B;**[!UICONTROL 新增決策]**，接著請選取以下其中一個決策類型:

      * **[!UICONTROL 作業系統決策]**

         支援的作業系統包括 iOS、Android、AMX 等等

      * **[!UICONTROL 裝置類型]**

         裝置類型包括桌上型電腦、電子閱讀器、遊戲主機、行動電話、數位機上盒等等
   1. 按一下&#x200B;**[!UICONTROL 目的地]**&#x200B;圖示 (![方形圖示](assets/icon_square.png)) 並選取以下其中一個目的地類型:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL 網頁連結]**
      * **[!UICONTROL 應用程式深層連結]**
      * **[!UICONTROL 混合式連結]**

      >[!TIP]
      >
      >如果使用具有應用程式商店連結的&#x200B;**[!UICONTROL 網頁連結]**&#x200B;目的地類型，將無法追蹤贏取。若要追蹤贏取，請使用&#x200B;**[!UICONTROL 「應用程式商店」]**&#x200B;目的地類型。

      如需詳細資訊，請參閱[建立新的連結目的地](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)。




1. 若要儲存行銷連結，請按一下![省略符號](assets/icon_elipses.png)，然後按&#x200B;**[!UICONTROL 儲存]**。
