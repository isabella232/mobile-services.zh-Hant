---
description: 以下為 Android 資料庫所提供的 Adobe Analytics 方法清單。
keywords: android;library;mobile;sdk
seo-description: 以下為 Android 資料庫所提供的 Adobe Analytics 方法清單。
seo-title: Analytics 方法
solution: Marketing Cloud,Analytics
title: Analytics 方法
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '740'
ht-degree: 100%

---


# Analytics 方法 {#analytics-methods}

以下為 Android 資料庫所提供的 Adobe Analytics 方法清單。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。各方法會根據解決方案加上前置詞，例如 Experience Cloud ID 方法會加上前置詞 `analytics`。

下列各方法將用來傳送資料至您的 Adobe Analytics 報表套裝：

* **trackState**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視，例如 `home dashboard`、`app settings`、`cart` 等。這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

   如果 `state` 空白，在報表中會顯示 `app name app version (build)`。如果在報表中看到這個值，請務必在每個 `state` 呼叫中設定 `trackState`。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
追蹤應用程式中的動作。

   您要測量的動作，例如 `logons`、`banner taps`、`feed subscriptions`，以及在應用程式中發生的其他量度。

   * 此方法的語法如下：

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
傳回自動產生的 Analytics 訪客識別碼。

   這是應用程式專屬、不重複的訪客 ID，會在初次啟動時產生，並會從此時間點儲存及使用。ID 會在應用程式升級時保留，並在解除安裝應用程式時移除。

   * 此方法的語法如下：

      ```java
      public static String getTrackingIdentifier();
      ```

   * 此方法的範例程式碼如下：

      ```java
      String trackingId = Analytics.getTrackingIdentifier();
      ```

* **trackLocation**

   傳送目前的經緯度，以及已定義地標中的位置。如需詳細資訊，請參閱[地理位置與地標](/help/android/location/geo-poi.md)。

   * 此方法的語法如下：

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   增加使用者期限值的 `amount`。

   * 此方法的語法如下：

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   以名稱 `action` 啟動計時動作。

   如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

   ```java
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   傳遞 `contextData` 以更新與 `action` 關聯的內容資料。傳遞的 `data` 會附加至該動作的現有資料，如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * 此方法的範例程式碼如下：

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   結束計時動作。如果您提供 `block`，則可在傳送最後一次點擊前存取最後時間值並處理 `data`。

   >[!TIP]
   >
   >如果您提供`block`，則必須傳回 `true` 以傳送點擊。針對 `block` 傳遞 `null` 會傳送最後一次點擊。

   * 此方法的語法如下：

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
              contextData.put("price", 49.95);
              return true;
          }
      });
      ```

* **sendQueuedHits**

   **須使用 SDK 4.1 版.**

   無論排入佇列的點擊數量多寡，此方法會強制資料庫傳送離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```java
      public static void sendQueuedHits();
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   傳回在離線佇列中儲存的追蹤呼叫數目。

   * 此方法的語法如下：

      ```java
      public static long getQueueSize();
      ```

   * 此方法的範例程式碼如下：

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   清除離線佇列中的所有點擊。

   * 此方法的語法如下：

      ```java
      public static void clearQueue();
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > 手動清除佇列時請小心。此程序無法回復。

* **processReferrer**

   處理來自 Google Play 商店的反向連結行銷活動資料，以供日後使用。

   * 此方法的語法如下：

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > 此 API 從 SDK 4.18.0 版開始提供使用

   從提供的 Google Play 安裝反向連結 URL 擷取贏取資料。

   從此 API 收集的資料會在傳送至 Analytics 的安裝點擊時傳送，並可在Adobe資料回撥中使用。

   如果 SDK 已收集反向連結資料，呼叫此方法會導致無操作。

   如需如何擷取反向連結 URL 的詳細資訊，請參閱 Google 文件：https://developer.android.com/google/play/installreferrer/library

   * 此方法的語法如下：

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * 此方法的範例程式碼如下：

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
