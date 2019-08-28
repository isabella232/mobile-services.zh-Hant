---
description: 在 Adobe Analytics，您可以在管理工具首頁管理角色。
seo-description: 在 Adobe Analytics，您可以在管理工具首頁管理角色。
seo-title: 角色與權限
title: 角色與權限
uuid: ad350f8d-ef51-4519-98aa-3025bc0 f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

在 Adobe Analytics，您可以在管理工具首頁管理角色。

## 概述 {#section_91B8192891E14E5285718C8118912500}

下列是 Mobile Services UI 的角色管理權限:

### Analytics 管理員

Analytics 管理員負責管理使用者群組 (其中一位是行動應用程式管理員) 和指派權限: Experience Cloud 管理員會將您的 Adobe ID 連結至您的 Adobe Analytics 帳戶，讓您可以透過您的 Adobe ID 登入 Mobile Services UI。如需關於 Experience Cloud 管理員的詳細資訊，請參閱[管理 - 使用者管理與常見問題](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!TIP]
>
>現有的Analytics管理員可以將Analytics管理員角色指派給任何使用者。

如需關於此角色的詳細資訊，請參閱下列內容:

* [使用者管理概觀](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [使用者和群組權限變更](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### 行動應用程式管理員

此角色為 Mobile Services UI 的管理員。

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是 Mobile Services UI 中部分存取選項的相關額外資訊:

### 應用程式與報表套裝

所有 Mobile Service 應用程式均與報表套裝相關聯。如果使用者沒有某報表套裝的存取權，則無法存取與該報表套裝相關的應用程式。

### Mobile Services與Analytics功能

如果您的公司並沒有 Analytics 合約以存取 UI 的功能 (例如推送訊息)，無論使用者的權限級別，您公司內的所有使用者都無法存取該功能。

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

下列是 Mobile Services UI 的角色以及其相關的權限:

### Analytics 管理員

* 所有使用者和行動應用程式管理員權限
* 以新的報表套裝建立應用程式
* 從 Mobile Services 刪除應用程式

   >[!IMPORTANT]
   >
   >雖然已在Mobile Services UI中刪除應用程式，但報表套裝仍存在於Analytics中。

* 「管理應用程式設定」

   * 啟用生命週期報表
   * 啟用定位報表
   * 建立/更新/刪除變數與量度

### 行動應用程式管理員

* 所有使用者的權限
* 以現有的報表套裝建立應用程式
* 「管理應用程式設定」

   * 設定應用程式的 Mobile SDK 選項
   * 設定應用程式的 UI 設定
   * 設定已連結的應用程式商店應用程式
   * 設定應用程式的通用連結選項
   * 設定推送服務認證及 API 密鑰
   * 建立/更新/啟動/停用/複製/封存/刪除回傳
   * 建立/更新/封存/刪除連結目的地

* 建立/更新/封存行銷連結
* 建立/匯入/更新/刪除舊版贏取連結
* 建立/匯入/更新/刪除地點 (地標) 設定
* 建立/更新/傳送/排程/取消/複製/封存/刪除推送訊息
* 建立/更新/啟動/停用/複製/封存/刪除應用程式內訊息

如需關於群組和使用者的詳細資訊，請參閱:

* [使用者群組設定](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [新增使用者至群組](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services使用者

此角色具備只可檢視的權限，並可在 Mobile Services UI 提供意見反應。

* 在 Mobile Services UI 提供意見反應
* 檢視應用程式

   >[!IMPORTANT]
   >
   >使用者只能看到他們在Adobe Analytics中存取的報表套裝。

* 檢視應用程式設定

   * 下載應用程式 SDK 配置
   * 檢視所有 UI 及 SDK 配置
   * 檢視變數與量度配置
   * 檢視回傳
   * 檢視連結目的地

* 檢視和執行報表
* 檢視行銷連結
* 檢視及匯出舊版贏取連結
* 檢視及匯出地點 (地標) 配置
* 檢視推送訊息
* 檢視應用程式內訊息
