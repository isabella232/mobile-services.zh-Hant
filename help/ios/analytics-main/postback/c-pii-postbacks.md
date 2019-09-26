---
description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
seo-description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
seo-title: PII 回傳
title: PII 回傳
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。

若您要使用 Adobe SDK 來收集 PII，應傳送追蹤 PII 呼叫。雖然使用此呼叫會啟用 PII 資料集合，但是 SDK 不會自動傳送資料至任何 Adobe 端點。PII 類型回傳需要以適當的端點進行設定。

>[!TIP]
>
>需要支援HTTPS的端點才能使用PII回傳類型。

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請 *參閱核心實作和生命週期中的「將SDK和設定檔案新*[增至專案」](/help/ios/getting-started/dev-qs.md)。
1. 匯入程式庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 當您準備擷取 PII 時，請呼叫 `trackPII` 以針對此動作、事件或檢視傳送點擊:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

