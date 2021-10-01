---
description: 若要開始使用 Experience Cloud Device Co-op，請洽詢您的 Adobe 代表。
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
exl-id: e34b8a7e-3b70-4725-94a5-9903987c34f8
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 97%

---

# Experience CloudDevice Co-op {#experience-cloud-device-co-op}

若要開始使用 Experience Cloud Device Co-op，請洽詢您的 Adobe 代表。

若要為 Experience Cloud Device Co-op 啟用行動應用程式，請完成適用於 Experience Cloud Android SDK 的下列步驟：

>[!IMPORTANT]
>
>此功能需使用 Android SDK 4.8.3 版或更新版本。

從 SDK 4.16.1 版開始，Device Co-op 成員可以選擇將行動裝置資料退出 Experience Cloud Device Co-op。如需詳細資訊，請參閱 [ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)以及 [isCoopSafe](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/coopsafe.html) 的 `visitorAPI.js` 方法。

1. 實作 Adobe Mobile SDK。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)。
1. 啟用您的 Experience Cloud ID。

   如需詳細資訊，請參閱 [Experience Cloud ID 設定](/help/android/c-marketing-cloud/mcvid.md)。
1. 使用其中一種同步方法，以傳遞驗證身分識別 (例如 CRM ID 或雜湊電子郵件)。

   如需詳細資訊，請參閱 [Adobe Experience Platform Identity Service 方法](/help/android/c-marketing-cloud/mc-methods.md)。

## `coopUnsafe` 標幟

`coopUnsafe` 標幟的額外資訊如下：

* 最低 SDK 版本：4.16.1
* `marketingCloud` 物件的布林值屬性一旦設為 `true`，就會導致裝置退出 Experience Cloud 的 Device Co-Op。
* 預設值為 `false`。
* **唯有**&#x200B;以 Device Co-op 佈建的客戶，才會使用此設定。

若 Device Co-op 成員要求將此值設為 `true`，您需要與 Co-op 團隊合作，為您的 Device Co-op 帳戶申請封鎖名單標幟。沒有自助式路徑可供啟用這些標幟。

請記住以下資訊：

* `coopUnsafe` 設為 `true` 時，`coop_unsafe=1` 一律會附加至 Audience Manager 和訪客 ID 點擊。
* 如果啟用 Analytics 伺服器端轉送至 Audience Manager，您也會看到 `coop_unsafe=1` Analytics 點擊。
