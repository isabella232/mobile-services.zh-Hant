---
description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
title: PII 回傳
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
exl-id: 9f0b9d7b-e51d-477b-ae04-72ab09fbc6fd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# PII 回傳 {#pii-postbacks}

您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。

若您要使用 Adobe SDK 來收集 PII，應傳送追蹤 PII 呼叫。雖然使用此呼叫會啟用 PII 資料集合，但是 SDK 不會自動傳送資料至 Adobe 端點。PII 類型回傳需要以適當的端點進行設定。

>[!TIP]
>
>須使用支援 HTTPS 的端點才能使用 PII 回傳類型。

## 追蹤 PII 回傳 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫：

   ```java
   #import "ADBMobile.h"
   ```

1. 準備好擷取 PII 時，請呼叫 `trackPII` 以針對此動作、事件或檢視傳送點擊：

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```
