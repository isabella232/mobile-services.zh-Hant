---
description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-title: 處理規則和內容資料
solution: Experience Cloud,Analytics
title: 處理規則和內容資料
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# 處理規則與內容資料{#processing-rules-and-context-data}

處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。

如需詳細資訊，請參閱下列內容:

* 2013 年高峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)
* 取得授權以使用處理規則

   如需處理規則的詳細資訊，請參閱[處理規則概述](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

操作處理規則時，請記住以下資訊:

* 使用命名空間為內容資料變數分組，有助您維持邏輯排序。

   例如，如果您想要收集產品的相關資訊，您可以定義下列變數：

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 內容資料變數在處理規則介面中按字母排序，讓您快速了解哪些變數在同一個命名空間中。

   避免使用 eVar 或 prop 編號來命名內容資料索引鍵：

   ```js
   "eVar1":"jimbo"
   ```

   如此，在處理規則中執行一次性對應時可能會&#x200B;*稍微*&#x200B;輕鬆一點，但在進行偵錯和日後的程式碼更新時，將會失去可讀性，使得作業反而更困難。請改用索引鍵和值的描述性名稱：

   ```js
   "username":"jimbo"
   ```

* 定義計數器事件的內容變數應設為 1：

   ```js
   "logon":"1"
   ```

* 定義增量器事件的內容變數可以將事件當作索引鍵，並將要增量的量當作值：

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe 會保留命名空間「`a.`」。除了此限制外，若要避免衝突，唯一的要求是，您的登入公司中的內容資料變數必須是唯一的。

