---
description: 在 Adobe Analytics，您可以在管理工具首頁管理角色。
title: 角色與權限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 42%

---

# 角色與權限{#roles-and-permissions}

在 Adobe Analytics，您可以在管理工具首頁管理角色。

## 總覽 {#section_91B8192891E14E5285718C8118912500}

下列是 Mobile Services UI 的角色管理權限:

### Analytics 管理員

Analytics管理員負責管理使用者群組並指派權限，其中一個是行動應用程式管理員。 Experience Cloud管理員會將您的Adobe ID連結至您的Adobe Analytics帳戶，讓您透過Adobe ID登入Mobile Services使用者介面。 有關Experience Cloud管理員的詳細資訊，請參閱Experience Cloud中心介面元件指南中的[管理Experience Cloud用戶和產品](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html)。

>[!TIP]
>
>現有的 Analytics 管理員能將 Analytics 管理員角色指派給任何使用者。

如需此角色的詳細資訊，請參閱Adobe Analytics檔案中的下列內容：

* [使用者管理概述](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/users.html)
* [使用者和群組權限變更](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/permissions-changes.html)

### 行動應用程式管理員

此角色為 Mobile Services UI 的管理員。

>[!IMPORTANT]
>
>推送訊息和 Analytics 管理員等部分功能必須在使用者管理中選取&#x200B;**[!UICONTROL 區段建立]**&#x200B;核取方塊。

## 管理存取權 {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是 Mobile Services UI 中部分存取選項的相關額外資訊:

### 應用程式與報表套裝

所有Mobile Service應用程式都與報表套裝相連結。 如果使用者沒有報表套裝的存取權，將無法存取該報表套裝的相關應用程式。

### Mobile Services 與 Analytics 功能

如果您的公司並沒有 Analytics 合約以存取 UI 的功能 (例如推送訊息)，無論使用者的權限級別，您公司內的所有使用者都無法存取該功能。

## 角色與權限 {#section_20AA029D5B8C413C8659777E79B11620}

下列是 Mobile Services UI 的角色以及其相關的權限:

### Analytics 管理員 權限

* 所有使用者與行動應用程式的管理員權限
* 使用新報表套裝建立應用程式
* 從Mobile Services刪除應用程式

   >[!IMPORTANT]
   >
   >雖然已在 Mobile Services 使用者介面中刪除應用程式，但 Analytics 仍會存在該報表套裝內。

* 「管理應用程式設定」

   * 啟用生命週期報告
   * 啟用位置報告
   * 建立/更新/刪除變數和量度

### 行動應用程式管理員 權限

* 所有使用者權限
* 使用現有報表套裝建立應用程式
* 「管理應用程式設定」

   * 設定應用程式的行動SDK選項
   * 配置應用的UI設定
   * 設定連結的App Store應用程式
   * 設定應用程式的通用連結選項
   * 設定推送服務憑證和API金鑰
   * 建立/更新/啟用/停用/複製/封存/刪除回傳
   * 建立/更新/封存/刪除連結目的地

* 建立/更新/封存行銷連結
* 建立/匯入/更新/刪除舊版贏取連結
* 建立/匯入/更新/刪除地標（地標）設定
* 建立/更新/傳送/排程/取消/複製/封存/刪除推送訊息
* 建立/更新/啟用/停用/複製/封存/刪除應用程式內訊息

如需群組和使用者的詳細資訊，請參閱Adobe Analytics檔案中的下列內容：

* [使用者群組設定（舊版）](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-groups/groups.html)
* [新增使用者至群組](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services 使用者

此角色具有僅限檢視的權限，且可在Mobile Services UI中提供意見反應。

* 在Mobile Services使用者介面上提供意見反應
* 檢視應用程式

   >[!IMPORTANT]
   >
   >使用者只可以在 Adobe Analytics 檢視他們具備存取權的報表套裝。

* 檢視應用程式設定

   * 下載應用程式SDK設定
   * 檢視所有UI和SDK設定
   * 檢視變數和量度設定
   * 檢視回傳
   * 檢視連結目的地

* 檢視和執行報表
* 檢視行銷連結
* 檢視及匯出舊版贏取連結
* 檢視和匯出位置（地標）設定
* 檢視推送訊息
* 檢視應用程式內訊息
