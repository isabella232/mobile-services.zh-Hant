---
description: 您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔案、SDK 以及開發與測試工具。
keywords: 行動
seo-description: 您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔案、SDK 以及開發與測試工具。
seo-title: 新增應用程式
solution: Marketing Cloud,Analytics
title: 新增應用程式
topic: 量度
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 新增應用程式{#add-a-new-app}

您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔案、SDK 以及開發與測試工具。

這些指示說明可協助您新增並設定 Adobe Analytics 和 Adobe Audience Manager 整合。

您必須先將應用程式新增到 Adobe Mobile Services 使用者介面，才能進行設定。建立應用程式後，系統會產生正確的設定，您可將此設定提供給為該應用程式實作 Mobile SDK 的開發人員。

1. 登入 Adobe Mobile Services，然後完成下列任一項工作:

   * 按一下&#x200B;**[!UICONTROL 「新建」]以建立應用程式。**
   * To add additional apps, click Manage Apps in the left navigation menu and click **[!UICONTROL Add]**.

      For more information about signing in, see Sign in.[](/help/using/gs/gs-signin.md)

      >[!TIP]
      >
      >若要管理現有應用程式，請按一下左側導覽功能表中的「管理應用程式」，然後按一下您要修改的應用程式。 您可以在「應用程式資訊」頁面上進行變更。

1. 在下列欄位輸入資訊:

   **[!UICONTROL 報表套裝]**

   指定要在 Adobe Analytics 中收集和儲存報表資料的報表套裝。每個應用程式都會連線至一個 Analytics 報表套裝。若要將應用程式資料傳送給多個報表套裝，請為每個報表套裝新增應用程式。每個應用程式都會連線至一個 Analytics 報表套裝。若要將應用程式資料傳送給多個報表套裝，請為每個報表套裝新增應用程式。

   如果您已獲得 Adobe Mobile 中的 Analytics 管理員權限，則可在 Adobe Mobile 中建立新的報表套裝。To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL 報告套裝 ID]**

      此ID可唯一識別Adobe Analytics中的報表套裝。 貴公司的前置詞會自動新增至 ID 開頭。

   * **[!UICONTROL 複製設定自]**

      變數、事件、處理規則和其他設定在新報表套裝中的設定，與在此報表套裝中的設定完全相同。 所使用的「**複製設定來源**」報表套裝是「行動應用程式範本」，或您建立的報表套裝已啟用離線功能，在 Mobile Services 中建立的報表套裝才會啟用離線功能。

   * **[!UICONTROL 時區]**

      All reporting dates are in this time zone. 此設定會嘗試使用與您的瀏覽器所用時區相近的時區。

   * **[!UICONTROL 貨幣]**

      收入會被追蹤並報告為此類貨幣。
   >[!TIP]
   >
   >若要使用虛擬報表套裝(VRS)，請參 [閱虛擬報表套裝](/help/using/manage-apps/c-mob-vrs.md)。

   * **[!UICONTROL 圖示]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL 名稱]**

      (**Optional**) Type a descriptive name for the app. 此名稱可協助您快速找到應用程式，而有意義的名稱可協助您快速瞭解應用程式的用途和設定。

   * **[!UICONTROL 類型]**

      從下拉式清單選取類型。左側導覽功能表中顯示的可用報表，取決於您選取的應用程式類型。

      可用的類型包括:

      * **[!UICONTROL 標準實作]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL 發佈]**

         如果您是使用 Adobe Digital Publishing Suite 建置應用程式，可選取此選項。

      * **[!UICONTROL 遊戲]**

         此選項與&#x200B;**[!UICONTROL 「標準」]**&#x200B;選項類似，只是&#x200B;**「遊戲」]會將報表中所用的詞彙改成遊戲專用術語。[!UICONTROL **&#x200B;例如，使用者會變更為播放器。 系統會自動為遊戲應用程式顯示遊戲專屬的報表。
   * **[!UICONTROL 說明]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   新增應用程式後，您可以到「應用程式資訊」頁面查看有關其他選項的設定資訊。For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
