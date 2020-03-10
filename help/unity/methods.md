---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs方法
solution: Marketing Cloud,Developer
title: ADBMobile.cs方法
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## 設定方法

* **CollectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void CollectLifecycleData();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications (僅限 iOS)**

   在應用程式中啟用本機通知。

   * 以下是此方法的語法：

      ```java
      public static void EnableLocalNotifications();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 以下是此方法的語法：

      ```java
      public static bool GetDebugLogging();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   傳回目前使用者的期限值。

   * 以下是此方法的語法：

      ```java
      public static double GetLifetimeValue();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: 會立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: 會捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) 檔案中。

   * 以下是此方法的語法：

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   如果有設定自訂識別碼，傳回自訂使用者識別碼。如果未設定自訂識別碼，則傳回 null。預設值為 `null`。

   * 以下是此方法的語法：

      ```java
      public static string GetUserIdentifier();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   取得資料庫版本。

   * 以下是此方法的語法：

      ```java
      public static string GetVersion();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (僅限 iOS)**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法適用於在背景中註冊通知的應用程式，且僅應從應用程式在背景時執行的程式碼呼叫此方法。

   * 以下是此方法的語法：

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (僅限 Android)**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期正確得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (僅限 Android)**

   向 SDK 指出應從 UnityPlayer 的目前活動設定 SDK 的應用程式內容.

   * 以下是此方法的語法：

      ```java
      public static void SetContext();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   設定偵錯記錄偏好設定為啟用。

   * 以下是此方法的語法：

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   設定目前使用者的隱私權狀態為 status。設定為下列其中一值：

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: 會立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: 會捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法：

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * 以下是此語法的程式碼範例：

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   設定使用者識別碼為 userId。

   * 以下是此方法的語法：

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Analytics 方法 

* **GetTrackingIdentifier**

   擷取分析追蹤識別碼。

   * 以下是此方法的語法:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視，例如 &quot;title screen&quot;、&quot;level 1&quot;、&quot;pause&quot; 等。這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。

   If state is empty, it displays as *`app name app version (build)`* in reports. 如果在報表中看到此值，請務必在每個 `TrackState` 呼叫中設定 state。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 以下是此方法的語法：

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   追蹤應用程式中的動作。動作是發生在應用程式中而且您想測量的項目，例如「死亡」、「獲得的層級」、「饋送訂閱」以及其他度量。

   >[!TIP]
   >
   >如果您的程式碼會在應用程式於背景時執行 (例如，背景資料擷取)，請改為使用 `trackActionFromBackground`。

   * 以下是此方法的語法:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (僅限 iOS)**

   追蹤背景發生的動作。如此會在某些情況下阻止觸發生命週期事件。

   >[!TIP]
   >
   >只有當應用程式在背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 以下是此方法的語法:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   傳送目前的經緯度座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並以 TrackLocation 呼叫傳送。

   * 以下是此方法的語法：

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   追蹤使用者何時進入信標鄰近地區。

   * 以下是此方法的語法:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 以下是此方法的語法:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   增加使用者期限值的量。

   * 以下是此方法的語法：

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   傳遞資料以更新與特定動作關聯的內容資料。傳遞的資料會附加至特定動作的現有資料，如果已為動作定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   結束計時動作。

   * 以下是此方法的語法：

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   傳回計時動作是否正在進行中。

   * 以下是此方法的語法：

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * 以下是此方法的範例程式碼：

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 以下是此方法的語法：

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   清除離線佇列中的所有點擊。

   * 以下是此方法的語法：

      ```java
      public static void TrackingClearQueue();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 以下是此方法的語法：

      ```java
      public static int TrackingGetQueueSize();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience Cloud ID方法

* **GetMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 以下是此方法的語法：

      ```java
      public static string GetMarketingCloudID();
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   透過 Experience Cloud ID，您可以設定額外的客戶 ID 來與每個訪客產生關聯。訪客 API 可接受同一名訪客的多個客戶 ID，以及用來區分不同客戶 ID 之範圍的客戶類型識別碼。此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

   * 以下是此方法的語法：

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * 以下是此方法的範例程式碼：

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## 贏取方法

* **ProcessGooglePlayInstallReferrerUrl** (僅 *限Android)*

   將呼叫Google Play安裝反向連結API所傳回的反向連結URL傳遞至此方法。

   * 以下是此方法的語法：

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
