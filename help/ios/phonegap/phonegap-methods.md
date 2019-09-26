---
description: 您可以使用 iOS PhoneGap 外掛程式方法來完成各種作業。
keywords: phonegap
seo-description: 您可以使用 iOS PhoneGap 外掛程式方法來完成各種作業。
seo-title: PhoneGap 外掛程式方法
solution: Marketing Cloud,Analytics
title: PhoneGap 外掛程式方法
topic: 開發人員和實施
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods {#phonegap-plug-in-methods}

您可以使用 iOS PhoneGap 外掛程式方法來完成各種作業。

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   傳回目前使用者的隱私權狀態。可用的狀態包括:

   * `ADB.optedIn`，會立即傳送點擊。
   * `ADB.optedOut`, where hits are discarded.
   * `ADB.optUnknown`如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。****&#x200B;如果您的報表套裝&#x200B;**沒有**&#x200B;啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。\
      預設值設定在 `ADBMobileConfig.json` 檔案中。

      * 以下是此方法的範例程式碼:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。您可以設定下列其中一種狀態:
   * `ADB.optedIn`，會立即傳送點擊。
   * `ADB.optedOut`, where hits are discarded.
   * `ADB.optUnknown`**** – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果您的報表套裝&#x200B;**沒有**&#x200B;啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的範例程式碼:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   傳回目前使用者的期限值。預設值為 0。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. 預設情況下，該變數為 `false`.

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   取得資料庫版本。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   傳回自動產生的訪客識別碼。這是應用程式專屬的唯一訪客 ID，會在應用程式初次啟動時產生，並會儲存以供後續使用。此 ID 會在應用程式升級時保留，並於應用程式解除安裝時移除。

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous visitor ID (custom or automatically generated) is retrieved and stored as the custom user identifier (see `getUserIdentifier` below). 這樣在 SDK 升級之後即可保留訪客資料。For new installations on the 4.x SDK, the user identifier is `null`, and tracking identifier is used.

   * 以下是此方法的範例程式碼:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   若已設定自訂識別碼，將會傳回自訂使用者識別碼，否則會傳回 `null`。預設值為 `null`。

   * 以下是此方法的範例程式碼:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   設定用於推送通知的裝置代號。

   * 以下是此方法的語法:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   將生命週期工作階段的偏好設定為保持運作。

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. 只有在應用程式註冊了接收背景通知時，才能使用此方法。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   不論目前的批次選項為何，都會強制資料庫傳送排入佇列的所有點擊。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   取得或設定離線佇列中儲存的追蹤呼叫數目。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   移除離線佇列中所有儲存的追蹤呼叫。

   >[!CAUTION]
   >
   >當手動清除佇列時，請務必小心，因為此動作無法復原。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   向 SDK 指出不論設定檔案中的生命週期工作階段逾時值為何，您下次從背景恢復時都不應啟動新的工作階段。

   >[!IMPORTANT]
   >
   >重要: 此方法旨在用於在背景中註冊接收通知的應用程式，且只有當應用程式於背景執行時，才應從此時執行的程式碼中呼叫此方法。

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱 [Lifecycle metrics](/help/ios/metrics.md).

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   提交 PII 收集要求。

   * 以下是此方法的語法:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   追蹤 Adobe 深層連結點進。

   >[!TIP]
   >
   >If the Lifecycle call is a launch event, the Adobe Link data will be appended, otherwise an extra call will be sent.

   * 以下是此方法的語法:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   追蹤推送訊息點進。

   * 以下是此方法的語法:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   追蹤本機通知訊息點進。

   * 以下是此方法的語法:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   使用可選內容資料來追蹤應用程式。States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。cData is a JSON object with key-value pairs to send in context data.

   * 以下是此方法的語法:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * 以下是此方法的程式碼範例：

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   追蹤應用程式中的動作。Actions are the things that happen in your app that you want to measure, include `logins`, `banner taps`, `feed subscriptions` and other metrics.

   * 以下是此方法的語法:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * 以下是此方法的程式碼範例：

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   追蹤背景發生的動作。如此會在某些情況下阻止觸發生命週期事件。

   * 以下是此方法的語法:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * 以下是此方法的程式碼範例：

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   發送當前x和y座標。 Also uses the points of interest that were defined in the `ADBMobileConfig.json` file to determine if the location provided as a parameter is within any of your POIs. 如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Adds `amount` to the user's lifetime value.

   * 以下是此方法的語法:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   以名稱 `action` 啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   傳遞 `cData` 以更新與指定 `action` 關聯的內容資料。傳遞的 `cData` 會附加至指定動作的現有資料；如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Target methods {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   傳送要求至您設定的 `Target` 伺服器並傳回選件的字串值。

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   傳送要求至您設定的 Target 伺服器。

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   清除共用 Cookie 儲存空間中的 Target Cookie。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   處理 Target 服務要求。

   * 以下是此方法的語法:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   處理 Target 服務要求。

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
      ADB.targetSessionID(success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   透過 Target 伺服器取得針對此訪客傳回之 `PcID` Cookie 的值。

   * 以下是此方法的語法:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   設定 Target 的自訂訪客 ID。

   * 以下是此方法的語法:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * 以下是此群組的程式碼範例：

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   取得 Target 的自訂訪客 ID。

   * 以下是此方法的語法:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   就像使用者已按一下連結，讓開發者得以展開應用程式贏取促銷活動。此方法有助於建立手動贏取連結，並且可由您將應用程式商店重新導向 (例如使用 `SKStoreView`)。

   * 以下是此方法的語法:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the `AppDelegate` generated by Cordova, call `[ADBMobile setAdvertisingIdentifier:]` in the `application:didFinishLaunchingWithOptions:` delegate method. For more information, see Configuration Methods.[](/help/ios/configuration/sdk-methods.md)

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   取得訪客的設定檔。

   * 以下是此方法的語法:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   傳回 DPUUID。

   * 以下是此方法的語法:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   傳回 DPID。

   * 以下是此方法的語法:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   設定 DPID 和 DPUUID。

   * 以下是此方法的語法:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Here are the code samples for this method:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   處理 Audience Manager 服務要求。

   * 以下是此方法的語法:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * 以下是此方法的程式碼範例：

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   重設觀眾管理員 UUID 並清除目前的訪客描述檔。

   * 以下是此方法的範例程式碼:

      ```java
      ADB.audienceReset(); 
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   從 ID 服務傳回 Experience Cloud ID。

   * 以下是此方法的語法:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   將提供的識別碼與 ID 服務同步。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * 以下是此方法的程式碼範例：

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   將提供的識別碼同步至訪客 ID 服務。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   將提供的識別碼同步至訪客 ID 服務。

   * 以下是此方法的語法:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   附加訪客識別碼至指定 URL。

   * 以下是此方法的語法:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorIDs` that have been synced.

   * 以下是此方法的語法:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

