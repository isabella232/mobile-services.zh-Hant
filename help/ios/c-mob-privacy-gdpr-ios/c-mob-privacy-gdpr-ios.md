---
description: Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。
seo-description: Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。
seo-title: 隱私權與一般資料保護規範
title: 隱私權與一般資料保護規範
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 74%

---


# 隱私權與一般資料保護規範 {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。

>[!IMPORTANT]
>
>**只有** Mobile SDK 4.16.0 或更新版本才支援 GDPR。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

當Adobe為企業提供軟體和服務時，Adobe會當成資料處理者，處理和儲存任何個人資料，做為提供這些服務的一部分。 身為資料處理者，Adobe會根據您公司的許可和指示（例如，如您與Adobe的合約所載）處理個人資料。

身為資料掌控者，您可以使用Adobe Mobile Services SDK來支援GDPR擷取和刪除行動應用程式的要求。

對於行動應用程式的 Adobe Mobile SDK 部分，您可以使用下列設定和方法:

* 如要擷取來自 SDK 的資料，並將此資料傳送至您的伺服器，請使用 `getAllIdentifiersAsync` 方法。

   如需詳細資訊，請參閱[擷取儲存的識別碼](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)。

* 如要設定您的選擇狀態並協助處理 GDPR 資料刪除請求，請使用以下的設定:

   * `privacyDefault`
   * `setPrivacyStatus`

   如需詳細資訊，請參閱[設定使用者的選擇狀態](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)。

## 其他資訊 {#section_7C7124C50D85469C8C8714533FB1A37D}

* 如需有關GDPR的詳細資訊，請參 [閱GDPR和您的業務](https://www.adobe.com/tw/privacy/general-data-protection-regulation.html)。
* To see the GDPR API documentation, go to [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html).

