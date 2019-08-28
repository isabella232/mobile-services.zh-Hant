---
description: 此資訊可協助您使用視訊分析。
seo-description: 此資訊可協助您使用視訊分析。
seo-title: Video Analytics
solution: Marketing Cloud、Analytics
title: Video Analytics
topic: 開發人員和實施
uuid: 7d4e6668-a1 d9-41da-96c8-8bbac860 c5 b0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Video Analytics {#video-analytics}

此資訊可協助您使用視訊分析。

Video measurement is described in detail in the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html/) guide. 所有 AppMeasurement 平台上測量視訊的一般程序都很相似。這一節快速入門提供開發人員任務的基本概覽和程式碼範例。

下表列出會傳送至 Analytics 的媒體資料。使用處理規則將上下文資料對應至Analytics變數。

* **a.media.name**

   (必要) 當訪客以某種方式檢視視訊時，請按照實施中指定的方式來收集視訊的名稱。您可以新增此變數的分類。

   (**選用**) Custom Insight 變數可提供視訊路徑資訊。

   * 變數類型：eVar
   * 預設過期時間: 造訪
   * Custom Insight (s.prop，用於視訊路徑)

* **a.media.name**

   (選用) 提供視訊路徑資訊。必須由 ClientCare 為此變數啟用路徑。

   事件類型: 自訂分析 (s.prop)

   * 變數類型：自訂分析(s. prop)

* **a.media.segment**

   (必要) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   預設的視訊資料收集方法會於下列時間點收集資料:

   * 視訊開始 (播放)
   * 區段開始
   * 視訊結束 (停止)
   Analytics 會在區段開始時計算第一個區段檢視，也就是訪客開始觀看的時候。後續的區段檢視會作為區段開始。

   * 變數類型：eVar
   * 預設過期時間: 頁面檢視


* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會獲指派「視訊」的內容類型。不需專為視訊追蹤保留此變數。具有使用此相同變數的其他內容報表內容類型，可讓您分析不同類型內容上造訪者的分佈情況。舉例來說，使用了這個變數，您就可以利用像是「article」或「product page」的值來標記其他內容類型。從視訊測量觀點，內容類型可讓您識別視訊訪客並計算視訊轉換率。

   * 變數類型：eVar
   * 預設過期時間: 頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型：Event
   * 類型: 計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數：Event
   * 類型: 計數器

* **a.media.segmentView**

   指出有訪客檢視了視訊區段的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型：Event
   * 類型: 計數器

* **a .media.complete**

   指出使用者已檢視完整的視訊。預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定想要將距離視訊結尾幾秒視為檢視完成。針對即時視訊和沒有已定義結尾的其他資料流，您可以指定測量完成的自訂點。例如，在檢視特定時間之後。

   * 變數類型：Event
   * 類型: 計數器


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

以您要用來追蹤視訊的設定，設定 `MediaSettings` 物件。

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. 舉例來說，當播放器暫停時，需呼叫 `Stop`。播放開始或繼續時則是呼叫 `Play`。

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

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingSwith(WinJS：SettingSwith)**

   傳回 `MediaSetting` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingSwith(WinJS：AdSettingSwith**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 以下是此方法的語法:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **開啓(WinJS：open)**

   Tracks a media open using the settings defined in `settings`.

   * 以下是此方法的語法:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **關閉(WinJS：close)**

   追蹤命名為&#x200B;*「名稱」*&#x200B;之媒體項目的媒體關閉。

   * 以下是此方法的語法:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.close("mediaName");
      ```

* **播放(WinJS：play)**

   Tracks a media play for the media item named *`name`* at the given *offset* (in seconds).

   * 以下是此方法的語法:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **完整(WinJS：complete)**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 以下是此方法的語法:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **停止(WinJS：stop)**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 以下是此方法的語法:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **按一下(WinJS：click)**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **追蹤(WinJS：track)**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.Media.track("mediaName", null);
      ```

