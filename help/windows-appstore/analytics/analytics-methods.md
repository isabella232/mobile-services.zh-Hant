---
description: 幫助您將Windows 8.1 UniversalApp StoreSDK與Adobe Analytics配合使用的資訊。
solution: Experience Cloud Services,Analytics
title: 'Analytics 方法 '
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 53%

---

# Analytics 方法  {#analytics-methods}

幫助您將Windows 8.1 UniversalApp StoreSDK與Adobe Analytics配合使用的資訊。

SDK當前支援多個Adobe Experience Cloud解決方案，包括分析、目標和Audience Manager。 各方法會根據解決方案加上前置詞。分析方法的前置詞為「分析」。

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

>[!TIP]
>
>消費時 `winmd` 來自winJS(JavaScript)的方法，所有方法的首字母都自動小寫。

* **跟蹤狀態(winJS:跟蹤狀態)**

   使用可選內容資料來追蹤應用程式。狀態是您的應用中可用的視圖，如「首頁儀表板」、「應用設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。如果 `state` 為空，它在報告中顯示為「app name app version(build)」。 如果在報告中看到此值，請確保正在設定 `state` 每 `TrackState` 呼叫。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **跟蹤操作(winJS:跟蹤操作)**

   追蹤應用程式中的動作。操作是您想要衡量的應用中發生的情況，如「登錄」、「橫幅點擊」、「訂閱源」和其他度量。

   * 此方法的語法如下：

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **GetTrackingIdentifierAsync(winJS:getTrackingIdentifierAsync)**

   
傳回自動產生的 Analytics 訪客識別碼。這是特定於應用的唯一訪問者ID，在初始啟動時生成，然後從該點向前儲存和使用。 此ID在應用程式升級之間保留，並在卸載時刪除。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **跟蹤位置(winJS:跟蹤位置)**

   傳送目前的 x 和 y 座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 此方法的語法如下：

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **TrackLifetime值&#x200B;增加(winJS:trackLifetime &#x200B; ValueIncrease)**

   增加使用者期限值的 `amount`。

   * 此方法的語法如下：

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **TrackTimed &#x200B; ActionStart(winJS:trackTimed &#x200B; ActionStart)**

   以名稱 `action` 啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **TrackTimed &#x200B; ActionUpdate(winJS:trackTimed &#x200B; ActionUpdate)**

   傳遞 `contextData` 以更新與指定 `action` 關聯的內容資料。的 `data` 傳遞的內容將附加到給定操作的現有資料中，如果為定義了相同的鍵，則覆蓋資料 `action`。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 此方法的語法如下：

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **TrackTimedActionExistsAsync(winJS:trackTimedActionExistsAsync)**

   如果給定的定時操作存在，則返回true；如果不存在，則返回false。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd(winJS:trackTimed &#x200B; ActionEnd)**

   結束計時動作。

   * 此方法的語法如下：

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue(winJS:clearTrackingQueue)**

   清除分析跟蹤隊列中儲存的所有命中。

   * 以下是此消息的語法：

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 下面是代碼示例：

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync(winJS:getQueueSizeAsync)**

   返回當前儲存在分析隊列中的命中數。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
