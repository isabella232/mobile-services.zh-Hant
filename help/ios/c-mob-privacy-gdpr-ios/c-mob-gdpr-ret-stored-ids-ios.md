---
description: 本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。
title: 擷取儲存的識別碼
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---

# 擷取儲存的識別碼{#retrieving-stored-identifiers}

本資訊可協助自您的 iOS 應用程式擷取本機儲存的 Experience Cloud SDK 身分識別，以及處理 GDPR 資料存取請求。

如需GDPR的詳細資訊，請參閱[GDPR和您的業務](https://www.adobe.com/tw/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法會擷取儲存於 Experience Cloud SDK 中的身分識別。您必須在使用者選擇退出的&#x200B;**之前呼叫此方法**。

Experience CloudSDK身分識別（若適用）會儲存於本機，並在JSON字串中傳回，其中可能包含：

* 公司內容 - IMS 組織 ID
* 使用者 ID
* Experience CloudiD(MID)，先前稱為Marketing CloudID
* 整合程式碼（ADID、推送ID）
* 資料來源 ID (DPID、DPUUID)
* Analytics ID (AVID、AID、VID 以及相關 RSID)
* Target舊版ID(TNTID、TNT3rdpartyID)
* Audience Manager ID (UUID)

以下是 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法的範例:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
