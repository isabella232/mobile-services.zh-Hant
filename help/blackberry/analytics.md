---
description: 將程式庫新增至專案後，您可以在應用程式中的任何地方進行任何Analytics方法呼叫（請務必將ADBMobile.h匯入至類別）。
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 13%

---

# Analytics {#analytics}

將程式庫新增至專案後，您可以在應用程式中的任何地方進行任何Analytics方法呼叫（請務必將ADBMobile.h匯入至類別）。

## 在Analytics中啟用行動應用報表 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

新增程式碼之前，請由您的Analytics管理員完成下列操作以啟用行動應用程式生命週期追蹤。 這些動作可確保您的報表套裝已準備好在您開始開發時擷取量度。

1. 開啟&#x200B;**[!UICONTROL 管理工具]** > **[!UICONTROL 報表套裝]**&#x200B;並選取您的行動報表套裝。
1. 按一下「**[!UICONTROL 編輯設定]** > **[!UICONTROL 行動管理]** > **[!UICONTROL 行動應用報表]**」。

   ![行動設定](assets/mobile-settings.png)

1. 按一下「**[!UICONTROL 啟用最新應用程式報表]**」。

   或者，您也可以按一下&#x200B;**[!UICONTROL 啟用行動位置追蹤]**&#x200B;和&#x200B;**[!UICONTROL 啟用背景點擊的舊版報表和歸因]**。

   ![啟用生命週期](assets/enable-lifecycle.png)

生命週期量度現在已可供擷取，而行動應用報表會顯示在行銷報表介面的&#x200B;**[!UICONTROL 報表]**&#x200B;功能表中。

## 收集生命週期量度 {#task_25D469C62DF84573AEB5E8E950B96205}

1. 若要在您的應用程式中收集生命週期量度，請呼叫`ApplicationUI`建構函式中的`collectLifecycleData()` 。

   例如：

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   如果在相同工作階段中呼叫了兩次`collectLifecycleData()`，則您的應用程式會在第一次呼叫後的每次呼叫中回報當機。 SDK會在應用程式關閉時設定標幟，指出是否成功退出。 如果未設定此標幟，`collectLifecyleData()`會回報當機。

## 事件、Prop 以及 eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

如果您查看過[ADBMobile類和方法參考](/help/blackberry/methods.md)，您可能會想知道應在何處設定事件、eVar、prop、heir和清單。 在第4版中，您無法再在應用程式中直接指派這些變數類型。 SDK 會改為使用內容資料和處理規則，將應用程式資料對應至 Analytics 變數以便報告。

處理規則提供幾項優點：

* 您可以直接變更資料對應，而無須將更新提交至 App Store。
* 您可以用有意義的資料名稱，取代設定報表套裝專用的變數。
* 對傳送額外資料的影響極小。這些值在透過處理規則對應前，不會出現在報表中。

您直接指派給變數的任何值，都應改為新增至`data` HashMap。

## 處理規則 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

處理規則可用來將您在內容資料變數中傳送的資料複製到eVar、prop和其他變數以供報告。

2013 年高峰會的[處理規則訓練](https://tv.adobe.com/embed/1181/16506/)

[處理規則](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[取得授權以使用處理規則](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

建議您使用「命名空間」將內容資料變數分組，因為這可協助您維持邏輯順序。 例如，如果您想要收集產品的資訊，可以定義下列變數：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

內容資料變數在處理規則介面中按字母排序，因此命名空間可讓您快速查看相同命名空間中的變數。

此外，我們聽說有些人使用eVar或prop編號來命名內容資料索引鍵：

```js
"eVar1":"jimbo"
```

這樣可讓您在處理規則中執行一次性對應時變得&#x200B;*稍微*&#x200B;更簡單，但在偵錯時會失去可讀性，而日後的程式碼更新則更困難。 強烈建議您改為為索引鍵和值使用描述性名稱：

```js
"username":"jimbo"
```

定義計數器事件的上下文變數可以有相同的索引鍵和值：

```js
"logon":"logon"
```

定義增量器事件的上下文資料變數可以將事件當作索引鍵，並將要增量的量當作值：

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe 會保留命名空間 `a.`。除了這些小限制以外，您的登入公司中的內容資料變數必須是唯一的，以避免衝突。

## 啟用離線追蹤 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

若要在裝置離線時儲存點擊，您可以選擇在`ADBMobileConfig.json`檔案中啟用離線追蹤。

在啟用離線追蹤之前，請非常注意設定檔案參考中所述的時間戳記需求。

## Analytics 方法 

如需BlackBerry可用的Analytics方法清單，請參閱[Adobe行動類別和方法參考](/help/blackberry/methods.md)中的&#x200B;*Analytics方法*。
