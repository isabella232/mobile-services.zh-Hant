---
description: 以下為 Android 資料庫所提供的方法清單。
keywords: Android；資料庫；行動；sdk
seo-description: 以下為 Android 資料庫所提供的方法清單。
seo-title: 設定方法
solution: Marketing Cloud、Analytics
title: 設定方法
topic: 開發人員和實施
uuid: 663ab6c-1b97-4a3a-8c0e-dd4 c2 ec28 c01
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Configuration methods{#configuration-methods}

以下為 Android 資料庫所提供的方法清單。

## Initial configuration {#section_9169243ECC4744A899A8271F92090ECD}

您必須在主要活動的 `onCreate` 方法中呼叫一次以下方法:

* `setContext`
以下是此方法的範例程式碼:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ````


## SDK settings (Config Class) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * 註冊實施 `AdobeDataCallback` 介面的物件。The overwritten "call" method will be invoked with a `Config.MobileDataEvent` value and the associated data in a `Map<String, Object>` for the triggering event. 如需哪些事件會觸發此回呼的詳細資訊，請參閱 *本主題底部的MobileDataEventNum* 。

      >[!TIP]
      >
      >此方法需要4.9.0版或更新版本。

   * 以下是此方法的語法:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * 以下是此方法的範例程式碼:

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
   * 以下是此方法的語法:

      ```java
      public static String getVersion();
      ```

   * 以下是此方法的程式碼範例：

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * 傳回目前使用者之隱私權狀態的列舉表示法。

      以下為隱私權狀態值:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`會立即傳送點擊。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`其被捨棄的位置。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`，如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

         如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。預設值設定在 `ADBMobileConfig.json` 檔案中。
   * 以下是此方法的語法:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * 將目前使用者的隱私權狀態設為 `status`。

      您可以將隱私權狀態設定為下列其中一個值:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`會立即傳送點擊。會立即傳送點擊。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`其被捨棄的位置。會捨棄點擊。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`，如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   * 以下是此方法的語法:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * 以下是此方法的程式碼範例：

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * 傳回目前使用者的期限值。預設值為 `0`。

   * 以下是此方法的語法:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * 以下是此方法的程式碼範例：

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * 若已設定自訂識別碼，將會傳回自訂使用者識別碼。若尚未設定自訂識別碼，則會傳回 `null`。預設值為 `null`。

      >[!TIP]
      >
      >如果您的應用程式升級從Experience Cloud3.x升級至4.x SDK，則會擷取先前的自訂或自動產生的訪客ID並儲存為自訂的使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，直到設定完成為止。

   * 以下是此方法的語法:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * 以下是此方法的程式碼範例：

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * 將使用者識別碼設為 `identifier`。
   * 以下是此方法的語法:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * 傳回目前的偵錯記錄偏好設定。預設值為 `false`。
   * 以下是此方法的語法:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * 將偵錯記錄偏好設定設為 `debugLogging`。
   * 以下是此方法的語法:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/configuration/methods.md)。

   * 以下是此方法的語法:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      含額外內容資料:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**4.2 版或更新版本**) 向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。
   * 以下是此方法的語法:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * 向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，`onPause` 以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

   * 以下是此方法的語法:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**4.2 版或更新版本**) 設定用於 SDK 所建立之通知的小型圖示。此圖示在使用者於通知中心查看完整通知時會出現在狀態列，且是所顯示影像的次要影像。
   * 以下是此方法的語法:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**4.2 版或更新版本**) 設定用於 SDK 所建立之通知的大型圖示。此圖示會是使用者在通知中心查看完整通知時所顯示的主要影像。
   * 以下是此方法的語法:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * 以下是此方法的範例程式碼:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**4.2 版或更新版本**) 可讓您在應用程式啟動時載入另一個 ADBMobile JSON 設定檔案。應用程式會使用另一個設定，直到關閉為止。
   * 以下是此方法的語法:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * 以下是此方法的範例程式碼:

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
   * 以下是此方法的語法:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * 提供一個會傳回廣告識別碼 (從 Google Play Services 傳回) 的「可呼叫」至 SDK。SDK 會在背景執行緒執行此作業，並根據「可呼叫」傳回的值，為廣告識別碼設定內部變數。

      >[!IMPORTANT]
      > 
      >If you want to use the Advertising Identifier in Acquisition or Lifecycle, call it before calling `Config.collectLifecycleData`.

      * 以下是此方法的語法:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * 以下是此方法的範例程式碼:

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
