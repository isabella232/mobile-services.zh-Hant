---
description: 若要開始使用 Experience Cloud Device Co-op，請聯絡您的 Adobe 代表。
seo-description: 若要開始使用 Experience Cloud Device Co-op，請聯絡您的 Adobe 代表。
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

若要開始使用 Experience Cloud Device Co-op，請聯絡您的 Adobe 代表。

若要啟用您的行動應用程式以使用 ExperienceCloud Device Co-op，請針對 Experience Cloud iOS SDK 完成下列步驟。

>[!IMPORTANT]
>
>此功能需使用 iOS SDK 4.8.5 版或更新版本。

自 SDK 4.16.1 版開始，Device Co-op 成員可將其行動裝置資料退出 Experience Cloud Device Co-op。如需詳細資訊，請參閱[適用於 ](/help/ios/configuration/json-config/json-config.md)isCoopSafe`visitorAPI.js` 的 ADBMobile JSON Config[ 和 ](https://marketing.adobe.com/resources/help/zh_TW/mcvid/mcvid-coopsafe.html) 方法。

1. 實施 Adobe Mobile SDK。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/dev-qs.md)。
1. 啟用您的 Experience Cloud ID。

   如需詳細資訊，請參閱 [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。
1. 使用此處所含的其中一種同步方法，以傳遞驗證身分識別 (例如 CRM ID 或雜湊電子郵件)。

   如需詳細資訊，請參閱 [Adobe Experience Platform Identity Service 方法](/help/ios/marketing-cloud/mc-methods.md)。

## `coopUnsafe` 標幟

以下是有關 `coopUnsafe` 標幟的額外資訊:

* 最低 SDK 版本: 4.16.1
* `marketingCloud` 物件的布林值屬性一旦設為 `true`，就會導致裝置退出 Experience Cloud 的 Device Co-Op。
* 預設值為 `false`.
* **唯有**&#x200B;以 Device Co-op 佈建的客戶，才會使用此設定。

若 Device Co-op 成員要求將此值設為 `true`，您需要與 Co-op 團隊合作，為您的 Device Co-op 帳戶向其申請黑名單標記。沒有啟用可這些標幟的自助式路徑。

請記住以下資訊:

* `coopUnsafe` 設為 `true` 時，`coop_unsafe=1` 一律會附加至 Audience Manager 和訪客 ID 點擊。
* 如果啟用 Analytics 伺服器端轉送至 Audience Manager，您也會在 Analytics 點擊看到 `coop_unsafe=1`。


