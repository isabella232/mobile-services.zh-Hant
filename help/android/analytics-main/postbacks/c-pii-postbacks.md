---
description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
seo-description: 您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。
seo-title: PII 回傳
title: PII 回傳
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

您可以使用 Adobe SDK 來收集個人識別資訊 (PII)，並傳送至第三方端點。

若您要使用 Adobe SDK 來收集 PII，應傳送追蹤 PII 呼叫。雖然使用此呼叫會啟用 PII 資料集合，但是 SDK 不會自動傳送資料至 Adobe 端點。PII 類型回傳需要以適當的端點進行設定。

>[!TIP]
>
>An endpoint that supports HTTPS is required to use the PII postback type.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 將[程式庫]新增至您的專案並實作生命週期。

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. 匯入程式庫:

   ```java
   #import "ADBMobile.h"
   ```

1. 當您準備擷取 PII 時，請呼叫 `trackPII` 以針對此動作、事件或檢視傳送點擊:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

