---
description: 以下為 Android 資料庫所提供的方法清單。
keywords: android;library;mobile;sdk
seo-description: 以下為 Android 資料庫所提供的方法清單。
seo-title: 設定方法
solution: Experience Cloud,Analytics
title: 設定方法
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 100%

---


# 設定方法{#configuration-methods}

以下為 Android 資料庫所提供的方法清單。

## 初始設定 {#section_9169243ECC4744A899A8271F92090ECD}

您必須在主要活動的 `onCreate` 方法中呼叫一次以下方法：

* `setContext`
此方法的範例程式碼如下：

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## SDK 設定 (設定類別) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * 註冊實作 `AdobeDataCallback` 介面的物件。系統會針對觸發事件，連同 `Config.MobileDataEvent` 值以及 `Map<String, Object>` 中的關聯資料叫用覆寫的「呼叫」方法。如需關於會觸發此回撥之事件的詳細資訊，請參閱本主題底部的 *MobileDataEventEnum*。

      >[!TIP]
      >
      >此方法需使用 4.9.0 版或更新版本。

   * 此方法的語法如下：

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * 此方法的範例程式碼如下：

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * 傳回 Adobe Mobile 程式庫的目前版本。
   * 此方法的語法如下：

      ```java
      public static String getVersion();
      ```

   * 此方法的範例程式碼如下：

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * 傳回目前使用者之隱私權狀態的列舉表示法。

      隱私權狀態值如下：

      * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

         如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 `ADBMobileConfig.json` 檔案中。
   * 此方法的語法如下：

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * 將目前使用者的隱私權狀態設為 `status`。

      您可以將隱私權狀態設定為下列其中一個值：
      * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即傳送點擊。系統會立即傳送點擊。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：捨棄點擊。系統會捨棄點擊。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   * 此方法的語法如下：

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * 傳回目前使用者的期限值。預設值為 `0`。

   * 此方法的語法如下：

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * 此方法的範例程式碼如下：

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * 若已設定自訂識別碼，將會傳回自訂使用者識別碼。若尚未設定自訂識別碼，則會傳回 `null`。預設值為 `null`。

      >[!TIP]
      >
      >如果您的應用程式從 Experience Cloud 3.x 升級至 4.x SDK，應用程式會擷取先前的訪客 ID (自訂或自動產生) 並將其儲存為自訂使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，直到設定完成為止。

   * 此方法的語法如下：

      ```java
      public static String&amp getUserIdentifier();
      ```

   * 此方法的範例程式碼如下：

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * 將使用者識別碼設為 `identifier`。
   * 此方法的語法如下：

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * 傳回目前的偵錯記錄偏好設定。預設值為 `false`。
   * 此方法的語法如下：

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * 將偵錯記錄偏好設定設為 `debugLogging`。
   * 此方法的語法如下：

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/configuration/methods.md)。

   * 此方法的語法如下：

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      含額外內容資料：

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**4.2 版或更新版本**) 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。
   * 此方法的語法如下：

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * 此方法的範例程式碼如下：

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
      ```

* **pauseCollecting&#x200B;LifecycleData**

   * 向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，`onPause` 以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 此方法的語法如下：

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**4.2 版或更新版本**) 設定 SDK 建立通知所使用的小型圖示。此圖示會顯示在狀態列中，亦即當使用者在通知中心看到完整通知時，畫面所顯示的次要影像。
   * 此方法的語法如下：

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**4.2 版或更新版本**) 設定 SDK 建立通知所使用的大型圖示。此圖示會是使用者在通知中心查看完整通知時所顯示的主要影像。
   * 此方法的語法如下：

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * 此方法的範例程式碼如下：

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**4.2 版或更新版本**) 讓您在應用程式啟動時載入其他 ADBMobile JSON 設定檔。應用程式會使用另一個設定，直到關閉為止。
   * 此方法的語法如下：

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * 此方法的程式碼範例如下：

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * 設定用於推送通知的裝置代號。
   * 此方法的語法如下：

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * 此方法的範例程式碼如下：

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * 提供一個會傳回廣告識別碼 (從 Google Play Services 傳回) 的「可呼叫」至 SDK。SDK 會在背景執行緒執行此作業，並根據「可呼叫」傳回的值，為廣告識別碼設定內部變數。

      >[!IMPORTANT]
      > 
      >如果您要在「贏取」或「生命週期」中使用「廣告識別碼」，請在呼叫 `Config.collectLifecycleData` 前對其呼叫。

      * 此方法的語法如下：

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * 此方法的範例程式碼如下：

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback Interface {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
