---
description: 本資訊可協助自您 Android 應用程式擷取儲存於本機的 SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-description: 本資訊可協助自您 Android 應用程式擷取儲存於本機的 SDK 身分識別，以及處理 GDPR 資料存取請求。
seo-title: 擷取儲存的識別碼
title: 擷取儲存的識別碼
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 69%

---


# 擷取儲存的識別碼{#retrieving-stored-identifiers}

本資訊可協助自您 Android 應用程式擷取儲存於本機的 SDK 身分識別，以及處理 GDPR 資料存取請求。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法會擷取儲存於 SDK 中的身分識別。You must call this method **before** the user opts-out.

SDK身分識別（如適用）會儲存在本機，並傳回至JSON字串中，其中可能包含：

* 公司內容 - IMS 組織 ID
* 使用者 ID
* Experience Cloud iD(MID)，先前稱為Marketing Cloud ID
* 整合代碼（ADID、推播ID）
* 資料來源 ID (DPID、DPUUID)
* Analytics ID (AVID、AID、VID 以及相關 RSID)
* 目標舊有ID(TNTID、TNT3rdpartyID)
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
