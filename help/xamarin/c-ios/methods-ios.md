---
description: iOS方法，用於Experience Cloud解決方案4.x SDK的Xamarin元件。
keywords: 沙馬林
solution: Experience Cloud Services
title: iOS 方法
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
exl-id: 92897d08-2b66-4688-9870-c877bea53cfc
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 70%

---

# iOS 方法{#ios-methods}

iOS方法，用於Experience Cloud解決方案4.x SDK的Xamarin元件。

## 設定方法 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **收集生命週期資料**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   * 此方法的語法如下：

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 此方法的語法如下：

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   將調試日誌記錄首選項設定為已啟用。

   * 此方法的語法如下：

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **生存期值**

   傳回目前使用者的期限值。

   * 此方法的語法如下：

      ```objective-c
      public static double LifetimeValue();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `ADBMobilePrivacyStatus.OptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatus.OptOut` – 會捨棄點擊。
   * ADBMobilePrivacyStatus.Unknown — 如果啟用離線跟蹤，則會保存命中，直到隱私狀態更改為opt-in（然後發送命中）或opt-out（然後丟棄命中）。 如果禁用離線跟蹤，則在隱私狀態更改為選擇加入之前，將丟棄命中。

   預設值在 [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md)。

   * 此方法的語法如下：

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **設定隱私狀態**

   將當前用戶的隱私狀態設定為狀態。 設定為下列其中一值：
   * `ADBMobilePrivacyStatus.OptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatus.OptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatus.Unknown` – 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **用戶標識符**

   如果已設定自定義標識符，則返回自定義用戶標識符。 如果未設定自定義標識符，則返回Null。 預設值為 `null`。

   * 此方法的語法如下：

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **設定用戶標識符**

   如果已設定自定義標識符，則返回自定義用戶標識符。 如果未設定自定義標識符，則返回Null。 預設值為 `null`。

   * 此方法的語法如下：

      ```objective-c
      public static string UserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier"); 
      ```

* **獲取版本**

   取得資料庫版本。

   * 此方法的語法如下：

      ```objective-c
      public static string Version();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive(僅限iOS)**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法用於在後台註冊通知的應用，並且只應從在後台運行的代碼調用。

   * 此方法的語法如下：

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics 方法  {#section_63CF636104EF41F790C3E4190D755BBA}

* **跟蹤標識符**

   擷取分析追蹤識別碼。

   * 此方法的語法如下：

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **跟蹤狀態**

   使用可選內容資料來追蹤應用程式。狀態是您應用中可用的視圖，如「標題螢幕」、「級別1」、「暫停」等。 這些狀態類似於網站上的頁面， `TrackState` 調用增量頁面視圖。如果狀態為空，則在報表中顯示為「應用程式名稱應用版本（內部版本）」。 如果在報表中看到此值，請確保在每個報表中都設定狀態 `TrackState` 呼叫。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **跟蹤操作**

   追蹤應用程式中的動作。操作是您想要衡量的應用程式中發生的情況，如「死亡」、「獲得的水準」、「訂閱源」和其他指標。

   >[!TIP]
   >
   >如果您的程式碼會在應用程式於背景時執行 (例如，背景資料擷取)，請改為使用 `trackActionFromBackground`。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground(僅iOS)**

   追蹤在背景發生的動作。在特定情境中抑制生命週期事件地觸發。

   >[!TIP]
   >
   > 只有當應用程式在背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **跟蹤位置**

   傳送目前的經緯度座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `TrackLocation` 呼叫一併傳送。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **跟蹤信標**

   追蹤使用者何時進入信標鄰近地區。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **跟蹤清除當前信標**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   將金額添加到用戶的生存期值。

   * 此方法的語法如下：

      公共nbsp；靜態voidTrackLifetimeValueIncrease（雙量，NSDictionary）;

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   傳入資料以更新與給定操作關聯的上下文資料。 傳入的資料將附加到給定操作的現有資料中，並在已為操作定義了相同的鍵時覆蓋資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   結束計時動作。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   返回是否正在執行（或未執行）定時操作。

   * 此方法的語法如下：

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **跟蹤SendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **跟蹤ClearQueue**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **跟蹤GetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 此方法的程式碼範例如下：

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience CloudID方法 {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 此方法的語法如下：

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **訪問者同步標識符**

   使用Experience CloudID，您可以設定附加的客戶ID以與每個訪問者關聯。 訪問者API為同一訪問者接受多個客戶ID，並使用客戶類型標識符來分隔不同客戶ID的範圍。 此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

   * 此方法的語法如下：

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target 方法 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **目標載入請求**

   將請求發送到已配置的目標伺服器並返回在 `Action<NSDictionary>` 回叫。

   * 此方法的語法如下：

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **目標建立請求**

   建立方便的建構子 `ADBTargetLocationRequest` 對象。

   * 此方法的語法如下：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **目標建立訂單確認請求**

   建立 `ADBTargetLocationRequest`。

   * 此方法的語法如下：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **目標清除Cookie**

   清除應用程式中的目標 Cookie。

   * 此方法的語法如下：

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **受眾訪問者個人資料**

   傳回最近取得的訪客描述檔。如果尚未提交任何信號，則返回零。 訪問者配置檔案保存在 `NSUserDefaults` 可輕鬆訪問多個應用程式。

   * 此方法的語法如下：

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **觀眾**

   傳回目前的 DPID。

   * 此方法的語法如下：

      ```objective-c
      public static string AudienceDpid ();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **觀眾數**

   傳回目前的 DPUUID。

   * 此方法的語法如下：

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **受眾集DpidAndDpuuid**

   設定dpid和dpuuid。 如果設定了dpid和dpuuid ，則將隨每個信號一起發送。

   * 此方法的語法如下：

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **受眾信號與資料**

   向受眾管理發送具有特徵的信號，並獲取在 `Action<NSDictionary>`  回叫。

   * 此方法的語法如下：

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **受眾重置**

   重設觀眾管理員 UUID 並清除目前的訪客描述檔。

   * 此方法的語法如下：

      ```objective-c
      public static void AudienceReset ();
      ```

   * 此方法的語法如下：

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## 影片 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

有關詳細資訊，請參見 [視頻分析](/help/ios/getting-started/dev-qs.md)。

* **媒體建立設定**

   傳回 `ADBMediaSettings` 物件以及指定的參數。

   * 此方法的語法如下：

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **媒體廣告建立設定**

   傳回 `ADBMediaSettings` 物件以便用於追蹤廣告視訊。

   * 此方法的語法如下：

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   開啟 `ADBMediaSettings` 物件用於追蹤。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **媒體關閉**

   關閉命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **媒體播放**

   在指定的偏移處 (以秒為單位) 播放命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **媒體完成**

   在提供的偏移處 (以秒為單位) 手動將媒體項目標示為已完成。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **媒體停止**

   通知媒體模組，視訊已在指定的偏移處停止或暫停。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **媒體按一下**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **媒體跟蹤**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
