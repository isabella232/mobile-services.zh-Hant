---
description: '設定報表套裝並收集 Android 應用程式資料之前，請完成以下必備作業 '
solution: Experience Cloud Services,Analytics
title: 開始之前
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 96%

---

# 開始之前 {#before-you-start}

設定報表套裝並收集 Android 應用程式資料之前，請完成以下必備作業：

## 角色特定作業 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理員和應用程式開發人員必須完成以下作業：

### Analytics 管理員

設定報表套裝並收集行動應用程式資料：

1. 完成[登入 Adobe Mobile Services UI](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) 任一節的指示。
1. 為每位應用程式開發人員建立 Analytics 帳戶。

應用程式開發人員現在擁有檢視您所建立之報表套裝的存取權。

>[!IMPORTANT]
>
>若要建立新報表套裝和下載 SDK，您必須是 Analytics 管理員。

### 應用程式開發人員

1. 確保您的 Analytics 管理員已完成&#x200B;*角色特定作業*&#x200B;中 [Analytics 管理員](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)一節所述的步驟。
1. 確認您的 Analytics 管理員已完成[登入 Adobe Mobile Services 使用者介面](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)的其中一節。
1. 報表套裝設定完成後，請完成[下載 SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46) 中的步驟。

如需角色和權限的詳細資訊，請參閱[角色和權限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登入 Adobe Mobile Services UI {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是行動應用程式分析和鎖定的主要報表介面。完成上述步驟後，您就可以下載已預先設定資料收集伺服器、報表套裝和其他諸多設定的設定檔。

您可以透過下列其中一種方式登入 Adobe Mobile Services 使用者介面：

### Experience Cloud

以您的 Adobe ID 登入 [Experience Cloud](https://experiencecloud.adobe.com)。這個方法假定 Experience Cloud 中已供應您的公司，且您已連結您的 Analytics 帳戶。有關詳細資訊，請參見 [管理Experience Cloud用戶和產品](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=zh-Hant) 中的「Experience Cloud中心介面元件」。

>[!TIP]
>
>如果您不確定貴公司是否已佈建在 Experience Cloud 中，請使用現有的 Adobe Analytics 帳戶。

### Adobe Analytics

按一下&#x200B;**[!UICONTROL 「使用 Analytics 登入」]**，然後輸入您的 Analytics 公司名稱、使用者名稱及密碼。

## 建立報表套裝 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

若要建立報表套裝，以收集應用程式資料並定義應用程式：

1. 登錄到 [AdobeMobile](https://mobilemarketing.adobe.com)。
1. 按一下&#x200B;**[!UICONTROL 建立應用程式]**。

   如果沒有看見此按鈕，請按一下&#x200B;**[!UICONTROL 「管理應用程式]** > **[!UICONTROL 新增」]**。

1. 在&#x200B;**[!UICONTROL 報表套裝]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL 新的報表套裝]**。

1. 輸入應用程式的名稱，然後選取報表套裝類型。

   `mycomobileappdev` 即是報表套裝 ID 的其中一例。您必須分別設定開發版本和生產版本的報表套裝與應用程式，如此一來，當您準備好設定生產版本時，便可重複這些步驟。
1. 在&#x200B;**[!UICONTROL 報表套裝 ID]** 中確認會顯示報表套裝名稱。
1. 在&#x200B;**[!UICONTROL 「複製設定來源」]**&#x200B;中確認已選取&#x200B;**[!UICONTROL 「行動應用程式範本」。]**

   此範本可讓時間戳記收集離線資料，並啟用行動解決方案變數來擷取生命週期量度。

1. 選取您的時區與貨幣，然後按一下&#x200B;**[!UICONTROL 儲存]**。

## 下載 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

若要下載行動 SDK：

1. 在瀏覽器中輸入 [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/)，登入 Mobile Services 使用者介面。
1. 在左窗格中，按一下&#x200B;**[!UICONTROL 「所有應用程式」]**&#x200B;下拉式清單，然後選取您的應用程式。您也可以從右窗格中選取您的應用程式。

   >[!IMPORTANT]
   >
   >若要在右窗格中查找應用程式，請先建立應用程式。如需建立應用程式的詳細資訊，請參閱[新增應用程式](/help/using/manage-apps/t-new-app.md)。

1. 進入您的應用程式後，在左窗格中按一下&#x200B;**[!UICONTROL 「管理應用程式設定」]**。

   >[!IMPORTANT]
   >
   >若畫面未顯示&#x200B;**[!UICONTROL 「管理應用程式設定」]**&#x200B;選項，請確認您是否已登入Adobe Mobile Services。若要確認，請按一下頁面右上方的![解決方案切換器](assets/solution-switcher.png)圖示，並確認左上方是否顯示 **[!UICONTROL Adobe Mobile Services]**。

1. 在「管理應用程式設定」頁面底部的&#x200B;**[!UICONTROL 「應用程式 SDK 下載」]**&#x200B;區段中，下載適用於您平台的 SDK 和範例應用程式。

>[!TIP]
>
>應用程式的設定檔會自動包含在 SDK 下載中，因此您無須另外下載此檔案。然而，如果您之前已下載 SDK，並且想要取得更新的設定，則須再次下載此設定檔。

如果您正使用 Android Studio，您也可以將以下項目新增至您應用程式的 `build.gradle` 檔：

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

請記住以下資訊：

* 以適用的 Android SDK 版本取代程式碼範例中的版本編號。
* 下載設定檔，並將其加入您的專案。
