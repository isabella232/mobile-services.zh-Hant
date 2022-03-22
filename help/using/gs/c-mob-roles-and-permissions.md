---
description: 在 Adobe Analytics，您可以在管理工具首頁管理角色。
title: 角色與權限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 46%

---

# 角色與權限{#roles-and-permissions}

在 Adobe Analytics，您可以在管理工具首頁管理角色。

## 總覽 {#section_91B8192891E14E5285718C8118912500}

下列是 Mobile Services UI 的角色管理權限:

### Analytics 管理員

An Analytics Admin manages user groups and assigns permissions, one of which is the Mobile App Admin. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=zh-Hant)

>[!TIP]
>
>現有的 Analytics 管理員能將 Analytics 管理員角色指派給任何使用者。

### 行動應用程式管理員

此角色為 Mobile Services UI 的管理員。

>[!IMPORTANT]
>
>推送訊息和 Analytics 管理員等部分功能必須在使用者管理中選取&#x200B;**[!UICONTROL 區段建立]**&#x200B;核取方塊。

## 管理存取權 {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是 Mobile Services UI 中部分存取選項的相關額外資訊:

### 應用程式與報表套裝

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Mobile Services 與 Analytics 功能

如果您的公司並沒有 Analytics 合約以存取 UI 的功能 (例如推送訊息)，無論使用者的權限級別，您公司內的所有使用者都無法存取該功能。

## 角色與權限 {#section_20AA029D5B8C413C8659777E79B11620}

下列是 Mobile Services UI 的角色以及其相關的權限:

### Analytics 管理員 permissions

* 所有使用者與行動應用程式的管理員權限
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >雖然已在 Mobile Services 使用者介面中刪除應用程式，但 Analytics 仍會存在該報表套裝內。

* 「管理應用程式設定」

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### 行動應用程式管理員 permissions

* All User Permissions
* Create App with existing report suite
* 「管理應用程式設定」

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=zh-Hant)
* [新增使用者至群組](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services 使用者

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >使用者只可以在 Adobe Analytics 檢視他們具備存取權的報表套裝。

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* 檢視和執行報表
* 檢視行銷連結
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
