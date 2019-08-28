---
description: 所有 AppMeasurement 平台上測量視訊的一般程序都很相似。本節提供開發人員任務的基本概覽以及程式碼範例。
seo-description: 所有 AppMeasurement 平台上測量視訊的一般程序都很相似。本節提供開發人員任務的基本概覽以及程式碼範例。
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a-9a-9db1-9a8c-1e56c12security4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics {#video-analytics}

所有 AppMeasurement 平台上測量視訊的一般程序都很相似。本節提供開發人員任務的基本概覽以及程式碼範例。

如需視訊測量的詳細資訊，請參閱「Adobe Analytics中 [的測量音訊和視訊](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) 」指南。下表列出會傳送至 Analytics 的媒體資料。請使用處理規則將「內容資料變數」欄中的內容資料對應至「變數類型」欄中的 Analytics 變數。

## 將播放器事件對應至Analytics變數

* **a.media.name**

   (必要) 當訪客以某種方式檢視視訊時，請按照實施中指定的方式來收集視訊的名稱。您可以新增此變數的分類。

   **(可選)** 自訂分析變數提供視訊路徑資訊。

   * 變數名稱：eVar
      * 預設過期時間: 造訪
      * Custom Insight (s.prop，用於視訊路徑)

* **a.media.name**

   (**選用**) 提供視訊路徑資訊。必須由 ClientCare 為此變數啟用路徑。

   * 事件類型: 自訂分析 (s.prop)
   * 自訂分析 (s.prop)

* **a.media.segment**

   (**必要**) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. 預設視訊資料收集方法會收集視訊開始(播放)、區段開始和視訊結束(停止)點處的資料。

   Analytics 會在區段開始時計算第一個區段檢視，也就是訪客開始觀看的時候。後續的區段檢視會作為區段開始。

   * 變數類型：eVar
   * 預設過期時間: 頁面檢視

* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會獲指派「視訊」的內容類型。不需專為視訊追蹤保留此變數。具有使用此相同變數的其他內容報表內容類型，可讓您分析不同類型內容上造訪者的分佈情況。舉例來說，使用了這個變數，您就可以利用像是「article」或「product page」的值來標記其他內容類型。從視訊測量觀點，內容類型可讓您識別視訊造訪者，並因此計算視訊轉換率。

   * 變數類型：eVar
   * 預設過期時間: 頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型：Event
   * 類型: 計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型：Event
   * 類型: 計數器

* **a.media.segmentView**

   指出有訪客檢視了視訊區段的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型：Event
   * 類型: 計數器

* **a .media.complete**

   指出使用者已檢視完整的視訊。預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定想要將距離視訊結尾幾秒視為檢視完成。針對即時視訊和沒有已定義結尾的其他資料流，您可以指定測量完成的自訂點。例如，在檢視特定時間之後。

   * 變數類型：Event
   * 類型: 計數器

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 舉例來說，當播放器暫停時，需呼叫 `mediaStop`。播放開始或繼續時則是呼叫 `mediaPlay`。

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   開啟視訊以供追蹤。

   * 以下是此方法的語法:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * 以下是此方法的範例程式碼:

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

   * 以下是此方法的語法:

      ```cpp
      void close(QString name);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * 以下是此方法的語法:

      ```cpp
      void play(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **完成**

   Manually mark the media item as complete at the *`offset`* provided (in seconds).

   * 以下是此方法的語法:

      ```cpp
      void complete(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 以下是此方法的語法:

      ```cpp
      stop(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```cpp
      void click(QString name, double offset);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
