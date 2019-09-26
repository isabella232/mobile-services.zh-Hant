---
description: 完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。
seo-description: 完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。
seo-title: 開始之前
solution: Marketing Cloud,Analytics
title: 開始之前
topic: 開發人員和實施
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

完成下列步驟來設定報表套裝以收集 iOS 應用程式資料。

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理員和應用程式開發人員必須完成以下作業:

### Analytics 管理員

設定報表套裝並收集行動應用程式資料: 

1. 完成[登入 Adobe Mobile Services 使用者介面](/help/ios/getting-started/getting-started.md)的其中一節。
1. 為每位應用程式開發人員建立 Analytics 帳戶。

應用程式開發人員現在便擁有檢視您所建立之報表套裝的存取權。。

>[!IMPORTANT]
>
>若要建立新報表套裝並下載SDK，您必須是Analytics管理員。

### 應用程式開發人員

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

如需有關角色與權限的詳細資訊，請參閱[角色與權限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登入 Adobe Mobile Services 使用者介面 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是行動應用程式分析與目標設定的主要報告介面。完成這些步驟後，您可以下載設定檔案，其中的資料收集伺服器、報表套裝及其他許多設定均已預先設定完成。

您可以透過下列任一方式登入 Adobe Mobile Services:

* **Experience Cloud**

   以您的 Adobe ID 登入 [Experience Cloud](https://marketing.adobe.com)。

   此方法假設您的公司已布建，且您已連結您的Analytics帳戶。 如需布建的詳細資訊，請參 [閱「管理Experience cloud使用者和產品」](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。 For more information about linking your account, see Organizations and account linking.[](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)

   >[!TIP]
   >
   >If you are unsure whether your company has been provisioned in the Experience Cloud, use your existing Adobe Analytics account.

* **Adobe Analytics**

   按一下&#x200B;**[!UICONTROL 「使用 Analytics 登入」]**，然後輸入您的 Analytics 公司名稱、使用者名稱及密碼。

## 建立報表套裝 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

若要建立報表套裝，以收集應用程式資料並定義應用程式:

1. Click **[!UICONTROL Create New App]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. 輸入應用程式的名稱，然後選取唯一的報表套裝 ID。

   `mycomobileappdev` 即是報表套裝 ID 的其中一例。You need to set up separate report suites and apps for the development and production versions. When you are ready to set up the production version, repeat these steps.
1. 保留&#x200B;**[!UICONTROL 「行動應用程式範本」]為已選取狀態。**

   此範本可讓時間戳記收集離線資料，並啟用行動解決方案變數來擷取生命週期量度。

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## 下載 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

若要下載行動 SDK:

1. 登入Mobile services並以下列其中一種方式開啟您的應用程式：

   * 在&#x200B;**[!UICONTROL 「所有應用程式]下拉式清單中，選取您的應用程式。**
   * 在右側窗格中，找出並開啟您的應用程式。

1. Click **[!UICONTROL Manage App Settings]**.
1. 在&#x200B;**[!UICONTROL 「應用程式 SDK 下載」]**&#x200B;區段中，向下捲動至&#x200B;**「應用程式 SDK 下載」]區段。[!UICONTROL **

1. 下載您的平台適用的 SDK 和範例應用程式。

>[!TIP]
>
>SDK下載中會自動包含應用程式的設定檔案，因此您不需要另外下載該檔案。 然而，如果您之前已下載 SDK，並且想要取得更新的設定，則須再次下載此設定檔案。

