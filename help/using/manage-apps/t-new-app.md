---
description: 您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔案、SDK 以及開發與測試工具。
keywords: 行動
seo-description: 您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔案、SDK 以及開發與測試工具。
seo-title: 新增應用程式
solution: Experience Cloud,Analytics
title: 新增應用程式
topic-fix: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
exl-id: 30dca517-61ac-495b-aa91-3febd1cb8639
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 100%

---

# 新增應用程式{#add-a-new-app}

您可以利用此資訊建立新應用程式和設定其關鍵量度；設定 Adobe Analytics 和 Adobe Audience Manager 的 SDK 選項；設定贏取和 ID 服務選項；以及下載設定檔、SDK 以及開發與測試工具。

這些指示說明可協助您新增並設定 Adobe Analytics 和 Adobe Audience Manager 整合。

您必須先將應用程式新增到 Adobe Mobile Services 使用者介面，才能進行設定。建立應用程式後，系統會產生正確的設定，您可將此設定提供給為該應用程式實作 Mobile SDK 的開發人員。

1. 登入 Adobe Mobile Services，然後完成下列任一操作：

   * 按一下&#x200B;**[!UICONTROL 「新建」]**&#x200B;以建立應用程式。
   * 若要新增其他應用程式，請按一下左側導覽選單中的「管理應用程式」，然後按一下&#x200B;**[!UICONTROL 「新增」]**。

      如需登入的詳細資訊，請參閱[登入](/help/using/gs/gs-signin.md)。

      >[!TIP]
      >
      >若要管理現有應用程式，請按一下左側導覽選單中的「管理應用程式」，然後再按一下您要修改的應用程式。您可以在「應用程式資訊」頁面上進行變更。

1. 在下列欄位輸入資訊：

   **[!UICONTROL 報表套裝]**

   指定要在 Adobe Analytics 中收集和儲存報表資料的報表套裝。每個應用程式都會連線至一個 Analytics 報表套裝。若要將應用程式資料傳送給多個報表套裝，請為每個報表套裝新增應用程式。每個應用程式都會連線至一個 Analytics 報表套裝。若要將應用程式資料傳送給多個報表套裝，請為每個報表套裝新增應用程式。

   如果您已獲得 Adobe Mobile 中的 Analytics 管理員權限，則可在 Adobe Mobile 中建立新的報表套裝。若要建立新的報表套裝，請選取&#x200B;**[!UICONTROL 「新增報表套裝」]**，然後填寫下列欄位：

   * **[!UICONTROL 報告套裝 ID]**

      此 ID 可唯一識別 Adobe Analytics 中的報表套裝。貴公司的前置詞會自動新增至 ID 開頭。

   * **[!UICONTROL 複製設定來源]**

      在新報表套裝中設定的變數、事件、處理規則和其他設定與此報表套裝中的完全相同。所使用的&#x200B;**[!UICONTROL 「複製設定來源」]**&#x200B;報表套裝是「行動應用程式範本」，或您建立的報表套裝已啟用離線功能，在 Mobile Services 中建立的報表套裝才會啟用離線功能。

   * **[!UICONTROL 時區]**

      所有報表日期皆為此時區時間。此設定會嘗試使用與您的瀏覽器所用時區相近的時區。

   * **[!UICONTROL 貨幣]**

      會使用這種貨幣來追蹤和報告收入。
   >[!TIP]
   >
   >若要使用虛擬報表套裝 (VRS)，請參閱[虛擬報表套裝](/help/using/manage-apps/c-mob-vrs.md)。

   * **[!UICONTROL 圖示]**

      (**選用**) 若要瀏覽並選取應用程式的圖示，請按一下&#x200B;**[!UICONTROL 圖示]**。

   * **[!UICONTROL 名稱]**

      (**選用**) 為應用程式輸入描述性名稱。此名稱可協助您快速找到應用程式，而有意義的名稱有助於迅速了解應用程式的用途和設定。

   * **[!UICONTROL 類型]**

      從下拉式清單中選取類型。左側導覽功能表顯示的可用報表，會視您選取的應用程式類型而異。

      可用的類型包括：

      * **[!UICONTROL 標準]**

         您可以讓大部分應用程式都保留選取&#x200B;**[!UICONTROL 「標準」]**&#x200B;選項。

      * **[!UICONTROL 發佈]**

         如果您是使用 Adobe Digital Publishing Suite 建置應用程式，可選取此選項。

      * **[!UICONTROL 遊戲]**

         此選項與&#x200B;**[!UICONTROL 「標準」]**&#x200B;選項類似，只是&#x200B;**[!UICONTROL 「遊戲」]**&#x200B;會將報表中所用的詞彙改成遊戲專用術語，例如將使用者變更為玩家。系統會自動為遊戲應用程式顯示遊戲專屬的報表。
   * **[!UICONTROL 說明]**

      (**選用**) 為應用程式輸入說明。



1. 按一下&#x200B;**[!UICONTROL 「儲存」]**，新增應用程式。

   新增應用程式後，您可以到「應用程式資訊」頁面查看有關其他選項的設定資訊。如需詳細資訊，請參閱[管理應用程式設定](/help/using/c-manage-app-settings/c-manage-app-settings.md)。
