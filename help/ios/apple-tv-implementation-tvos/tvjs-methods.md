---
description: 以下為 tvOS 資料庫所提供的 TVJS 方法清單。
seo-description: 以下為 tvOS 資料庫所提供的 TVJS 方法清單。
seo-title: TVJS 方法
solution: Marketing Cloud,Analytics
title: TVJS 方法
topic: 開發人員和實施
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS 方法 {#tvjs-methods}

以下為 tvOS 資料庫所提供的 TVJS 方法清單。

## 設定方法 {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **版本**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 以下是此方法的語法:

      ```objective-c
      version()
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * 傳回: `String`

* **privacyStatus**

   傳回目前使用者之隱私權狀態列舉的 NSUInteger 表示法。

   選項如下:

   * `ADBMobilePrivacyStatusOptIn`: 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut`: 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown`: 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 以下是此方法的語法:

      ```objective-c
      privacyStatus()
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * 傳回: `Number`

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為下列其中一個值:

   * `ADBMobilePrivacyStatusOptIn`: 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut`: 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown`: 如果已啟用離線追蹤，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。
   如果沒有啟用離線追蹤，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   傳回目前使用者的期限值。預設值為 `0`。

   * 以下是此方法的語法:

      ```objective-c
      lifetimeValue()
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * 傳回: `Number`

* **userIdentifier**

   如果已設定自訂識別碼，則傳回使用者識別碼。如果未設定自訂識別碼，則傳回 nil。預設值為 `nil`.

   >[!IMPORTANT]
   >
   >如果您的應用程式從 Experience Cloud 3.x 升級至 4.x SDK，應用程式會擷取先前的訪客 ID (自訂或自動產生) 並將其儲存為自訂使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 nil，直到設定完成為止。

   * 以下是此方法的語法:

      ```objective-c
      userIdentifier()
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * 傳回: `String`

* **setUserIdentifier**

   設定使用者識別碼。

   * 以下是此方法的語法:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * 傳回: N/A

   * 參數:  `userID`

      * 類型: 字串
      * 該使用者的新識別碼。

* **setAdvertisingIdentifier**

   在 SDK 中設定 IDFA；若已在 SDK 中設定 IDFA，則 IDFA 會在生命週期中傳送。您亦可在「訊號」(回傳) 中存取 IDFA。

   >[!IMPORTANT]
   >
   >只有在您使用廣告服務時，才能從 Apple API 擷取 IDFA。若您擷取了 IDFA 卻不當使用，您的應用程式可能會遭到拒絕。

   * 以下是此方法的語法:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * 傳回: N/A
   * 參數: `idfa`
      * 類型: `String`
      * 從 Apple API 擷取的 IDFA。

* **setDebugLogging**

   設定偵錯記錄偏好設定。

   * 以下是此方法的語法:

      ```objective-c
      setDebugLogging(logging)
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * 傳回: N/A
   * 參數: `logging`
      * 類型: `Bool`
      * 表示 Adobe SDK 是否應記錄至偵錯主控台的值。


## Analytics 方法 {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視 (例如首頁儀表板、應用程式設定和購物車等)。這些狀態類似於網站上的頁面，且 trackState 呼叫會遞增頁面檢視。

   如果狀態空白，在報表中會顯示為 app name app version (build)。如果在報表中看到此值，請務必在每個 trackState 呼叫中設定狀態。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 以下是此方法的語法:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * 傳回: N/A
      * 參數: `stateName`
         * 類型: `String`
         * 頁面狀態名稱
      * 參數: `contextData`
         * 類型: 物件
         * 此點擊的其他內容資料。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   追蹤應用程式中的動作。動作是發生在應用程式中而且您想測量的項目，例如「登入」、「橫幅點選」、「摘要訂閱」以及其他量度。

   * 以下是此方法的語法:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * 傳回: N/A
      * 參數: `actionName`
         * 類型: 字串
         * 正在追蹤的動作名稱。
      * 參數: `contextData`
         * 類型: 物件
         * 此點擊的其他內容資料。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   傳送目前的經緯度座標。

   也會使用 `ADBMobileConfig.json` 檔案中定義的地標 (POI)，來判斷輸入做為參數的位置是否在您的任何 POI 範圍內。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * 傳回: N/A
      * 參數: `lat`
         * 類型: 數字
         * 位置的緯度。
      * 參數: `lon`
         * 類型: 數字
         * 位置的經度。
      * 參數: `contextData`
         * 類型: 物件
         * 此點擊的其他內容資料。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   增加使用者期限值的量。

   * 以下是此方法的語法:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * 傳回: N/A
      * 參數: `increaseAmount`
         * 類型: 數字
         * 要增加至使用者目前期限值的量。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   以名稱動作啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * 傳回: N/A
      * 參數: `name`
         * 類型: 字串
         * 即將開始的計時動作名稱。
      * 參數: `contextData`
         * 類型: 物件
         * 此點擊的其他內容資料。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   傳遞資料以更新與指定動作關聯的內容資料。

   傳遞的資料會附加至指定動作的現有資料，如果已為動作定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * 傳回: N/A
      * 參數: `name`
         * 類型: 字串
         * 即將更新的計時動作名稱。
      * 參數: `contextData`
         * 類型: 物件
         * 此點擊的其他內容資料。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   結束計時動作。

   如果您提供回撥函式，則可以存取最終時間值。如果沒有提供回撥，或回撥傳回 true，則 Adobe SDK 會自動傳送點擊。若從回撥傳回 false，則會抑制計時動作點擊。

   * 以下是此方法的語法:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * 傳回: N/A
      * 參數: `name`
         * 類型: 字串
         * 即將結束的計時動作名稱。
      * 參數: `callback`
         * 類型: `function(inAppDuration, totalDuration, data)`
         * 回撥方法的參數會有: `inAppDuration` (數字)、`totalDuration` (數字) 及 `data` (內容資料物件)。

            您可以在回撥函式中傳回 `false`，藉此防止 SDK 傳送最終點擊。
      * 以下是此方法的範例程式碼:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   傳回計時動作是否正在進行中。

   * 以下是此方法的語法:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * 傳回: 布林值
      * 參數: `name`
         * 類型: `String`
         * 您需要檢查是否存在的計時動作名稱。
   * 以下是此方法的範例程式碼:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   傳回自動產生的訪客識別碼。

   這是由 Adobe 伺服器所產生的應用程式專屬唯一訪客 ID。如果產生 ID 時無法連線至 Adobe 伺服器，則會改由透過 Apple 的 CFUUID 產生 ID。此值會在初次啟動時產生，然後儲存以供後續使用。此 ID 會在應用程式升級時保留、在標準應用程式備份程序期間儲存並還原，以及在應用程式解除安裝時移除。

   >[!TIP]
   >
   >如果您的應用程式從 Experience Cloud 3.x 升級至 4.x SDK，應用程式會擷取先前的訪客 ID (自訂或自動產生) 並將其儲存為自訂使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `nil`，且會使用追蹤識別碼。如需詳細資訊，請參閱下方的 userIdentifier 列。

   * 以下是此方法的語法:

      ```objective-c
      trackingIdentifier()
      ```

      * 傳回: `String`
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   強制資料庫傳送離線佇列中的所有點擊，不論目前還有多少處於佇列中。

   * 以下是此方法的語法:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * 傳回: N/A
      * 參數: 無
   * 以下是此方法的範例程式碼:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   清除離線佇列中的所有點擊。

   * 以下是此方法的語法:

      ```objective-c
      trackingClearQueue()
      ```

      * 傳回: N/A
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   擷取離線佇列中目前的點擊數。

   * 以下是此方法的語法:

      ```objective-c
      trackingGetQueueSize()
      ```

      * 傳回: 數字
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager 方法 {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   傳回最近取得的訪客描述檔。

   如果尚未提交任何訊號，則傳回 null。訪客設定檔會儲存在 `NSUserDefaults` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```objective-c
      audienceVisitorProfile()
      ```

      * 傳回: 物件
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   傳回目前的 DPID。

   * 以下是此方法的語法:

      ```objective-c
      audienceDpid()
      ```

      * 傳回: 字串
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   傳回目前的 DPUUID。

   * 以下是此方法的語法:

      ```objective-c
      audienceDpuuid()
      ```

      * 傳回: `String`
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   設定 dpid 和 dpuuid，若已設定，則兩者會以各自訊號傳送。

   * 以下是此方法的語法:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * 傳回: N/A
      * 參數: `dpid`
         * 類型: `String`
         * Audience Manager 資料提供者 ID。
      * 參數: `dpuuid`
         * 類型: `String`
         * 使用者和資料提供者組合的識別碼。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   傳送具有特徵的信號給 Audience Manager，並取得回撥函式中傳回的相符區段。

   * 以下是此方法的語法:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * 參數: `traits`
         * 類型: 物件
         * 該使用者的特徵字典。
      * 參數: `callback`
         * 類型: 函式 (設定檔)
         * 在回撥函式參數中從 Audience Manager 傳回的設定檔。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   重設 Audience Manager UUID 並清除目前的訪客設定檔。

   * 以下是此方法的範例程式碼:

      ```objective-c
      audienceReset()
      ```

      * 傳回: N/A
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID 服務方法 {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   從 ID 服務中擷取 Experience Cloud ID。

   * 以下是此方法的語法:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * 傳回: 字串
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   除了 Experience Cloud ID 之外，您還可以設定額外的客戶 ID 來與每個訪客產生關聯。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 程式庫中的 setCustomerIDs。

   * 以下是此方法的語法:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * 傳回: N/A
      * 參數: `identifiers`

         * 類型: `Object`
         * 用來同步至此使用者之 ID 服務的識別碼。
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   將提供的識別碼同步至 ID 服務。

   * 以下是此方法的語法:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * 傳回: N/A
      * 參數: `identifiers`
         * 類型: `Object`
         * 用來同步至此使用者之 ID 服務的識別碼。
      * 參數: `authState`
         * 類型: ADBMobileVisitorAuthenticationState
         * 使用者的驗證狀態，可能的值包括:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   將提供的識別碼類型和值同步至 ID 服務。

   * 以下是此方法的語法:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * 傳回: 不適用
      * 參數: `idType`
         * 類型: `String`
         * 正在同步的識別碼類型。
      * 參數: `identifier`
         * 類型: `String`
         * 正在同步的識別碼值。
      * 參數: `authState`
         * 類型: ADBMobileVisitorAuthenticationState
使用者的驗證狀態。可能的值包括:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 以下是此方法的範例程式碼:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   擷取一連串唯讀 ADBVisitorID 物件。下列程式碼範例為 VisitorID 物件的範例:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * 以下是此方法的語法:

      ```objective-c
      visitorGetIDsJs()
      ```

      * 傳回: `Array [Object]`

      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target 方法 {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   傳回第三方 ID。

   * 以下是此方法的語法:

      ```objective-c
      targetThirdPartyID()
      ```

      * 傳回: `String`
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   設定第三方 ID。

   * 以下是此方法的語法:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * 傳回: N/A
      * 參數: `thirdPartyID`
         * 類型: `String`
         * 用於目標要求的第三方 ID。
   * 以下是此方法的範例程式碼:
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   傳回 PcID。

   * 以下是此方法的語法:

      ```objective-c
      targetPcID()
      ```

      * 傳回: `String`
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   傳回工作階段 ID。

   * 以下是此方法的語法:

      ```objective-c
      targetSessionID()
      ```

      * 傳回: `String`
      * 參數: 無
   * 以下是此方法的範例程式碼:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
