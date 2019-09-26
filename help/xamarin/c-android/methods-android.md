---
description: 適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件的 Android 方法
keywords: Xamarin
seo-description: 適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件的 Android 方法
seo-title: Android方法
solution: Marketing Cloud，開發人員
title: Android方法
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

適用於 Experience Cloud 解決方案 4.x SDK 的 Xamarin 元件的 Android 方法

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   傳回目前的除錯記錄偏好設定，預設值為false。

   * 以下是此方法的語法:

      ```java
      public static Boolean DebugLogging;
      ```

   * 以下是此方法的範例程式碼:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   傳回目前使用者的期限值。

   * 以下是此方法的語法:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * 以下是此方法的範例程式碼:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `ADBMobilePrivacyStatus.OptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatus.OptOut` - hits are discarded.
   * `ADBMobilePrivacyStatus.Unknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   預設值設定在 [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) 檔案中。

   * 以下是此方法的語法:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   如果已設定自訂識別碼，請傳回此識別碼。 如果未設定自訂識別碼，則傳回null。 預設值為 `null`。

   * 以下是此方法的語法:

      ```java
      public static UserIdentifier();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **版本**

   取得資料庫版本。

   * 以下是此方法的語法:

      ```java
      public static string Version;
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期正確得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity activity)**

   (4.2 或更新版本) 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity activity)**

   (4.2 或更新版本) 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * 以下是此方法的範例程式碼:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. 應用程式會使用另一個設定，直到關閉為止。

   * 以下是此方法的語法:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   （4.2或更新版本）設定用於SDK所建立通知的大型圖示。 此圖示是當使用者在通知中心看到完整通知時所顯示的主要影像。

   * 以下是此方法的語法:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   （4.2或更新版本）設定用於SDK所建立通知的小型圖示。 此圖示會顯示在狀態列中，是當使用者在通知中心看到完整通知時顯示的次要影像。

   * 以下是此方法的語法:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   傳回自動產生的 Analytics ID。這是應用程式專屬的唯一ID，會在初始啟動時產生，並會從此時開始儲存和使用。 此ID會在應用程式升級時保留，並在解除安裝時移除。

   * 以下是此方法的語法:

      ```java
      public static string TrackingIdentifier;
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   使用可選內容資料來追蹤應用程式。`States`為應用程式中可用的檢視，例如 "title screen"、"level 1"、"pause" 等。這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。如果狀態空白，在報表中會顯示為「應用程式名稱 應用程式版本 (組建)」。如果在報表中看到此值，請務必在每個 `TrackState` 呼叫中設定 state。

   >[!TIP]
   >
   >這是唯一會增加頁面檢視次數的追蹤呼叫。

   * 以下是此方法的語法:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   追蹤應用程式中的動作。動作是發生在應用程式中而且您想測量的項目，例如「死亡」、「獲得的層級」、「饋送訂閱」以及其他度量。

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 以下是此方法的語法:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   傳送目前的經緯度座標。Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. 如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `TrackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   追蹤使用者何時進入信標鄰近地區。

   * 以下是此方法的語法:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 以下是此方法的語法:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   增加使用者期限值的量。

   * 以下是此方法的語法:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   > 此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Here is code sample for this method:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   傳遞資料以更新與指定動作關聯的內容資料。傳遞的資料會附加至特定動作的現有資料，如果已為動作定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   結束計時動作。

   * 以下是此方法的語法:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * 以下是此方法的範例程式碼:

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

   * 以下是此方法的語法:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Forces the library to send all hits in the offline queue, regardless of how many hits are currently queued.

   * 以下是此方法的語法:

      ```java
      public static void SendQueuedHits();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   清除離線佇列中的所有點擊。

   * 以下是此方法的語法:

      ```java
      public static void ClearQueue(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   擷取離線佇列中目前的點擊數。

   * 以下是此方法的語法:

      ```java
      public static long QueueSize(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   從 ID 服務中擷取 Experience Cloud ID。

   * 以下是此方法的語法:

      ```java
      public static string MarketingCloudId;
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   透過 Experience Cloud ID，您可以設定額外的客戶 ID 來與每個訪客產生關聯。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 以下是此方法的語法:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target methods {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * 以下是此方法的語法:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * 以下是此方法的範例程式碼:

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

* **CreateRequest**

   方便讓建構函式使用指定的參數來建立 `ADBTargetLocationRequest` 物件。

   * 以下是此方法的語法:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   建立 `ADBTargetLocationRequest`。

   * 以下是此方法的語法:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   清除應用程式中的Target Cookie。

   * 以下是此方法的語法:

      ```java
      public static void ClearCookies(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   傳回最近取得的訪客描述檔。如果尚未提交任何信號則傳回 nil。訪客設定檔會儲存在 `NSUserDefaults` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * 以下是此方法的語法:

      ```java
      public static string Dpuuid; 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * 以下是此方法的語法:

      ```java
      public static string AudienceDpuuid; 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   設定 `dpid` 和 `dpuuid`。 If `dpid` and `dpuuid` are set, they are sent with each signal.

   * 以下是此方法的語法:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * 以下是此方法的語法:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * 以下是此方法的範例程式碼:

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

   重設觀眾管理員 `UUID` 並清除目前的訪客描述檔。

   * 以下是此方法的語法:

      ```java
      public static void Reset ();
      ```

   * 以下是此方法的範例程式碼:

      ```java
       AudienceManager.Reset ();
      ```

## 影片 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

如需視訊分析的詳細資訊，請參閱視 [訊分析](/help/android/analytics-main/video-qs.md)。

* **MediaSettings**

   傳回 `MediaSettings` 物件以及指定的參數。

   * 以下是此方法的語法:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * 以下是此方法的範例程式碼:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   傳回 `MediaSettings` 物件以便用於追蹤廣告視訊。

   * 以下是此方法的語法:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **開啟**

   開啟 `ADBMediaSettings` 物件用於追蹤。

   * 以下是此方法的語法:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Close**

   關閉媒體項目具名名稱。

   * 以下是此方法的語法:

      ```java
      public static void Close(string name);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Close (settings.Name); 
      ```

* **播放**

   在指定的偏移處 (以秒為單位) 播放媒體項目具名名稱。

   * 以下是此方法的語法:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **完成**

   在提供的偏移處 (以秒為單位) 手動標示媒體項目為已完成。

   * 以下是此方法的語法:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   通知媒體模組，視訊已在指定的偏移處停止或暫停。

   * 以下是此方法的語法:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **按一下**

   通知媒體模組，媒體項目已被點按。

   * 以下是此方法的語法:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **追蹤**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 以下是此方法的語法:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Media.Track (settings.Name, null); 
      ```
