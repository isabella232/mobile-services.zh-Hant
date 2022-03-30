---
description: ADBMobile.cs配置方法
keywords: Unity
solution: Experience Cloud Services
title: ADBMobile.cs 方法
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
exl-id: d12c16f1-c25c-4698-8943-a660d9c08faf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 66%

---

# ADBMobile.cs 方法 {#adbmobile-cs-methods}

## 設定方法

* **收集生命週期資料**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void CollectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications(僅iOS)**

   在應用中啟用本地通知。

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

* **獲取隱私狀態**

   傳回目前使用者之隱私權狀態的列舉表示法。
   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果啟用離線跟蹤，則會保存命中，直到隱私狀態更改為opt-in（然後發送命中）或opt-out（然後丟棄命中）。

      如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值在 [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) 的子菜單。

   * 此方法的語法如下：

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **獲取用戶標識符**

   如果已設定自定義標識符，則返回自定義用戶標識符。 如果未設定自定義標識符，則返回Null。 預設值為 `null`。

   * 此方法的語法如下：

      ```java
      public static string GetUserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **獲取版本**

   取得資料庫版本。

   * 此方法的語法如下：

      ```java
      public static string GetVersion();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive(僅限iOS)**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!TIP]
   >
   >此方法用於在後台註冊通知的應用，並且只應從在後台運行的代碼調用。

   * 此方法的語法如下：

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectionLifecycleData（僅Android）**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停時收集時間戳以確定上一個會話長度。 這還設定了一個標誌，這樣生命週期就能正確知道應用程式沒有崩潰。 如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext（僅Android）**

   向SDK指示它應從UnityPlayer的當前活動中設定其應用程式上下文。

   * 此方法的語法如下：

      ```java
      public static void SetContext();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   將調試日誌記錄首選項設定為已啟用。

   * 此方法的語法如下：

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **設定隱私狀態**

   將當前用戶的隱私狀態設定為狀態。 設定為下列任一值：

   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果啟用離線跟蹤，則會保存命中，直到隱私狀態更改為opt-in（然後發送命中）或opt-out（然後丟棄命中）。 如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * 以下是此語法的代碼示例：

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **設定用戶標識符**

   將用戶標識符設定為userId。

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

* **跟蹤狀態**

   使用可選內容資料來追蹤應用程式。狀態是您應用中可用的視圖，如「標題螢幕」、「級別1」、「暫停」等。 這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。

   如果狀態為空，則顯示為 *`app name app version (build)`* 的子菜單。 如果在報表中看到此值，請確保在每個報表中都設定狀態 `TrackState` 呼叫。

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

* **跟蹤操作**

   追蹤應用程式中的動作。操作是您想要衡量的應用程式中發生的情況，如「死亡」、「獲得的水準」、「訂閱源」和其他指標。

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

* **TrackActionFromBackground(僅iOS)**

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

* **跟蹤位置**

   傳送目前的經緯度座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果當前坐標在定義的POI內，則會填充上下文資料變數並隨TrackLocation調用一起發送。

   * 此方法的語法如下：

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **跟蹤信標**

   追蹤使用者何時進入信標鄰近地區。

   * 此方法的語法如下：

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **跟蹤清除當前信標**

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

   將金額添加到用戶的生存期值。

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

   傳入資料以更新與給定操作關聯的上下文資料。 傳入的資料將附加到給定操作的現有資料中，並在已為操作定義了相同的鍵時覆蓋資料。

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

* **跟蹤SendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 此方法的語法如下：

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **跟蹤ClearQueue**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```java
      public static void TrackingClearQueue();
      ```

   * 此方法的程式碼範例如下：

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **跟蹤GetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 此方法的語法如下：

      ```java
      public static int TrackingGetQueueSize();
      ```

   * 此方法的程式碼範例如下：

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience CloudID方法

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

* **訪問者同步標識符**

   使用Experience CloudID，您可以設定附加的客戶ID以與每個訪問者關聯。 訪問者API為同一訪問者接受多個客戶ID，並使用客戶類型標識符來分隔不同客戶ID的範圍。 此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

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

* **ProcessGooglePlayInstallReferrerUrl** *（僅限Android）*

   將從調用返回的引用者URL傳遞到Google Play安裝引用者API到此方法。

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
