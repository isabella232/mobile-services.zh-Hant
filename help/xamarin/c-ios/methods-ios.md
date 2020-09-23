---
description: Experience Cloud解決方案4.x SDK專用Xamarin元件的iOS方法。
keywords: Xamarin
seo-description: Experience Cloud解決方案4.x SDK專用Xamarin元件的iOS方法。
seo-title: iOS方法
solution: Experience Cloud
title: iOS方法
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 70%

---


# iOS方法{#ios-methods}

Experience Cloud解決方案4.x SDK專用Xamarin元件的iOS方法。

## 設定方法 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

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

   將調試記錄首選項設定為啟用。

   * 此方法的語法如下：

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   傳回目前使用者的期限值。

   * 此方法的語法如下：

      ```objective-c
      public static double LifetimeValue();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **隱私權狀態**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `ADBMobilePrivacyStatus.OptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatus.OptOut` – 會捨棄點擊。
   * ADBMobilePrivacyStatus.Unknown —— 如果啟用離線追蹤，會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著會捨棄點擊）為止。 如果離線追蹤已停用，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * 此方法的語法如下：

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

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

* **使用者識別碼**

   如果已設定自訂識別碼，則傳回自訂使用者識別碼。 如果未設定自訂識別碼，則傳回null。 預設值為 `null`。

   * 此方法的語法如下：

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   如果已設定自訂識別碼，則傳回自訂使用者識別碼。 如果未設定自訂識別碼，則傳回null。 預設值為 `null`。

   * 此方法的語法如下：

      ```objective-c
      public static string UserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   取得資料庫版本。

   * 此方法的語法如下：

      ```objective-c
      public static string Version();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive（僅限iOS）**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法適用於在背景中註冊通知的應用程式，且僅應從應用程式在背景時執行的程式碼呼叫此方法。

   * 此方法的語法如下：

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics 方法 {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   擷取分析追蹤識別碼。

   * 此方法的語法如下：

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   使用可選內容資料來追蹤應用程式。狀態是應用程式中可用的檢視，例如「標題畫面」、「層級1」、「暫停」等。 這些狀態類似於網站上的頁面，而呼叫 `TrackState` 會增加頁面檢視次數。如果狀態為空，則會在報表中顯示為「應用程式名稱應用程式版本（組建版本）」。 If you see this value in reports, make sure you are setting state in each `TrackState` call.

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

* **TrackAction**

   追蹤應用程式中的動作。動作是您要測量的應用程式中發生的事，例如「死亡」、「獲得的層級」、「動態消息訂閱」和其他度量。

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

* **TrackActionFromBackground（僅限iOS）**

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

* **TrackLocation**

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

* **TrackBeacon**

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

* **TrackingClearCurrentBeacon**

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

   增加使用者期限值的金額。

   * 此方法的語法如下：

      public nbsp; static voidTrackLifetimeValueIncrease(double amount, NSDictionary cdata);

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

   傳遞資料以更新與指定動作相關的上下文資料。 傳入的資料會附加至指定動作的現有資料，並覆寫資料（如果已為動作定義相同的索引鍵）。

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

   傳回計時動作是否正在進行中。

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

* **TrackingSendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 此方法的程式碼範例如下：

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

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

* **VisitorSyncIdentifiers**

   透過Experience Cloud ID，您可以設定其他客戶ID以與每個訪客建立關聯。 訪客API可接受同一訪客的多個客戶ID，以及客戶類型識別碼，以區隔不同客戶ID的範圍。 此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

   * 此方法的語法如下：

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * 此方法的範例程式碼如下：

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target 方法 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

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

* **TargetCreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * 此方法的語法如下：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   建立 `ADBTargetLocationRequest`。

   * 此方法的語法如下：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

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

* **AudienceVisitorProfile**

   傳回最近取得的訪客描述檔。如果尚未提交任何信號，則返回nil。 Visitor profile is saved in `NSUserDefaults` for easy access across multiple launches of your app.

   * 此方法的語法如下：

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   傳回目前的 DPID。

   * 此方法的語法如下：

      ```objective-c
      public static string AudienceDpid ();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   傳回目前的 DPUUID。

   * 此方法的語法如下：

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   設定dpid和dpuuid。 如果已設定dpid和dpuuid，則會隨每個訊號傳送。

   * 此方法的語法如下：

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

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

* **AudienceReset**

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

如需詳細資訊，請參閱 [視訊分析](/help/ios/getting-started/dev-qs.md)。

* **MediaCreateSettings**

   傳回 `ADBMediaSettings` 物件以及指定的參數。

   * 此方法的語法如下：

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

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

* **MediaClose**

   關閉命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   在指定的偏移處 (以秒為單位) 播放命名為「名稱」的媒體項目。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   在提供的偏移處 (以秒為單位) 手動將媒體項目標示為已完成。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   通知媒體模組，視訊已在指定的偏移處停止或暫停。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   通知媒體模組，媒體項目已被點按。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   傳送目前媒體狀態的追蹤動作呼叫 (無頁面檢視)。

   * 此方法的語法如下：

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
