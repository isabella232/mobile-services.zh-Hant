---
description: 以下提供一些關於如何透過里程碑視訊測量在 iOS 上測量視訊的資訊。
seo-description: 以下提供一些關於如何透過里程碑視訊測量在 iOS 上測量視訊的資訊。
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: 開發人員和實施
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Video Analytics {#video-analytics}

以下提供一些關於如何透過里程碑視訊測量在 iOS 上測量視訊的資訊。

>[!TIP]
>
>在視訊播放期間，會傳送頻繁的「心率」呼叫給此服務，測量播放時間。這些心率呼叫每 10 秒傳送一次，因此可產生精細的視訊參與量度，以及更精確的視訊流失報表。如需詳細資訊，請參閱[在 Adobe Analytics 中測量音訊和視訊](https://docs.adobe.com/content/help/zh-Hant/media-analytics/using/media-overview.html)。

所有 平台上測量視訊的一般程序都很相似。本內容提供開發人員作業的基本概覽和程式碼範例。

## 將播放器事件對應至 Analytics 變數 {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

下表列出會傳送至 Analytics 的媒體資料。使用處理規則，將內容資料對應至 Analytics 變數。

* **a.media.name**

   (必要) 如實施中所指定，當訪客以某種方式檢視視訊時收集視訊的名稱。您可以新增此變數的分類。

   (選擇性) Custom Insight 變數可提供視訊路徑資訊。

   * 變數類型: eVar
   * 預設過期時間: 造訪
   * Custom Insight (s.prop，用於視訊路徑)

* **a.media.name**

   (選用) 提供視訊路徑資訊。必須由客戶服務中心為此變數啟用路徑。

   * 變數類型: Custom Insight (s.prop)
   * 事件類型: 自訂分析 (s.prop)

* **a.media.segment**

   (必要) 收集視訊區段資料，包括區段名稱和視訊中區段發生的順序。此變數可透過啟用 `segmentByMilestones` 變數，在自動追蹤播放器事件時填入，或透過在手動追蹤播放器事件時設定自訂區段名稱。例如，當訪客檢視視訊中的第一個區段時，SiteCatalyst 可能會在 `1:M:0-25` 區段 eVar 中收集以下資訊。

   預設的視訊資料收集方法會於下列時間點收集資料:

   * 視訊開始 (播放)
   * 區段開始
   * 視訊結束 (停止)
   Analytics 會在區段開始時計算第一個區段檢視，也就是訪客開始觀看的時候。後續的區段檢視會作為區段開始。

   * 變數類型: eVar
   * 預設過期時間: 頁面檢視


* **a.contentType**

   收集訪客所檢視內容類型的相關資料。視訊測量傳送的點擊會被指派為 `video` 的內容類型。不需專為視訊追蹤保留此變數。使用此相同變數而具有其他內容報表內容類型，可讓您分析不同內容類型中訪客的分佈情況。舉例來說，使用了這個變數，您就可以利用像是「article」或「product page」的值來標記其他內容類型。從視訊測量觀點來看，內容類型可讓您識別視訊訪客，並據此計算視訊轉換率。

   * 變數類型: eVar
   * 預設過期時間: 頁面檢視

* **a.media.timePlayed**

   計算自上次資料收集程序 (影像請求) 以來，用於觀看視訊的時間 (以秒為單位)。

   * 變數類型: 事件
   * 類型: 計數器

* **a.media.view**

   指出有訪客檢視了視訊的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型: 事件
   * 類型: 計數器

* **a.media.segmentView**

   指出有訪客檢視了視訊區段的某部分。但此量度並不會針對訪客所檢視的視訊提供任何關於檢視內容的多少、哪一部分的資訊。

   * 變數類型: 事件
   * 類型: 計數器

* **a.media.complete**

   指出使用者已檢視完整的視訊。預設情況下，完成事件會在視訊結尾之前 1 秒測量。實施期間，您可以指定想要將距離視訊結尾幾秒視為檢視完成。若為沒有明確結束時間的即時視訊和其他串流，您可以指定自訂的時間點來測量完成的檢視，例如在檢視多少特定時間之後。

   * 變數類型: 事件
   * 類型: 計數器

## 設定媒體設定 {#section_929945D4183C428AAF3B983EFD3E2500}

以您要用來追蹤視訊的設定，設定 `ADBMediaSettings` 物件。

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## 追蹤播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

若要測量視訊播放，必須在適當時間呼叫 `mediaPlay`、`mediaStop` 以及 `mediaClose` 方法。舉例來說，當播放器暫停時，需呼叫 `mediaStop`。播放開始或繼續時則是呼叫 `mediaPlay`。

下列範例將示範如何設定通知與呼叫媒體方法來測量視訊:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## 類別 {#section_16838332727348F990305C0C6B0D795C}

### 類別: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### 類別: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## 媒體測量類別與方法參考 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   傳回 `ADBMediaSettings` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   傳回 `ADBMediaSettings` 物件以便用於追蹤廣告視訊。

   * 以下是此方法的語法:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   開啟 `ADBMediaSettings` 物件用於追蹤。

   * 以下是此方法的語法:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   關閉命名為&#x200B;*「名稱」*&#x200B;的媒體項目。

   * 以下是此方法的語法:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   在指定的&#x200B;*偏移處* (以秒為單位) 播放命名為&#x200B;*「名稱」*&#x200B;的媒體項目。

   * 以下是此方法的語法:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   在提供的&#x200B;*偏移處* (以秒為單位) 手動將媒體項目標示為已完成。

   * 以下是此方法的語法:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   通知媒體模組，視訊已在指定的&#x200B;*偏移處*&#x200B;停止或暫停。

   * 以下是此方法的語法:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```

