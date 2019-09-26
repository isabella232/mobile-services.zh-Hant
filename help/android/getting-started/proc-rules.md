---
description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-title: 處理規則和內容資料
solution: Marketing Cloud,Analytics
title: 處理規則和內容資料
topic: 開發人員和實施
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

操作處理規則時，請記住以下資訊:

* 使用命名空間為內容資料變數分組，有助您維持邏輯排序。例如，若要收集產品資訊，您將需要定義以下變數:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 內容資料變數在處理規則介面中按字母排序，讓您快速了解哪些變數在同一個命名空間中。

   避免使用 eVar 或 prop 編號來命名內容資料鍵值:

   ```js
   "eVar1":"jimbo"
   ```

   這樣可協助您在處理規則中完成一次性對應時變得&#x200B;*較為*&#x200B;容易，但在日後的程式碼更新和偵錯時會失去易讀性，使其變得更困難。因此，我們強烈建議您為鍵值和值使用描述性名稱:

   ```js
   "username":"jimbo"
   ```

* 定義計數器事件的內容變數應設為 1:

   ```js
   "logon":"1"
   ```

* 定義增量器事件的內容變數可以將事件作為鍵值，並將要增量的量作為值:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe保留命名空間 `"a."`。 若要避免衝突，唯一的其他要求是，您的登入公司中的內容資料變數必須是唯一的。

