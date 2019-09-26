---
description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-title: 處理規則和內容資料
solution: Marketing Cloud,Analytics
title: 處理規則和內容資料
topic: 開發人員和實施
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。

如需詳細資訊，請參閱下列內容:

* 2013 年峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)
* 獲得使用處理規則的授權

   For more information about processing rules, see Processing rules overview.[](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

操作處理規則時，請記住以下資訊:

* 使用命名空間為內容資料變數分組，有助您維持邏輯排序。

   例如，若您想要收集產品資訊，將需要定義以下變數:

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

   這樣可協助您在處理規則中執行一次性對應時變得&#x200B;*較為*&#x200B;容易，但在日後的程式碼更新和偵錯時會失去易讀性，使其變得更困難。請改為為鍵值和值使用描述性名稱:

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
>Adobe reserves the namespace " ". `a.`除了此限制外，若要避免衝突，唯一的要求是，您的登入公司中的內容資料變數必須是唯一的。

