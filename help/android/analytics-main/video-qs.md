---
description: 以下提供一些關於透過視訊測量解決方案在 Android 上測量視訊的資訊。
keywords: android;library;mobile;sdk
seo-description: 以下提供一些關於透過視訊測量解決方案在 Android 上測量視訊的資訊。
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: 開發人員和實施
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Video Analytics {#video-analytics}

以下提供一些關於透過視訊測量解決方案在 Android 上測量視訊的資訊。

>[!TIP]
>
>在視訊播放期間，會傳送頻繁的「心率」呼叫給此服務，測量播放時間。這些心率呼叫每 10 秒傳送一次，因此可產生精細的視訊參與量度，以及更精確的視訊流失報表。如需Adobe視訊測量解決方案的詳細資訊，請參 [閱在Adobe Analytics中測量音訊和視訊](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)。

所有平台上測量視訊的一般程序都很相似。本內容提供開發人員作業的基本概覽和程式碼範例。下表列出會傳送至 Analytics 的媒體資料。處理規則可用來將上下文資料對應至Analytics變數。

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * 變數類型：eVar
      * 預設過期時間: 造訪
      * Custom Insight (s.prop，用於視訊路徑)
   * (**必要**) 當訪客以某種方式檢視視訊時，這個內容資料變數會按照實施中指定的方式來收集視訊的名稱。您可以新增此變數的分類。
   * (**選用**) Custom Insight 變數可提供視訊路徑資訊。

* **a.media.name**
   * 變數類型：自訂分析(s.prop)
   * (**選用**) 提供視訊路徑資訊。

      >[!IMPORTANT]
      >
      >必須由ExpCare為此變數啟用路徑分析。
   * 事件類型: 自訂分析 (s.prop)

* **a.media.segment**
   * 變數類型：eVar
   * 預設過期時間: 頁面檢視
   * (**必要**) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。

      您可在自動追蹤播放器事件時啟用 `segmentByMilestones` 變數，或在手動追蹤播放器事件時設定自訂區段名稱，藉此填入此變數。例如，當訪客檢視視訊中的第一個區段時，SiteCatalyst 可能會在區段 eVar 中收集以下資訊: `1:M:0-25`.

      預設的視訊資料收集方法會於下列時間點收集資料:

      * 視訊開始 (播放)
      * 區段開始
      * 視訊結束 (停止)
      Analytics 會在區段開始時計算第一個區段檢視，也就是訪客開始觀看的時候。後續的區段檢視會作為區段開始。


* **a.contentType**
   * 變數類型：eVar
   * 預設過期時間: 頁面檢視
   * 收集訪客所檢視內容類型的相關資料。

      視訊測量傳送的點擊會被指派為 `video` 的內容類型。從視訊測量觀點來看，**內容類型**&#x200B;可讓您識別視訊訪客，並據此計算視訊轉換率。

* **a.media.timePlayed**
   * 變數類型：事件
   * 類型: 計數器
   * 計算自上次資料收集程序 (影像要求) 以來，用於觀看視訊的時間 (以秒為單位)。

* **a.media.view**
   * 變數類型：事件
   * 類型: 計數器
   * 指出有訪客檢視了視訊的某部分。

      但此變數並不會提供有關訪客檢視視訊時長或觀看部分的任何資訊。

* **a.media.segmentView**
   * 變數類型：事件
   * 類型: 計數器
   * 指出有訪客檢視了視訊區段的某部分。

      但此變數並不會提供有關訪客檢視視訊時長或觀看部分的任何資訊。

* **a .media.complete**
   * 變數類型：事件
   * 類型: 計數器
   * 指出使用者已檢視完整的視訊。

      預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定要將視訊結束後多久 (以秒計算) 視為檢視完成。若為沒有明確結束時間的即時視訊和其他串流，您可以指定自訂的時間點來測量完成的檢視 (例如在檢視多少特定時間之後)。


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

以您要用來追蹤視訊的設定，設定 `MediaSettings` 物件。

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 舉例來說，當播放器暫停時，需呼叫 `mediaStop`；播放開始或繼續時則是呼叫 `mediaPlay`。

## 類別 {#section_16838332727348F990305C0C6B0D795C}

**類別: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**類別: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

以下是「媒體測量」類別中的方法：

* **settingsWith**

   傳回 `MediaSettings` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。
   * 以下是此方法的語法:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   開啟 `MediaSettings` 物件以供追蹤。

   * 以下是此方法的語法:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      關閉命名為&#x200B;*「名稱」*&#x200B;的媒體項目。

      * 以下是此方法的語法:
      ```java
      public static void close(String name);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.close("name"); 
      ```


* **play**
   * 在指定的&#x200B;*偏移處* (以秒為單位) 播放命名為&#x200B;*「名稱」*&#x200B;的媒體項目。
   * 以下是此方法的語法:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **完成**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 以下是此方法的語法:

      ```java
      public static void complete(String name, double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 以下是此方法的語法:

      ```java
      public static void stop(String name, double offset); 
      ```

   * 以下是程式碼範例或此方法：

      ```java
      Media.stop("name", 0);
      ```

* **click**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```java
      public static void click(String name double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.click("name", 0);
      ```

* **track**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.track("name", null); 
      ```
