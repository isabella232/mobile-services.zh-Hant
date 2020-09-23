---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs方法
solution: Experience Cloud
title: ADBMobile.cs方法
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 66%

---


# ADBMobile.cs方法 {#adbmobile-cs-methods}

## 設定方法

* **CollectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void CollectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications（僅限iOS）**

   在您的應用程式中啟用本機通知。

   * 此方法的語法如下：

      ```java
      public static void EnableLocalNotifications();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 此方法的語法如下：

      ```java
      public static bool GetDebugLogging();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   傳回目前使用者的期限值。

   * 此方法的語法如下：

      ```java
      public static double GetLifetimeValue();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果啟用離線追蹤，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著捨棄點擊）為止。

      如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) file.

   * 此方法的語法如下：

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   如果已設定自訂識別碼，則傳回自訂使用者識別碼。 如果未設定自訂識別碼，則傳回null。 預設值為 `null`。

   * 此方法的語法如下：

      ```java
      public static string GetUserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   取得資料庫版本。

   * 此方法的語法如下：

      ```java
      public static string GetVersion();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive（僅限iOS）**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法適用於在背景中註冊通知的應用程式，且僅應從應用程式在背景時執行的程式碼呼叫此方法。

   * 此方法的語法如下：

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData（僅限Android）**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停時會收集時間戳記，以判斷先前的作業長度。 這也會設定旗標，讓生命週期正確知道應用程式未當機。 如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext（僅限Android）**

   向SDK指出應從UnityPlayer的目前活動設定其應用程式內容。

   * 此方法的語法如下：

      ```java
      public static void SetContext();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   將調試記錄首選項設定為啟用。

   * 此方法的語法如下：

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   將當前用戶的隱私狀態設定為狀態。 設定為下列任一值：

   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果啟用離線追蹤，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著捨棄點擊）為止。 如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * 以下是此語法的程式碼範例：

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   將使用者識別碼設為userId。

   * 此方法的語法如下：

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Analytics 方法 

* **GetTrackingIdentifier**

   擷取分析追蹤識別碼。

   * 此方法的語法如下：

      ```java
      public static string GetTrackingIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   使用可選內容資料來追蹤應用程式。狀態是應用程式中可用的檢視，例如「標題畫面」、「層級1」、「暫停」等。 這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。

   如果狀態為空白，則會顯示為報 *`app name app version (build)`* 表中。 If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   追蹤應用程式中的動作。動作是您要測量的應用程式中發生的事，例如「死亡」、「獲得的層級」、「動態消息訂閱」和其他度量。

   >[!TIP]
   >
   >如果您的程式碼會在應用程式於背景時執行 (例如，背景資料擷取)，請改為使用 `trackActionFromBackground`。

   * 此方法的語法如下：

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground（僅限iOS）**

   追蹤在背景發生的動作。在特定情境中抑制生命週期事件地觸發。

   >[!TIP]
   >
   >只有當應用程式在背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 此方法的語法如下：

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   傳送目前的經緯度座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標在已定義的POI中，則會填入內容資料變數，並隨TrackLocation呼叫傳送。

   * 此方法的語法如下：

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   追蹤使用者何時進入信標鄰近地區。

   * 此方法的語法如下：

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 此方法的語法如下：

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   增加使用者期限值的金額。

   * 此方法的語法如下：

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   傳遞資料以更新與指定動作相關的上下文資料。 傳入的資料會附加至指定動作的現有資料，並覆寫資料（如果已為動作定義相同的索引鍵）。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   結束計時動作。

   * 此方法的語法如下：

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   傳回計時動作是否正在進行中。

   * 此方法的語法如下：

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * 此方法的程式碼範例如下：

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 此方法的語法如下：

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackingClearQueue();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 此方法的語法如下：

      ```java
      public static int TrackingGetQueueSize();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience Cloud ID方法

* **GetMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 此方法的語法如下：

      ```java
      public static string GetMarketingCloudID();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   透過Experience Cloud ID，您可以設定其他客戶ID以與每個訪客建立關聯。 訪客API可接受同一訪客的多個客戶ID，以及客戶類型識別碼，以區隔不同客戶ID的範圍。 此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

   * 此方法的語法如下：

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * 此方法的程式碼範例如下：

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## 贏取方法

* **ProcessGooglePlayInstallReferrerUrl** (僅 *限Android)*

   將呼叫Google Play安裝反向連結API所傳回的反向連結URL傳遞至此方法。

   * 此方法的語法如下：

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * 此方法的程式碼範例如下：

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
