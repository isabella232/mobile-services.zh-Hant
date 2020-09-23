---
description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-title: 處理規則和內容資料
solution: Experience Cloud,Analytics
title: 處理規則和內容資料
topic: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 48%

---


# 處理規則與內容資料 {#processing-rules-and-context-data}

處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。如需詳細資訊，請參閱[處理規則](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

操作處理規則時，請記住以下資訊:

* 使用名稱空間將上下文資料變數分組，因為它有助於維持邏輯順序。 例如，若要收集產品的相關資訊，您可以定義下列變數：

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 上下文資料變數在處理規則介面中會依字母順序排序，讓您快速查看哪些變數位於相同的命名空間中。

   使用evar或prop編號，避免命名上下文資料索引鍵：

   ```js
   "eVar1":"jimbo"
   ```

   當您完成處 *理規則中的一次性對應* ，這可能會稍微輕鬆一些，但在除錯和未來的程式碼更新時，會失去可讀性，這可能會比較困難。 我們強烈建議您為索引鍵和值使用描述性名稱：

   ```js
   "username":"jimbo"
   ```

* 定義計數器事件的上下文變數應設為1:

   ```js
   "logon":"1"
   ```

* 定義增量器事件的上下文資料變數可以以事件為索引鍵，而要增量的量則為值：

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe 會保留命名空間 `"a."`。若要避免衝突，唯一的其他要求是，您的登入公司中的內容資料變數必須是唯一的。

