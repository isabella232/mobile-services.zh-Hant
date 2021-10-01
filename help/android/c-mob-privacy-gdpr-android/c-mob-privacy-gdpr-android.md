---
description: Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。
title: 隱私權與通用資料保護規則概述
uuid: 56d6f155-efec-4b3f-a972-a63155729167
exl-id: 57696f2e-87f4-4f72-bec2-80c7192576f9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 76%

---

# 隱私權與通用資料保護規則概述 {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

>[!IMPORTANT]
>
>**只有** Mobile SDK 4.16.0 或更新版本才支援 GDPR。

當Adobe向企業提供軟體和服務時，Adobe會作為資料處理者，處理和儲存任何個人資料，作為提供這些服務的一部分。 身為資料處理者，Adobe會根據貴公司的權限和指示(例如，依照您與Adobe的合約規定)處理個人資料。

身為資料控管單位，您可以使用AdobeMobile Services SDK來支援GDPR從行動應用程式擷取和刪除請求。

對於行動應用程式的 Adobe Mobile SDK 部分，您可以使用下列設定和方法:

* 如要擷取來自 SDK 的資料，並將此資料傳送至您的伺服器，請使用 `getAllIdentifiersAsync` 方法。

   如需詳細資訊，請參閱[擷取儲存的識別碼](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)。

* 如要設定您的選擇狀態並協助處理 GDPR 資料刪除請求，請使用以下的設定:

   * `privacyDefault`
   * `setPrivacyStatus`
   如需詳細資訊，請參閱[設定使用者的選擇狀態](/help/android/c-mob-privacy-gdpr-android/privacy.md)。
