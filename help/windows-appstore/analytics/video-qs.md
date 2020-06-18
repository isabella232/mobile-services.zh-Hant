---
description: 協助您使用視訊分析的資訊。
seo-description: 協助您使用視訊分析的資訊。
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 65%

---


# Video Analytics {#video-analytics}

協助您使用視訊分析的資訊。

在Adobe Analytics中測量音訊和視訊指南 [中，對視訊測量有詳細說明](https://docs.adobe.com/content/help/zh-Hant/media-analytics/using/media-overview.html/) 。 測量視訊的一般程式在所有AppMeasurement平台上都非常類似。 此快速入門區段提供開發人員工作的基本概觀以及程式碼範例。

下表列出會傳送至 Analytics 的媒體資料。使用處理規則，將內容資料對應至 Analytics 變數。

* **a.media.name**

   （必要）當訪客以某種方式檢視視訊時，收集視訊名稱（如實作中所指定）。您可以新增此變數的分類。

   (可&#x200B;**選**)自訂分析變數提供視訊路徑資訊。

   * 變數類型: eVar
   * 預設過期時間: 造訪
   * 自訂分析（s.prop，用於視訊路徑）

* **a.media.name**

   (選用) 提供視訊路徑資訊。ClientCare必須為此變數啟用路徑分析。

   事件類型: 自訂分析 (s.prop)

   * 變數類型: Custom Insight (s.prop)

* **a.media.segment**

   (必要) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   預設的視訊資料收集方法會收集下列點的資料：

   * 視訊開始（播放）
   * 區段開始
   * 視訊結束（停止）

   Analytics會在訪客開始檢視區段時計算第一個區段檢視。 當區段開始時，後續區段會檢視。

   * 變數類型: eVar
   * 預設過期時間: 頁面檢視


* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會指派內容類型為「視訊」。 此變數不需專門保留供視訊追蹤使用。 使用相同變數擁有其他內容報告內容類型可讓您分析不同內容類型的訪客分佈。 舉例來說，使用了這個變數，您就可以利用像是「article」或「product page」的值來標記其他內容類型。從視訊測量的角度來看，內容類型可讓您識別視訊訪客並計算視訊轉換率。

   * 變數類型: eVar
   * 預設過期時間: 頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型: 事件
   * 類型: 計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數： 事件
   * 類型: 計數器

* **a.media.segmentView**

   指出有訪客檢視了視訊區段的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型: 事件
   * 類型: 計數器

* **a .media.complete**

   指出使用者已檢視完整的視訊。預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定想要將距離視訊結尾幾秒視為檢視完成。針對即時視訊和沒有已定義結尾的其他資料流，您可以指定測量完成的自訂點。例如，在特定檢視次數之後。

   * 變數類型: 事件
   * 類型: 計數器


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

* **SettingsWith(winJS: settingsWith)**

   傳回 `MediaSetting` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * 以下是此方法的範例程式碼：

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith(winJS: adSettingsWith**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 以下是此方法的語法：

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * 以下是此方法的範例程式碼：

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **開啟(winJS: 開啟)**

   使用中定義的設定跟蹤開啟的介質 `settings`。

   * 以下是此方法的語法：

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.open(mySettings); 
      ```

* **關閉(winJS: 關閉)**

   追蹤名稱為「名稱」的媒體項目的媒 *體關閉*。

   * 以下是此方法的語法：

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.close("mediaName");
      ```

* **播放(winJS: 播放)**

   追蹤指定偏移處（以秒為單位） *`name`* 的媒體項 *目* 的媒體播放。

   * 以下是此方法的語法：

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **完整(winJS: 完整)**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 以下是此方法的語法:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **停止(winJS: 停止)**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 以下是此方法的語法：

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **按一下(winJS: 按一下)**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **追蹤(winJS: 追蹤)**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法：

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 以下是此方法的範例程式碼：

      ```js
      ADB.Media.track("mediaName", null);
      ```

