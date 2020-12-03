---
description: 本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-description: 本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-title: 檢索儲存的標識符
title: 檢索儲存的標識符
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 64%

---


# 擷取儲存的識別碼{#retrieving-stored-identifiers}

本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。

如需有關GDPR的詳細資訊，請參 [閱GDPR和您的業務](https://www.adobe.com/tw/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法會擷取儲存於 Experience Cloud SDK 中的身分識別。You must call this method **before** the user opts-out.

Experience Cloud SDK身分識別（如適用）會儲存在本機，並傳回至JSON字串中，其中可能包含：

* 公司內容 - IMS 組織 ID
* 使用者 ID
* Experience Cloud iD(MID)，先前稱為Marketing Cloud ID
* 整合代碼（ADID、推播ID）
* 資料來源 ID (DPID、DPUUID)
* Analytics ID (AVID、AID、VID 以及相關 RSID)
* 目標舊有ID(TNTID、TNT3rdpartyID)
* Audience Manager ID (UUID)

以下是 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法的範例:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

