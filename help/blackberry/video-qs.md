---
description: 測量視訊的一般程式在所有AppMeasurement平台上都非常類似。 本節提供開發人員工作的基本概觀以及程式碼範例。
seo-description: 測量視訊的一般程式在所有AppMeasurement平台上都非常類似。 本節提供開發人員工作的基本概觀以及程式碼範例。
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 66%

---


# Video Analytics {#video-analytics}

測量視訊的一般程式在所有AppMeasurement平台上都非常類似。 本節提供開發人員工作的基本概觀以及程式碼範例。

For more information about Video measurement, see the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/zh-Hant/media-analytics/using/media-overview.html) guide.  下表列出會傳送至 Analytics 的媒體資料。使用處理規則將「上下文資料變數」欄中的上下文資料對應至Analytics變數，如「變數類型」欄所述。

## 將播放器事件對應至 Analytics 變數

* **a.media.name**

   （必要）當訪客以某種方式檢視視訊時，收集視訊名稱（如實作中所指定）。您可以新增此變數的分類。

   **（可選）** 「自訂分析」變數提供視訊路徑資訊。

   * 變數名稱：eVar
      * 預設過期時間：造訪
      * 自訂分析 (s.prop，用於視訊路徑)

* **a.media.name**

   (**選用**) 提供視訊路徑資訊。ClientCare必須為此變數啟用路徑分析。

   * 事件類型: 自訂分析 (s.prop)
   * 自訂分析(s.prop)

* **a.media.segment**

   (**必要**) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. 預設的視訊資料收集方法會收集視訊開始（播放）、區段開始和視訊結束（停止）點的資料。

   當訪客開始觀看時，Analytics 會在區段的開頭計算第一個區段檢視次數。後續區段會在區段開始時計為檢視次數。

   * 變數類型: eVar
   * 預設過期時間：頁面檢視

* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會指派內容類型為「視訊」。 此變數不需專門保留供視訊追蹤使用。 使用相同變數擁有其他內容報告內容類型可讓您分析不同內容類型的訪客分佈。 舉例來說，使用了這個變數，您就可以利用像是「article」或「product page」的值來標記其他內容類型。從視訊測量觀點，「內容類型」可讓您識別視訊訪客，並因此計算視訊轉換率。

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

## 追蹤播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

若要測量視訊播放，必須在適當時間呼叫 `mediaPlay`、`mediaStop` 以及 `mediaClose` 方法。舉例來說，當播放器暫停時，需呼叫 `mediaStop`。播放開始或繼續時則是呼叫 `mediaPlay`。

## 媒體測量類別與方法參考 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   開啟視訊以進行追蹤。

   * 此方法的語法如下：

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * 此方法的程式碼範例如下：

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   開啟 `MediaSettings` 物件以供追蹤。

   * 以下是此方法的語法:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Closes the media item named *`name`*.

   * 此方法的語法如下：

      ```cpp
      void close(QString name);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * 此方法的語法如下：

      ```cpp
      void play(QString name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **complete**

   Manually mark the media item as complete at the *`offset`* provided (in seconds).

   * 此方法的語法如下：

      ```cpp
      void complete(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 此方法的語法如下：

      ```cpp
      stop(QString name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```cpp
      void click(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
