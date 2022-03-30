---
description: Android方法，用於Experience Cloud解決方案4.x SDK的Xamarin元件。
keywords: 沙馬林
solution: Experience Cloud Services
title: Android 方法
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Android 方法{#android-methods}

Android方法，用於Experience Cloud解決方案4.x SDK的Xamarin元件。

## 設定方法 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   返回當前調試日誌記錄首選項，預設值為false。

   * 此方法的語法如下：

      ```java
      public static Boolean DebugLogging;
      ```

   * 此方法的程式碼範例如下：

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **生存期值**

   傳回目前使用者的期限值。

   * 此方法的語法如下：

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * 此方法的程式碼範例如下：

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `ADBMobilePrivacyStatus.OptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatus.OptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatus.Unknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   預設值在 [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) 的子菜單。

   * 此方法的語法如下：

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * 此方法的程式碼範例如下：

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **用戶標識符**

   如果已設定自定義標識符，則返回此標識符。 如果未設定自定義標識符，則返回null。 預設值為 `null`。

   * 此方法的語法如下：

      ```java
      public static UserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **版本**

   取得資料庫版本。

   * 此方法的語法如下：

      ```java
      public static string Version;
      ```

   * 此方法的程式碼範例如下：

      ```java
      var version = ADBMobile.Version;
      ```

* **暫停收集生命週期資料**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停時收集時間戳以確定上一個會話長度。 這還設定了一個標誌，這樣生命週期就能正確知道應用程式沒有崩潰。 如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData（活動活動）**

   （4.2或更高版本）向SDK表示應收集生命週期資料，以便在SDK中的所有解決方案中使用。 如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData（活動活動）**

   （4.2或更高版本）向SDK表示應收集生命週期資料，以便在SDK中的所有解決方案中使用。 如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * 此方法的程式碼範例如下：

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **覆蓋配置流**

   （4.2或更高版本）用於載入其他 `ADBMobile JSON` 應用程式啟動時配置檔案。 應用程式會使用另一個設定，直到關閉為止。

   * 此方法的語法如下：

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   （4.2或更高版本）設定用於SDK建立的通知的大表徵圖。 此圖示是使用者在通知中心查看完整通知時所顯示的主要影像。

   * 以下是此方法的語法:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   （4.2或更高版本）設定用於SDK建立的通知的小表徵圖。 此表徵圖顯示在狀態欄中，是當用戶在通知中心看到完整通知時顯示的次映像。

   * 此方法的語法如下：

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * 此方法的程式碼範例如下：

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics 方法  {#section_63CF636104EF41F790C3E4190D755BBA}

* **跟蹤標識符**

   返回自動生成的分析ID。 這是應用程式特定的唯一ID，在初始啟動時生成，並從該點向前儲存和使用。 此ID將在應用程式升級之間保留，並在卸載時刪除。

   * 此方法的語法如下：

      ```java
      public static string TrackingIdentifier;
      ```

   * 此方法的程式碼範例如下：

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **跟蹤狀態**

   使用可選內容資料來追蹤應用程式。`States` 是應用程式中可用的視圖，如「標題螢幕」、「級別1」、「暫停」等。 這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。如果狀態為空，則它在報告中顯示為「應用名稱應用版本（內部版本）」。 如果在報表中看到此值，請確保在每個報表中都設定狀態 `TrackState` 呼叫。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **跟蹤操作**

   追蹤應用程式中的動作。操作是您想要衡量的應用程式中發生的情況，如「死亡」、「獲得的水準」、「訂閱源」和其他指標。

   >[!TIP]
   >
   >
   >如果您的程式碼會在應用程式於背景時執行 (例如，背景資料擷取)，請改為使用 `trackActionFromBackground`。

   * 此方法的語法如下：

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **跟蹤位置**

   傳送目前的經緯度座標。還使用在 `ADBMobileConfig.json` 檔案，以確定作為參數提供的位置是否位於任何POI中。 如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `TrackLocation` 呼叫一併傳送。

   * 此方法的語法如下：

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **跟蹤信標**

   追蹤使用者何時進入信標鄰近地區。

   * 此方法的語法如下：

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **清除信標**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 此方法的語法如下：

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   增加使用者期限值的量。

   * 此方法的語法如下：

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   > 此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   傳遞資料以更新與指定動作關聯的內容資料。傳入的資料將附加到給定操作的現有資料中，並在已為操作定義了相同的鍵時覆蓋資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   結束計時動作。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   傳回計時動作是否正在進行中。

   * 此方法的語法如下：

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **發送排隊命中數**

   強制庫發送離線隊列中的所有命中，而不管當前排隊的命中數是多少。

   * 此方法的語法如下：

      ```java
      public static void SendQueuedHits();
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **清除隊列**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```java
      public static void ClearQueue(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Analytics.ClearQueue(); 
      ```

* **隊列大小**

   檢索當前在離線隊列中的命中數。

   * 此方法的語法如下：

      ```java
      public static long QueueSize(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience CloudID方法 {#section_157919E46030443DBB5CED60D656AD9F}

* **營銷雲ID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 此方法的語法如下：

      ```java
      public static string MarketingCloudId;
      ```

   * 此方法的程式碼範例如下：

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **同步標識符**

   使用Experience CloudID，您可以設定附加的客戶ID以與每個訪問者關聯。 訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 此方法的語法如下：

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * 此方法的程式碼範例如下：

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target 方法 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **載入請求**

   將請求發送到已配置的目標伺服器並返回在 `Action<NSDictionary>` 回叫。

   * 此方法的語法如下：

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **建立請求**

   建立方便的建構子 `ADBTargetLocationRequest` 對象。

   * 此方法的語法如下：

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **建立訂單確認請求**

   建立 `ADBTargetLocationRequest`。

   * 此方法的語法如下：

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * 此方法的程式碼範例如下：

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **清除Cookie**

   清除應用中的目標Cookie。

   * 此方法的語法如下：

      ```java
      public static void ClearCookies(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **訪問者配置檔案**

   傳回最近取得的訪客描述檔。如果尚未提交任何信號，則返回零。 訪客設定檔會儲存在 `NSUserDefaults` 中，方便您在多次啟動應用程式時存取。

   * 此方法的語法如下：

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * 此方法的程式碼範例如下：

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   返回當前 `DPID`。

   * 此方法的語法如下：

      ```java
      public static string Dpuuid; 
      ```

   * 此方法的程式碼範例如下：

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **德普伊德**

   返回當前 `DPUUID`。

   * 此方法的語法如下：

      ```java
      public static string AudienceDpuuid; 
      ```

   * 此方法的程式碼範例如下：

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **受眾集DpidAndDpuuid**

   設定 `dpid` 和 `dpuuid`。 如果 `dpid` 和 `dpuuid` 設定，並隨信號一起發送。

   * 此方法的語法如下：

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * 此方法的程式碼範例如下：

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **信號與資料**

   向受眾管理發送具有特徵的信號，並獲取在 `Action<NSDictionary>` 回叫。

   * 此方法的語法如下：

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **重設**

   重置受眾管理器 `UUID` 並清除當前訪客的檔案。

   * 此方法的語法如下：

      ```java
      public static void Reset ();
      ```

   * 此方法的程式碼範例如下：

      ```java
       AudienceManager.Reset ();
      ```

## 影片 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

有關視頻分析的詳細資訊，請參見 [視頻分析](/help/android/analytics-main/video-qs.md)。

* **媒體設定**

   傳回 `MediaSettings` 物件以及指定的參數。

   * 此方法的語法如下：

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * 此方法的程式碼範例如下：

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **廣告設定**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 此方法的語法如下：

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **開啟**

   開啟 `ADBMediaSettings` 物件用於追蹤。

   * 此方法的語法如下：

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * 此方法的程式碼範例如下：

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **關閉**

   關閉命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```java
      public static void Close(string name);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Close (settings.Name); 
      ```

* **播放**

   在指定的偏移處 (以秒為單位) 播放命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```java
      public static void Play ( string name, double offset); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **完成**

   在提供的偏移處 (以秒為單位) 手動將媒體項目標示為已完成。

   * 此方法的語法如下：

      ```java
      public static void Complete (string name, double offset); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **停止**

   通知媒體模組，視訊已在指定的偏移處停止或暫停。

   * 此方法的語法如下：

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **按一下**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```java
      public static void Click ( string name, double offset); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **跟蹤**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Media.Track (settings.Name, null); 
      ```
