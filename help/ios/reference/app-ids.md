---
description: 下表說明 iOS SDK 和 Adobe Mobile Services 所採用的不同應用程式識別碼。
seo-description: 下表說明 iOS SDK 和 Adobe Mobile Services 所採用的不同應用程式識別碼。
seo-title: 應用程式 ID
solution: Marketing Cloud,Analytics
title: 應用程式 ID
topic: 開發人員和實施
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: ht
source-git-commit: 0e22d5e080b680ff6b23462f1bc12f27d99e6d42

---


# 應用程式 ID {#app-ids}

下表說明 iOS SDK 和 Adobe Mobile Services 所採用的不同應用程式識別碼。

| ID | 說明 |
|--- |--- |
| 與生命週期量度一併傳送的 ID | 此 ID 為應用程式名稱及提交至應用程式商店搭售版本的組合。此值可用於 Adobe Mobile Services 中的「版本」報表，且您可依照應用程式的特定發行版本使用此值篩選結果。 |
| 應用程式商店 ID | 此 ID 會由應用程式商店指派至應用程式，並會在您建立贏取連結時於 Adobe Mobile Services 中提供。 |
| ADBMobile JSON 設定中的 AppID | 此 ID 為 Adobe Mobile Services 針對系統中的所有關聯中繼資料，指派至應用程式例項的唯一 ID。此 ID 可用來針對贏取追蹤或追蹤連結建立唯一 URL，會自動新增至從使用者介面下載的 ADBMobile JSON 設定檔案中，且可在應用程式「贏取」設定下的「管理應用程式設定」中找到。 |

