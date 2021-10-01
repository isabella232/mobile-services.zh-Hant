---
description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
title: PII 回傳
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# PII 回傳 {#pii-postbacks}

您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。

若您要使用 Adobe SDK 來收集 PII，應傳送追蹤 PII 呼叫。雖然使用此呼叫會啟用PII資料收集，但SDK不會自動將資料傳送至任何Adobe端點。 PII 類型回傳需要以適當的端點進行設定。

>[!TIP]
>
>須使用支援 HTTPS 的端點才能使用 PII 回傳類型。

## 追蹤 PII 回傳 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的專案*。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 準備好擷取 PII 時，請呼叫 `trackPII` 以針對此動作、事件或檢視傳送點擊：

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
