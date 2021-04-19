---
description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-description: 處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。
seo-title: 處理規則和內容資料
solution: Experience Cloud,Analytics
title: 處理規則和內容資料
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# 處理規則與內容資料 {#processing-rules-and-context-data}

處理規則是用來將您在內容資料變數中傳送的資料，複製到 eVar、prop 及其他變數以供報告。如需詳細資訊，請參閱[處理規則](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

操作處理規則時，請記住以下資訊:

* 使用命名空間為內容資料變數分組，有助您維持邏輯排序。例如，若要收集產品資訊，您可能要定義下列變數：

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

   這樣可讓您在處理規則中完成一次性對應時變得&#x200B;*較為*&#x200B;容易，但在除錯和日後的程式碼更新時不易讀，使其變得更困難。因此，我們強烈建議您為索引鍵和值使用描述性名稱：

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
>Adobe 會保留命名空間 `"a."`。若要避免衝突，唯一的其他要求是，您的登入公司中的內容資料變數必須是唯一的。
