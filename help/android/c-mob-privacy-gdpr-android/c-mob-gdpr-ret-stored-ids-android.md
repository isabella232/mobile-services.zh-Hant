---
description: 本資訊可協助自您 Android 應用程式擷取儲存於本機的 SDK 身分識別，以及處理 GDPR 資料存取請求。
title: 擷取儲存的識別碼
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 64%

---

# 擷取儲存的識別碼{#retrieving-stored-identifiers}

本資訊可協助自您 Android 應用程式擷取儲存於本機的 SDK 身分識別，以及處理 GDPR 資料存取請求。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法會擷取儲存於 SDK 中的身分識別。您必須在使用者選擇退出的&#x200B;**之前呼叫此方法**。

SDK身分識別（若適用）會儲存於本機，並在JSON字串中傳回，其中可能包含：

* 公司內容 - IMS 組織 ID
* 使用者 ID
* Experience CloudiD(MID)，先前稱為Marketing CloudID
* 整合程式碼（ADID、推送ID）
* 資料來源 ID (DPID、DPUUID)
* Analytics ID (AVID、AID、VID 以及相關 RSID)
* Target舊版ID(TNTID、TNT3rdpartyID)
* Audience Manager ID (UUID)

以下是 Android 中的 `ADBMobile getAllIdentifiersAsync` 方法的範例:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
