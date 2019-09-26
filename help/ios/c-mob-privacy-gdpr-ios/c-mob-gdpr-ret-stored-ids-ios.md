---
description: 本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-description: 本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-title: 擷取儲存的識別碼
title: 擷取儲存的識別碼
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。

如需 GDPR 的詳細資訊，請參閱 [GDPR 和您的業務](https://www.adobe.com/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>The  method retrieves identities that are stored in the Experience Cloud SDKs. `getAllIdentifiersAsync`您必須在使用者選擇退出&#x200B;**之前**&#x200B;呼叫此方法。

Experience Cloud SDK 身分識別 (若適用的話) 會儲存在本機，並於 JSON 字串中傳回，且可能包括:

* 公司內容 - IMS 組織 ID
* 使用者 ID
* Experience Cloud ID (MID) (舊稱 Marketing Cloud ID)
* 整合代碼 (ADID、Push ID)
* 資料來源 ID (DPID、DPUUID)
* Analytics ID (AVID、AID、VID 以及相關 RSID)
* Target 舊版 ID (TNTID、TNT3rdpartyID)
* Audience Manager ID (UUID)

以下是 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法的範例:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

