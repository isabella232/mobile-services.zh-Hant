---
description: 此資訊可協助您將通用 Windows 平台 SDK 與 Adobe Analytics 搭配使用。
seo-description: 此資訊可協助您將通用 Windows 平台 SDK 與 Adobe Analytics 搭配使用。
seo-title: 分析方法
solution: Marketing Cloud、Analytics
title: 分析方法
topic: 開發人員和實施
uuid: cc299bb5-ec61-49fb-869a-f3 c3 bc83359 f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

此資訊可協助您將通用 Windows 平台 SDK 與 Adobe Analytics 搭配使用。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target 以及 Audience Manager。各方法會根據解決方案加上前置詞。Analytics 方法會加上前置詞 "Analytics"。

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **trackState(WinJS：trackState)**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」和「購物車」等等。這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。如果 `state` 空白，在報表中會顯示為 "app name app version (build)"。如果在報表中看到此值，請務必在每個 `state` 呼叫中設定 `TrackState`。

   >[!TIP]
   >
   >這是唯一遞增頁面檢視的追蹤呼叫。

   * 以下是此方法的語法:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **trackAction(WinJS：trackAction)**

   追蹤應用程式中的動作。動作是發生在應用程式中而且您想測量的項目，例如「登入」、「橫幅點選」、「摘要訂閱」以及其他量度。

   * 以下是此方法的語法:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync(WinJS：getTrackingIdentifierAsync)**

   傳回自動產生的 Analytics 訪客 ID。這是應用程式專屬的唯一訪客 ID，在首次啟動時產生，接著會儲存起來以供後續使用。此 ID 在應用程式升級時會予以保留，在解除安裝時移除。

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation(WinJS：trackLocation)**

   傳送目前的 x 和 y 座標。也會使用 `ADBMobileConfig.json` 檔案中定義的地標，來判斷提供做為參數的地點是否位在您的 POI 中。如果目前座標位在定義的 POI 中，則會填入內容資料變數並與 `trackLocation` 呼叫一併傳送。

   * 以下是此方法的語法:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **trackLifetimeValueIncrease(WinJS：trackLifetimeValueIncrement)**

   Adds `amount` to the user's lifetime value.

   * 以下是此方法的語法:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimedActionStart(WinJS：trackTimedActionStart)**

   以名稱 `action` 啟動計時動作。如果您對已啟動的動作呼叫此方法，則會覆寫先前的計時動作。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimedActionUpdate(WinJS：TrackTimedActionUpdate)**

   傳遞 `contextData` 以更新與指定 `action` 關聯的內容資料。傳遞的 `data` 會附加至指定動作的現有資料；如果已為 `action` 定義了相同鍵值，則會覆寫資料。

   >[!TIP]
   >
   >此呼叫不會傳送點擊。

   * 以下是此方法的語法:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync(WinJS：trackTimedActionExistsAsync)**

   如果指定的計時動作存在且不存在，則傳回true。

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimedActionEnd(WinJS：trackTimedActionEnd)**

   結束計時動作。

   * 以下是此方法的語法:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **clearTrackingQueue(WinJS：clearTrackingQueue)**

   清除 Analytics 追蹤佇列中所有儲存的點擊。

   * 以下是此方法的語法:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeSync(WinJS：getQueueSizeSync)**

   傳回 Analytics 佇列中目前儲存的點擊數量。

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
