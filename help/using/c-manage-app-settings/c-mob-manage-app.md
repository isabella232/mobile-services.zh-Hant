---
description: 您可以透過設定各種變數和量度以追蹤及管理從應用程式接收的資料。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 管理您的應用程式
topic-fix: Metrics
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
exl-id: 599fef94-c188-47f5-b9d6-25a7c8cb07bc
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 92%

---

# 管理您的應用程式 {#managing-your-app}

{#eol}

您可以透過設定各種變數和量度以追蹤及管理從應用程式接收的資料。

## 管理變數和量度 {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **「標準變數與量度」**

   每個應用程式都包含用於追蹤購物車和購物活動的變數和量度。部分購物資訊無法由處理規則來處理，因此 SDK 會公開特殊的 `"&&products"` 上下文資料。例如，您可以有購物車新增次數、購物車移除次數、結帳次數、訂單數量等變數。內容資料必須對應至 Adobe Analytics 中的資料。如果以簡單的內容資料映射填入此變數，則這是映射至它的關鍵值。如果要依 Analytics 管理工具中更複雜的規則來填入變數，請保留空白。

* **自訂變數**

   「自訂變數」頁面會顯示為報表套裝 (此套裝包含您的應用程式資料) 設定的所有自訂 Analytics 變數。您可以在此頁面上啟用其他變數，並將內容資料映射至 Analytics 變數。

### 映射上下文資料至 Analytics 變數

按一下&#x200B;**[!UICONTROL 「管理應用程式設定]** > **[!UICONTROL 管理變數和量度]** > **[!UICONTROL 自訂變數」]**。

這些對應會呼叫與 [處理規則](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) 在Adobe Analytics中使用。

![上下文資料對應](assets/custom_data_content.png)

以下是您可以設定的自訂變數清單:

* **[!UICONTROL 自訂屬性]** (或 Prop) 可回答「哪一個?」問題。Prop 可設為文字值，會與相同點擊中傳送的其他變數和量度相關聯。這些值可用於篩選報表，或可依相關量度以排名順序列出。

   為追蹤呼叫 (或點擊) 中的屬性設定值時，該值僅適用於該呼叫。

* 此 **[!UICONTROL 自訂變數]** （或eVar）也可回答「哪一個？」問題。 不過，eVar值不僅可套用至傳入的點擊，也可套用至後續點擊中傳送的變數和量度，直到值過期或設定新值為止。
* **[!UICONTROL 自訂清單變數 (或是多重值變數)]** 除了可允許您在單一點擊上擷取多個值外，其他行為與變數相同。如需詳細資訊，請參閱 [清單](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/list.html?lang=zh-Hant) 變數。

當下列對應在 Mobile Services 中建立，就會顯示在 Analytics 中。

* **[!UICONTROL 名稱]**

   資料收集變數的好記名稱。

* **[!UICONTROL 內容資料]**

   如果以簡單的內容資料映射填入此變數，則這是映射至它的關鍵值。如果要依 Analytics 管理工具中更複雜的規則來填入變數，請將此欄位保留空白。

   按一下內容資料欄，然後選取您要對應的內容資料變數。下拉式清單包含過去 30 天內收到的變數，因此如果您要對應的內容資料不在清單中，您可以加以輸入。

* **[!UICONTROL 永續性 (自訂變數和自訂清單變數)]**

   永續性決定自訂變數 (eVar) 值到期或是不再與額外點擊關聯的時間點。如果點擊發生時，eVar 已到期，則沒有任何值會與該 eVar 點擊相關聯。這表示點擊觸發時沒有作用中的 eVar 值。

   您可以選取下列任一選項：

   * **[!UICONTROL Session]**

      eVar 值會在 Analytics 造訪期間持續存在。

   * **[!UICONTROL 追蹤呼叫]**

      eVar 值只會在追蹤呼叫，或是在其包含的點擊中持續存在。

   * **[!UICONTROL 永不過期]**

      eVar 值會在所有隨後的追蹤乎叫中持續存在。
   * **[!UICONTROL 進階]**

      Adobe Analytics 針對設定 eVars 永續性提供更進階的 UI。如果針對不受 Mobile Services 支援的 eVar 設定了永續性值，此值會顯示在 Mobile Services UI 中。

      若要管理 eVar，請按一下&#x200B;**[!UICONTROL 「Adobe Analytics 報表套裝管理]** > **[!UICONTROL 轉換變數 UI」]**。

   * **[!UICONTROL 清單支援]**

      啟用傳遞多重值以與一個追蹤呼叫的內容相關聯。分隔字元必須為一個字元，且不可以是零或空格。

   * **[!UICONTROL 分隔字元]**

      分隔字元必須為一個字元，且不可以是零或空格。

### 其他 Analytics 變數

您可以使用每個變數區段底部的下拉式清單，來啟用其他變數。

![新增變數](assets/add_variable.png)

選取未使用的變數編號，並輸入名稱。您可選擇提供要儲存的內容資料變數和任何其他資訊。

* **自訂量度**

   量度 (或事件) 可回答以下問題: *多少?*&#x200B;或&#x200B;*數量多少?*。事件數量可能會在使用者每次採取動作或保留數值 (例如價格) 時增加。自訂量度包括建立應用程式、下載或匯出 PDF 或 CSV 檔案、儲存行銷活動、下載 SDK、執行報表、新增 App Store 連結、啟用應用程式內訊息等事件。

   選取下列其中一個自訂量度類型:

   * **[!UICONTROL 整數]**
   * **[!UICONTROL 小數位數]**
   * **[!UICONTROL 貨幣]**

## 管理地標 {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

地標可讓您定義地理位置，以便用於關聯、使用應用程式內訊息定位等等。在地標傳送點擊時，地標就會附加至該點擊。如需地標的詳細資訊，請參閱[管理地標](/help/using/location/t-manage-points.md)。

## 管理連結目的地 {#section_F722A387E22A430187B063D358A87711}

您可以建立、編輯、封存/取消封存及刪除連結目的地。然後便可在建立行銷連結、推送通知或應用程式內訊息時內嵌呼叫這些目的地。如需連結目的地的詳細資訊，請參閱[管理連結目的地](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md)。

## 管理回傳 {#section_78B0A8D7AE6940E78D85AE3AB829E860}

回傳可讓您將 Adobe Mobile 所收集的資料傳送至個別的第三方伺服器。運用您用來顯示應用程式內訊息的相同觸發器和特性，便可以設定 Mobile 將自訂資料傳送至第三方目的地。如需回傳的詳細資訊，請參閱[設定回傳](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md)。
