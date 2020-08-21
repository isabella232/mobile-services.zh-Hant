---
description: 將程式庫新增至專案後，您可以在應用程式的任何地方進行任何Analytics方法呼叫（請確定您將ADBMobile.h匯入至您的類別）。
seo-description: 將程式庫新增至專案後，您可以在應用程式的任何地方進行任何Analytics方法呼叫（請確定您將ADBMobile.h匯入至您的類別）。
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 5%

---


# Analytics {#analytics}

將程式庫新增至專案後，您可以在應用程式的任何地方進行任何Analytics方法呼叫（請確定您將ADBMobile.h匯入至您的類別）。

## 在Analytics中啟用行動應用程式報表 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

在您新增程式碼之前，請您的Analytics管理員完成下列作業，以啟用行動應用程式生命週期追蹤。 這可確保您的報表套裝在您開始開發時，已準備好擷取量度。


1. 開啟「 **[!UICONTROL 管理工具]** >報 **[!UICONTROL 表套裝]** 」，然後選取您的行動報表套裝。
1. 按一 **[!UICONTROL 下「編輯設定]** > **[!UICONTROL 行動管理]** >行動應 **[!UICONTROL 用程式報表]**」。

   ![](assets/mobile-settings.png)

1. 按一 **[!UICONTROL 下「啟用最新應用程式報表]**」。

   或者，您也可以按一下「啟 **[!UICONTROL 用行動位置追蹤]** 」 **[!UICONTROL 和「啟用背景點擊的舊版報告與歸因」]**。

   ![](assets/enable-lifecycle.png)

生命週期量度現在已可供擷取，而行銷報告介面的「報告」功能表中 **[!UICONTROL 會顯示]** 「行動應用報表」。

## 收集生命週期度量 {#task_25D469C62DF84573AEB5E8E950B96205}

1. 若要在應用程式中收集生命週期量度，請在建構 `collectLifecycleData()` 函式中呼 `ApplicationUI` 叫。

   例如：

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   如果 `collectLifecycleData()` 在相同作業中呼叫兩次，則您的應用程式會在第一次呼叫後的每次呼叫上報告當機。 SDK會在應用程式關閉時設定標幟，指出成功退出。 如果未設定此標幟，則 `collectLifecyleData()` 會報告當機。

## 事件、Prop 以及 eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


如果您已檢視過 [ADBMobile類別和方法參考](/help/blackberry/methods.md)，您可能會想知道在何處設定事件、eVar、prop、繼承和清單。 在第4版中，您無法再直接在應用程式中指派這些類型的變數。 SDK會改用上下文資料和處理規則將應用程式資料對應至Analytics變數以進行報告。

處理規則提供您幾項優點：

* 您可以變更資料對應，毋需送出更新至App Store。
* 您可以對資料使用有意義的名稱，而不是設定報表套裝專屬的變數。
* 傳送額外資料的影響很小。 這些值在使用處理規則對應之前，不會出現在報表中。

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## 處理規則 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

處理規則可用來將您在上下文資料變數中傳送的資料複製到evar、prop和其他變數，以供報告。

[2013年峰會的處理規則](https://tv.adobe.com/embed/1181/16506/) 訓練

[處理規則](https://docs.adobe.com/content/help/zh-Hant/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[取得授權以使用處理規則](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我們建議您使用「名稱空間」將上下文資料變數分組，因為這有助於您維持邏輯順序。 例如，如果您想要收集產品的相關資訊，可以定義下列變數：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

上下文資料變數在處理規則介面中會依字母順序排序，因此命名空間可讓您快速查看位於相同名稱空間中的變數。

此外，我們聽說您中有些人使用evar或prop編號來命名上下文資料索引鍵：

```js
"eVar1":"jimbo"
```

這可能會讓處 *理規則執行一次對應* ，稍為輕鬆，但在除錯時會失去可讀性，而未來的程式碼更新則會更困難。 我們強烈建議您針對索引鍵和值使用描述性名稱：

```js
"username":"jimbo"
```

定義計數器事件的上下文變數可具有相同的索引鍵和值：

```js
"logon":"logon"
```

定義增量器事件的上下文資料變數可以將事件作為索引鍵，而將增量值作為值：

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe 會保留命名空間 `a.`。除了這些小限制外，上下文資料變數在登入公司中只需要是唯一的，以避免衝突。

## 啟用離線追蹤 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

若要在裝置離線時儲存點擊，您可以選擇在檔案中啟用離線追 `ADBMobileConfig.json` 蹤。

在啟用離線追蹤之前，請務必留意設定檔案參考中所述的時間戳記要求。

## Analytics 方法 

如需BlackBerry可用的Analytics方法清單，請參閱 *Adobe Mobile Class* and Method Reference中 [的Analytics方法](/help/blackberry/methods.md)。