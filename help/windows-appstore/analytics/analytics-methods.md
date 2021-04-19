---
description: 協助您搭配Adobe Analytics使用Windows 8.1通用應用程式商店SDK的資訊。
seo-description: 協助您搭配Adobe Analytics使用Windows 8.1通用應用程式商店SDK的資訊。
seo-title: 'Analytics 方法 '
solution: Experience Cloud,Analytics
title: 'Analytics 方法 '
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 52%

---

# Analytics 方法 {#analytics-methods}

協助您搭配Adobe Analytics使用Windows 8.1通用應用程式商店SDK的資訊。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。Analytics方法的前置詞為「Analytics」。

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

>[!TIP]
>
>當您從winJS(JavaScript)使用`winmd`方法時，所有方法都會自動將其第一個字母小寫。

* **TrackState(winJS:trackState)**

   使用可選內容資料來追蹤應用程式。狀態是應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `TrackState` 呼叫會遞增頁面檢視。如果`state`為空白，則會在報表中顯示為「應用程式名稱應用程式版本（組建版本）」。 如果您在報表中看到此值，請務必在每個`TrackState`呼叫中設定`state`。

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

* **TrackAction(winJS:trackAction)**

   追蹤應用程式中的動作。動作是您要測量的應用程式中發生的事，例如「登入」、「橫幅點選」、「動態消息訂閱」和其他量度。

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

   
傳回自動產生的 Analytics 訪客識別碼。這是應用程式專屬的獨特訪客ID，會在初次啟動時產生，然後儲存並從此開始使用。 此ID會在應用程式升級時保留，並在解除安裝時移除。

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

* **TrackLocation(winJS:trackLocation)**

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

* **TrackLifetime &#x200B; ValueIncrease(winJS:trackLifetime &#x200B; ValueIncrease)**

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

   傳遞 `contextData` 以更新與指定 `action` 關聯的內容資料。傳遞的`data`會附加至指定動作的現有資料，並在`action`已定義相同金鑰時覆寫資料。

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

   如果指定的計時動作存在，則傳回true；如果不存在，則傳回false。

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

   清除Analytics追蹤佇列中所有儲存的點擊。

   * 以下是此訊息的語法：

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 以下是程式碼範例：

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync(winJS:getQueueSizeAsync)**

   傳回目前儲存在Analytics佇列中的點擊數。

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
