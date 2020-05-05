---
description: 若要開始使用Experience Cloud Device Co-op，請連絡您的Adobe代表。
seo-description: 若要開始使用Experience Cloud Device Co-op，請連絡您的Adobe代表。
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

若要開始使用Experience Cloud Device Co-op，請連絡您的Adobe代表。

若要為Experience Cloud Device Co-op啟用行動應用程式，請完成Experience Cloud Android SDK的下列步驟：

>[!IMPORTANT]
>
>此功能需使用 Android SDK 4.8.3 版或更新版本。

從SDK 4.16.1版開始，Device Co-op會員可以從Experience Cloud Device Co-op選擇其行動裝置資料。 如需詳細資訊，請 [參閱ADBMobile JSON設定](/help/android/configuration/json-config/json-config.md) ，以 `visitorAPI.js` 及isCoopSafe [的方法](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html)。

1. 實施 Adobe Mobile SDK。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/android/getting-started/dev-qs.md)。
1. 啟用您的 Experience Cloud ID。

   如需詳細資訊，請參閱 [Experience Cloud ID 設定](/help/android/c-marketing-cloud/mcvid.md)。
1. 使用其中一種同步方法，以傳遞驗證身分識別 (例如 CRM ID 或雜湊電子郵件)。

   如需詳細資訊，請參閱 [Adobe Experience Platform Identity Service 方法](/help/android/c-marketing-cloud/mc-methods.md)。

## `coopUnsafe` 標幟

以下是有關 `coopUnsafe` 標幟的額外資訊:

* 最低 SDK 版本: 4.16.1
* `marketingCloud` 物件的布林值屬性一旦設為 `true`，就會導致裝置退出 Experience Cloud 的 Device Co-Op。
* 預設值為 `false`.
* **唯有**&#x200B;以 Device Co-op 佈建的客戶，才會使用此設定。

若 Device Co-op 成員要求將此值設為 `true`，您需要與 Co-op 團隊合作，為您的 Device Co-op 帳戶向其申請黑名單標記。沒有啟用可這些標幟的自助式路徑。

請記住以下資訊:

* `coopUnsafe` 設為 `true` 時，`coop_unsafe=1` 一律會附加至 Audience Manager 和訪客 ID 點擊。
* 如果啟用 Analytics 伺服器端轉送至 Audience Manager，您也會看到 `coop_unsafe=1` Analytics 點擊。