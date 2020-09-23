---
description: 完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。
seo-description: 完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。
seo-title: 開始之前
solution: Experience Cloud,Analytics
title: 開始之前
topic: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 93%

---


# 開始之前 {#before-you-start}

完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。

## 角色特定作業 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理員和應用程式開發人員必須完成以下作業：

### Analytics 管理員

設定報表套裝並收集行動應用程式資料：

1. 完成[登入 Adobe Mobile Services UI](/help/ios/getting-started/getting-started.md) 任一節的指示。
1. 為每位應用程式開發人員建立 Analytics 帳戶。

應用程式開發人員現在擁有檢視您所建立之報表套裝的存取權。

>[!IMPORTANT]
>
>若要建立新報表套裝和下載 SDK，您必須是 Analytics 管理員。

### 應用程式開發人員

1. 確保您的 Analytics 管理員完成以上 *Analytics 管理員*&#x200B;一節中的步驟。

1. 確認您的 Analytics 管理員完成以下&#x200B;*登入 Adobe Mobile Services 使用者介面*&#x200B;的其中一節。
1. 報表套裝設定完成後，請完成以下&#x200B;*下載 SDK* 一節中的步驟。

如需角色和權限的詳細資訊，請參閱[角色和權限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登入 Adobe Mobile Services UI {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是行動應用程式分析和鎖定的主要報表介面。完成這些步驟後，您可以下載已預先設定資料收集伺服器、報表套裝和許多其他設定的設定檔。

您可以透過下列其中一種方式登入Adobe Mobile Services:

* **Experience Cloud**

   以您的 Adobe ID 登入 [Experience Cloud](https://marketing.adobe.com)。

   這個方法假定已佈建您的公司，且您已連結您的 Analytics 帳戶。如需佈建的詳細資訊，請參閱[管理 Experience Cloud 使用者和產品](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/manage-users-and-products/admin-getting-started.html)。如需連結帳戶的詳細資訊，請參閱[組織和帳戶連結](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/manage-users-and-products/organizations.html)。

   >[!TIP]
   >
   >如果您不確定貴公司是否已佈建在 Experience Cloud 中，請使用現有的 Adobe Analytics 帳戶。

* **Adobe Analytics**

   按一下&#x200B;**[!UICONTROL 「使用 Analytics 登入」]**，然後輸入您的 Analytics 公司名稱、使用者名稱及密碼。

## 建立報表套裝 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

若要建立報表套裝，以收集應用程式資料並定義應用程式：

1. 按一下&#x200B;**[!UICONTROL 建立新應用程式]**。

   如果沒有看見此按鈕，請按一下&#x200B;**[!UICONTROL 「管理應用程式]** > **[!UICONTROL 新增」]**。

1. 在&#x200B;**[!UICONTROL 報表套裝]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 新的報表套裝]**。

1. 輸入應用程式的名稱，然後選取唯一的報表套裝 ID。

   `mycomobileappdev` 即是報表套裝 ID 的其中一例。您必須分別設定開發版本和生產版本的報表套裝與應用程式。當您準備好設定生產版本，請重複這些步驟。
1. 保留&#x200B;**[!UICONTROL 「行動應用程式範本」]**&#x200B;為已選取狀態。

   此範本可讓時間戳記收集離線資料，並啟用行動解決方案變數來擷取生命週期量度。

1. 選取您的&#x200B;**[!UICONTROL 時區]**&#x200B;與&#x200B;**[!UICONTROL 貨幣]**，然後按一下&#x200B;**[!UICONTROL 儲存]**。

## 下載 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

若要下載行動 SDK:

1. 登入 Mobile Services，並以下列其中一種方式開啟您的應用程式:

   * 在&#x200B;**[!UICONTROL 「所有應用程式]**&#x200B;下拉式清單中，選取您的應用程式。
   * 在右側窗格中，找出並開啟您的應用程式。

1. 按一下&#x200B;**[!UICONTROL 管理應用程式設定]**。
1. 在&#x200B;**[!UICONTROL 「應用程式 SDK 下載」]**&#x200B;區段中，向下捲動至&#x200B;**[!UICONTROL 「應用程式 SDK 下載」]**&#x200B;區段。

1. 下載您的平台適用的 SDK 和範例應用程式。

>[!TIP]
>
>應用程式的設定檔案會自動包含在 SDK 下載中，因此您無須另外下載此檔案。然而，如果您之前已下載 SDK，並且想要取得更新的設定，則須再次下載此設定檔案。

