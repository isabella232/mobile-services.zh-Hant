---
description: 幫助您處理視頻分析的資訊。
solution: Experience Cloud Services,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 71%

---

# 視頻分析 {#video-analytics}

幫助您處理視頻分析的資訊。

視頻測量在 [測量Adobe Analytics流媒體](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hant) 的子菜單。 所有AppMeasurement平台中測量視頻的一般過程非常相似。 此快速入門部分提供了開發人員任務的基本概述以及代碼示例。

下表列出會傳送至 Analytics 的媒體資料。使用處理規則，將內容資料對應至 Analytics 變數。

* **a.media.name**

   （必需）當訪問者以某種方式查看視頻時，按實現中指定的方式收集視頻名稱。您可以為此變數添加分類。

   (**選用**) 自訂深入分析變數能提供視訊路徑資訊。

   * 變數類型: eVar
   * 預設過期時間：造訪
   * 自訂分析 (s.prop，用於視訊路徑)

* **a.media.name**

   (選用) 提供視訊路徑資訊。必須由客戶服務為此變數啟用路徑。

   事件類型: 自訂分析 (s.prop)

   * 變數類型: Custom Insight (s.prop)

* **a.media.segment**

   (必要) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。例如，當訪問者查看視頻中的第一個段時，SiteCatalyst可能會在 `1:M:0-25` 分部eVar。

   系統會於下列時間點，以預設的視訊資料收集方法收集資料：

   * 視訊開始 (播放)
   * 區段開始
   * 視訊結束 (停止)

   當訪客開始觀看時，Analytics 會在區段的開頭計算第一個區段檢視次數。後續區段會在區段開始時計為檢視次數。

   * 變數類型: eVar
   * 預設過期時間：頁面檢視


* **a.contentType**

   收集訪客所檢視內容類型的相關資料。通過視頻測量發送的點擊被分配「視頻」的內容類型。 此變數不需要專門保留用於視頻跟蹤。 使用同一變數使用其他內容報告內容類型，可以分析訪問者在不同類型內容之間的分佈。 例如，可以使用此變數使用值（如「article」或「product page」）標籤其他內容類型。 從視頻測量的角度，內容類型允許您識別視頻訪問者並計算視頻轉換率。

   * 變數類型: eVar
   * 預設過期時間：頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型: 事件
   * 類型：計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。然而，此量度不會針對訪客所檢視的視訊，提供訪客檢視多少內容、檢視視訊哪一部分的相關資訊。

   * 變數：事件
   * 類型：計數器

* **a.media.segmentView**

   指出有訪客檢視了視訊區段的某部分。然而，此量度不會針對訪客所檢視的視訊，提供訪客檢視多少內容、檢視視訊哪一部分的相關資訊。

   * 變數類型: 事件
   * 類型：計數器

* **a .media.complete**

   指出使用者已檢視完整的視訊。預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定想要將距離視訊結尾幾秒視為檢視完成。針對即時視訊和沒有已定義結尾的其他資料流，您可以指定測量完成的自訂點。例如，在特定檢視次數之後。

   * 變數類型: 事件
   * 類型：計數器

## 設定媒體設定 {#section_929945D4183C428AAF3B983EFD3E2500}

以您要用來追蹤視訊的設定，設定 `MediaSettings` 物件。

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## 追蹤播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

若要測量視訊播放，必須在適當時間呼叫 `Play`、`Stop` 以及 `Close` 方法。舉例來說，當播放器暫停時，需呼叫 `Stop`。播放開始或繼續時則是呼叫 `Play`。

## 類別 {#section_16838332727348F990305C0C6B0D795C}

### 類別: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## 媒體測量類別與方法參考 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith(winJS:設定為)**

   傳回 `MediaSetting` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith(winJS:adSettingsWith**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 此方法的語法如下：

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **開啟(WinJS:開啟)**

   使用中定義的設定跟蹤開啟的介質 `settings`。

   * 此方法的語法如下：

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.open(mySettings); 
      ```

* **關閉(winJS:關閉)**

   跟蹤介質關閉的介質項 *名稱*。

   * 此方法的語法如下：

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.close("mediaName");
      ```

* **播放(winJS:播放)**

   跟蹤名為的媒體項的媒體播放 *`name`* 在給定 *偏移* （秒）。

   * 此方法的語法如下：

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **完成(winJS:完成)**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 此方法的語法如下：

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **停止(winJS:停)**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 此方法的語法如下：

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **按一下(winJS:按一下)**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **跟蹤(WinJS:跟蹤)**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.track("mediaName", null);
      ```
