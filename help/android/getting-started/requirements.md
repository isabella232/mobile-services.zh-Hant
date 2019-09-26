---
description: '設定報表套裝並收集 Android 應用程式資料之前，請完成以下必備作業 '
seo-description: '設定報表套裝並收集 Android 應用程式資料之前，請完成以下必備作業 '
seo-title: 開始之前
solution: Marketing Cloud,Analytics
title: 開始之前
topic: 開發人員和實施
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Before you start {#before-you-start}

設定報表套裝並收集 Android 應用程式資料之前，請完成以下必備作業:

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理員和應用程式開發人員必須完成以下作業:

### Analytics 管理員

設定報表套裝並收集行動應用程式資料: 

1. 完成[登入 Adobe Mobile Services 使用者介面](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)的其中一節。
1. 為每位應用程式開發人員建立 Analytics 帳戶。

應用程式開發人員現在便擁有檢視您所建立之報表套裝的存取權。。

>[!IMPORTANT]
>
>若要建立新報表套裝並下載SDK，您必須是Analytics管理員。

### 應用程式開發人員

1. 確保您的 Analytics 管理員完成[角色特定作業](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)的 *Analytics 管理員*&#x200B;一節中的步驟。

1. 確認您的 Analytics 管理員完成[登入 Adobe Mobile Services 使用者介面](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)的其中一節。
1. 報表套裝設定完成後，請完成[下載 SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46) 中的步驟。

如需有關角色與權限的詳細資訊，請參閱[角色與權限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登入 Adobe Mobile Services 使用者介面 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是行動應用程式分析與目標設定的主要報告介面。完成這些步驟後，您可以下載設定檔案，其中的資料收集伺服器、報表套裝及其他許多設定均已預先設定完成。

您可以透過下列其中一種方式登入 Adobe Mobile Services 使用者介面:

### Experience Cloud

以您的 Adobe ID 登入 [Experience Cloud](https://marketing.adobe.com)。這個方法假定 Experience Cloud 中已供應您的公司，且您已連結您的 Analytics 帳戶。For more information, see Manage Experience Cloud users and products.[](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)

>[!TIP]
>
>If you are unsure whether your company has been provisioned in the Experience Cloud, use your existing Adobe Analytics account.

### Adobe Analytics

按一下&#x200B;**[!UICONTROL 「使用 Analytics 登入」]**，然後輸入您的 Analytics 公司名稱、使用者名稱及密碼。

## 建立報表套裝 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

若要建立報表套裝，以收集應用程式資料並定義應用程式:

1. Click **[!UICONTROL Create New App]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. 輸入應用程式的名稱，然後選取報表套裝類型。

   `mycomobileappdev` 即是報表套裝 ID 的其中一例。您必須分別設定開發版本和生產版本的報表套裝與應用程式，如此一來，當您準備好設定生產版本時，便可重複這些步驟。
1. In **[!UICONTROL Report Suite ID]**, verify that your report suite name is displayed.
1. 在&#x200B;**[!UICONTROL 「複製設定來源」]**&#x200B;中確認已選取&#x200B;**「行動應用程式範本」[!UICONTROL 。]**

   此範本可讓時間戳記收集離線資料，並啟用行動解決方案變數來擷取生命週期量度。

1. Select your time zone, your currency, and click **[!UICONTROL Save]**.

## 下載 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

若要下載行動 SDK:

1. 登入 Mobile Services 使用者介面，並以下列其中一種方式開啟您的應用程式:

   * 在&#x200B;**[!UICONTROL 「所有應用程式]下拉式清單中，選取您的應用程式。**
   * 在右側窗格中，找出並開啟您的應用程式。

1. Click **[!UICONTROL Manage App Settings]**.
1. 向下捲動至&#x200B;**[!UICONTROL 「應用程式 SDK 下載」]區段。**
1. 下載您的平台適用的 SDK 和範例應用程式。

>[!TIP]
>
>A config file for your app is automatically included in the SDK download, so you do not need to download that file separately. 然而，如果您之前已下載 SDK，並且想要取得更新的設定，則須再次下載此設定檔案。

如果您正使用 Android Studio，您也可以將以下項目新增至您應用程式的 `build.gradle` 檔:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

請記住以下資訊:

* 將程式碼範例中的版本編號替換為適當的 Android SDK 版本。
* 下載設定檔案並將其包含在您的專案中。