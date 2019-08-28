---
description: Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。
seo-description: Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。
seo-title: 隱私權與一般資料保護規範
title: 隱私權與一般資料保護規範
uuid: 69bb82de-1993-440c-a1 b0-8d37919 b48 b6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 隱私權與一般資料保護規範 {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 為控制器提供可配合一般資料保護規範 (GDPR) 的 API，讓使用者能夠擷取本機儲存的身分識別，以及設定資料收集與傳輸的選擇狀態旗標。

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

當 Adobe 提供軟體和服務給企業時，Adobe 為了提供這些服務，會以資料處理者的角色處理和儲存任何個人資料。身為資料處理者，Adobe 處理個人資料時，須遵循貴公司的允許和指示 (例如，依照您與 Adobe 合約中的規定)。

身為資料控管者，您可以使用 Adobe Mobile Services SDK 支援來自行動應用程式的 GDPR 擷取和刪除請求。

## 新版 Adobe Experience Cloud SDK

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 如需詳細資訊，請參閱 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。


對於行動應用程式的 Adobe Mobile SDK 部分，您可以使用下列設定和方法:

* 如要擷取來自 SDK 的資料，並將此資料傳送至您的伺服器，請使用 `getAllIdentifiersAsync` 方法。

   如需詳細資訊，請參閱 [「擷取儲存的識別碼](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)」。

* 如要設定您的選擇狀態並協助處理 GDPR 資料刪除請求，請使用以下的設定:

   * `privacyDefault`
   * `setPrivacyStatus`
   如需詳細資訊，請參閱 [設定使用者的選擇狀態](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)。

## 其他資訊 {#section_7C7124C50D85469C8C8714533FB1A37D}

* 如需 GDPR 的詳細資訊，請參閱 [GDPR 和您的業務](https://www.adobe.com/privacy/general-data-protection-regulation.html)。
* 若要查看 GDPR API 文件，請前往[一般資料保護規範 API](https://adobe.io/apis/cloudplatform/gdpr.html)。

