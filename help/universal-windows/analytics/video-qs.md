---
description: 可協助您處理Video Analytics的資訊。
solution: Experience Cloud,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: f45dac3b-cd2e-4fba-a3b2-c243640ecfa4
exl-id: bf7a2936-4a90-4630-8a0c-df41baa1d6a8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 71%

---

# Video Analytics {#video-analytics}

可協助您處理Video Analytics的資訊。

在[在Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hant)測量串流媒體指南中詳細說明視訊測量。 所有AppMeasurement平台上測量視訊的一般程式都很類似。 此快速入門區段提供開發人員工作的基本概覽和程式碼範例。

下表列出會傳送至 Analytics 的媒體資料。使用處理規則，將內容資料對應至 Analytics 變數。

* **a.media.name**

   （**必要**）當訪客以某種方式檢視視訊時，收集實作中指定的視訊名稱。您可以為此變數新增分類。

   (**選用**) 自訂深入分析變數能提供視訊路徑資訊。

   * 變數類型: eVar
   * 預設過期時間：造訪
   * 自訂分析 (s.prop，用於視訊路徑)

* **a.media.name**

   (**選用**) 提供視訊路徑資訊。必須由客戶服務為此變數啟用路徑。

   * 事件類型: 自訂分析 (s.prop).
   * 變數類型: Custom Insight (s.prop)

* **a.media.segment**

   (**必要**) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。

   此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。例如，當訪客檢視視訊中的第一個區段時，SiteCatalyst可能會在`1:M:0-25`區段eVar中收集下列內容。

   預設的視訊資料收集方法會在下列時間點收集資料：視訊開始（播放）、區段開始和視訊結束（停止）。 當訪客開始觀看時，Analytics 會在區段的開頭計算第一個區段檢視次數。後續區段會在區段開始時計為檢視次數。

   * 變數類型: eVar
   * 預設過期時間：頁面檢視

* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會被指派為「視訊」的內容類型。 不需專為視訊追蹤保留此變數。 使用此相同變數而擁有其他內容報表內容類型，可讓您分析不同內容類型中訪客的分佈情況。 例如，您可以使用此變數，使用「article」或「product page」等值來標籤其他內容類型。

   從視訊測量觀點，「內容類型」可讓您識別視訊訪客，並因此計算視訊轉換率。

   * 變數類型: eVar
   * 預設過期時間：頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型: 事件
   * 類型：計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。然而，此量度不會針對訪客所檢視的視訊，提供訪客檢視多少內容、檢視視訊哪一部分的相關資訊。

   * 變數類型: 事件
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

### 媒體測量類別與方法參考 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith(winJS:settingsWith)**

   傳回 `MediaSettings` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **AdSettingsWith(winJS:adSettingsWith)**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 此方法的語法如下：

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **開啟(winJS:open)**

   使用`settings`中定義的設定來追蹤媒體開啟。

   * 此方法的語法如下：

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.open(mySettings);
      ```

* **關閉(winJS:close)**

   跟蹤名為&#x200B;*`name`*&#x200B;的媒體項的媒體關閉。

   * 此方法的語法如下：

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **播放(winJS:play)**

   在指定的&#x200B;*offset*（以秒為單位）追蹤名為&#x200B;*`name`*&#x200B;的媒體項目的媒體播放。

   * 此方法的語法如下：

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **完成(winJS:complete)**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 此方法的語法如下：

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **停止(winJS:停止)**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 此方法的語法如下：

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **按一下(winJS:按一下)**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **追蹤(winJS:track)**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADB.Media.track("mediaName",  null);
      ```
