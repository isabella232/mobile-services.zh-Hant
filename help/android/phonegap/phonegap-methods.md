---
description: 您可以使用 iOS PhoneGap 外掛程式方法來完成各種作業。
keywords: Android；資料庫；行動；sdk
seo-description: 您可以使用 iOS PhoneGap 外掛程式方法來完成各種作業。
seo-title: PhoneGap增效模組方法
solution: Marketing Cloud、Analytics
title: PhoneGap增效模組方法
topic: 開發人員和實施
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

您可以使用 Android PhoneGap 增效模組方法來完成各種作業。

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   傳回目前使用者的隱私權狀態。

   可用的狀態包括:

   * `ADB.optedIn`：隨即傳送點擊。
   * `ADB.optedOut`：點擊會被捨棄。
   * `ADB.optUnknown`：如果您的報表套裝 **已** 啓用時間戳記，則會儲存點擊直到隱私權狀態變更為選擇加入(點擊傳送點擊)或選擇退出(點擊捨棄點擊)為止。如果您的報表套裝&#x200B;**沒有**&#x200B;啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 以下是此方法的範例程式碼:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。

   您可以設定下列其中一種狀態:

   * `ADB.optedIn`：隨即傳送點擊。
   * `ADB.optedOut`：點擊會被捨棄。
   * `ADB.optUnknown`：如果您的報表套裝 **已** 啓用時間戳記，則會儲存點擊直到隱私權狀態變更為選擇加入(點擊傳送點擊)或選擇退出(點擊捨棄點擊)為止。如果您的報表套裝&#x200B;**沒有**&#x200B;啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   傳回目前使用者的期限值。預設值為 0。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. 預設情況下，該變數為 `false`.

   * 以下是此方法的範例程式碼:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   取得資料庫版本。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   傳回自動產生的訪客識別碼。

   這是應用程式專屬的唯一訪客 ID，會在應用程式初次啟動時產生，並會儲存以供後續使用。此 ID 會在應用程式升級時保留，並於應用程式解除安裝時移除。

   >[!TIP]
   >
   >如果您的應用程式升級從Experience Cloud3.x到4.x SDK，先前的訪客ID(自訂或自動產生)會被擷取並儲存為自訂的使用者識別碼。如需詳細資訊，請參閱下方的 `getUserIdentifier`。此 ID 會在 SDK 升級後保留訪客資料。

   若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，且會使用追蹤識別碼。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   若已設定自訂使用者識別碼，將會傳回此識別碼，否則會傳回 `null`。預設值為 `null`。

   * 以下是此方法的範例程式碼:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   設定用於推送通知的裝置代號。

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * 以下是此方法的語法:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   將生命週期工作階段的偏好設定為保持運作。

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. 只有在應用程式註冊了接收背景通知時，才能使用此方法。

   * 以下是此方法的範例程式碼:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   不論目前的批次選項為何，都會強制資料庫傳送排入佇列的所有點擊。

   * 以下是此方法的範例程式碼:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   取得或設定離線佇列中儲存的追蹤呼叫數目。

   * 以下是此方法的範例程式碼:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   移除離線佇列中所有儲存的追蹤呼叫。

   >[!WARNING]
   >
   >手動清除佇列時請小心，因為它無法反轉。

   * 以下是此方法的範例程式碼:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   提交 PII 收集要求。

   * 以下是此方法的語法:
   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   追蹤 Adobe 深層連結點進。

   >[!TIP]
   >
   >如果生命週期呼叫是啓動事件，則會附加Adobe連結資料，否則會傳送額外的呼叫。

   * 以下是此方法的語法:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   使用可選內容資料來追蹤應用程式。States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

   `cData`: JSON 物件，具有要在內容資料中傳送的鍵值值組。

   * 以下是此方法的語法:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * 以下是此方法的程式碼範例：

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   追蹤應用程式中的動作。Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * 以下是此方法的語法:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * 以下是此方法的程式碼範例：

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   傳送目前的 x 和 y 座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adds `amount` to the user's lifetime value.

   * 以下是此方法的語法:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   以名稱 `action` 啟動計時動作。

   如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   傳遞的 `cData` 會附加至該動作的現有資料，如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   * 以下是此方法的語法:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   結束計時動作。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   傳回計時動作是否正在進行中。

   * 以下是此方法的語法:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   追蹤使用者何時進入信標鄰近地區。

   * 以下是此方法的語法:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   在使用者離開信標鄰近地區後，清除信標資料。

   * 以下是此方法的語法:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Target methods {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   傳送要求至您設定的 `Target` 伺服器並傳回選件的字串值。

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   傳送要求至您設定的 `Target` 伺服器。

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   清除共用 Cookie 儲存空間中的 `Target` Cookie。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   透過 Target 伺服器取得針對此訪客傳回之 `SessionID` Cookie 的值。

   * 以下是此方法的語法:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   透過 `PcID` 伺服器取得針對此訪客傳回之 `Target` Cookie 的值。

   * 以下是此方法的語法:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   設定 Target 的自訂訪客 ID。

   * 以下是此方法的語法:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   取得 Target 的自訂訪客 ID。

   * 以下是此方法的語法:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * 以下是此方法的程式碼範例：

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   傳送要求至您設定的 Target 伺服器並傳回選件的字串值。

   * 以下是此方法的語法:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. 如需詳細資訊，請參閱 [設定方法](/help/android/configuration/methods.md)。

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   取得訪客的設定檔。

   * 以下是此方法的語法:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   傳回 DPUUID。

   * 以下是此方法的語法:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   傳回 DPID。

   * 以下是此方法的語法:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   設定 DPID 和 DPUUID。

   * 以下是此方法的語法:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   處理 Audience Manager 服務要求。

   * 以下是此方法的語法:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * 以下是此方法的程式碼範例：

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID並清除目前的訪客個人資料。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   從 ID 服務傳回 Experience Cloud ID。

   * 以下是此方法的語法:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   將提供的識別碼與 ID 服務同步。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   將提供的識別碼同步至 ID 服務。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   將提供的識別碼同步至 ID 服務。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   附加訪客識別碼至指定 URL。

   * 以下是此方法的語法:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * 以下是此方法的語法:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
