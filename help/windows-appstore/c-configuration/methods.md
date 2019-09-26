---
description: Windows 8.1 通用應用程式商店程式庫所提供的類別和方法。
seo-description: Windows 8.1 通用應用程式商店程式庫所提供的類別和方法。
seo-title: SDK methods
solution: Marketing Cloud,Analytics
title: SDK methods
topic: 開發人員和實施
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Windows 8.1 通用應用程式商店程式庫所提供的類別和方法。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion(winJS:getVersion)**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * `ADBMobilePrivacyStatusOptIn` -會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` - hits are discarded.
   * `ADBMobilePrivacyStatusUnknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Here are the code samples for this method:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus(winJS:setPrivacyStatus)**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值:

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` -會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是此方法的範例程式碼:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue(winJS:getLifetimeValue)**

   傳回目前使用者的期限值。預設值為 0。

   * 以下是此方法的語法:

      ```csharp
      static float GetLifetimeValue();
      ```

   * 以下是此方法的範例程式碼:

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier(winJS:getUserIdentifier)**

   如果有設定自訂識別碼，傳回自訂使用者識別碼。如果未設定自訂識別碼，則傳回 null。預設值為 `null`。

   >[!TIP]
   >
   >如果您的應用程式從Experience Cloud 3.x升級至4.x SDK，則會擷取先前的ID（自訂或自動產生）並儲存為自訂使用者識別碼。 這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，直到設定完成為止。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier(winJS:setUserIdentifier)**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的語法:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging(winJS:getDebugLogging)**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 以下是此方法的語法:

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging(winJS:setDebugLogging)**

   將偵錯記錄偏好設定設為 `debugLogging`。偵錯記錄只會在使用程式庫的除錯版本時作用，發行版本會忽略此設定。

   * 以下是此方法的語法:

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData(winJS:collectLifecycleData)**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. 也建議您將「活動」或「服務」當成上下文物件傳遞，而非當成全域「應用程式」上下文。

   * 以下是此方法的語法:

      ```csharp
      static void CollectLifecycleData();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollecting &#x200B; LifecycleData(winJS:pauseCollecting &#x200B; LifecycleData)**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期正確得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. 也建議您將「活動」或「服務」當成上下文物件傳遞，而非當成全域「應用程式」上下文。

   * 以下是此方法的語法:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
