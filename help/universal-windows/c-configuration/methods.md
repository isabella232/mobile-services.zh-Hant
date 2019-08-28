---
description: 通用 Windows 平台程式庫所提供的類別和方法。
seo-description: 通用 Windows 平台程式庫所提供的類別和方法。
seo-title: SDK方法
solution: Marketing Cloud、Analytics
title: SDK方法
topic: 開發人員和實施
uuid: e3aa41d6-7bc0-4208-a662-129007c209 a77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

通用 Windows 平台程式庫所提供的類別和方法。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion(WinJS：getVersion)**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync(WinJS：getPrivacyStatusAsync)**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * `ADBMobilePrivacyStatusOptIn` - 立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` - 點擊會被捨棄。
   * `ADBMobilePrivacyStatusUnknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      The default value is set in the `ADBMobileConfig.json` config file. 如需詳細資訊，請查看 [ADBMobileConfig. json config檔案](/help/universal-windows/c-configuration/c.json.md)。

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * 以下是此方法的程式碼範例：

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **setPrivacyStatus(WinJS：setPrivacyStatus)**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值:
   * `ADBMobilePrivacyStatusOptIn` - 點擊會立即傳送。
   * `ADBMobilePrivacyStatusOptOut` - 點擊會被捨棄。
   * `DBMobilePrivacyStatusUnknown` - 如果您的報表套裝已啓用時間戳記，則會儲存點擊直到隱私權狀態變更為選擇加入(點擊傳送點擊)或選擇退出(點擊捨棄點擊)為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      * 以下是此方法的語法:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * 以下是此方法的程式碼範例：

         **C-sharp**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue(WinJS：getLifetimeValue)**

   傳回目前使用者的期限值。預設值為 `0`。

   * 以下是此方法的語法:

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **getUserIdentifier(WinJS：getUserIdentifier)**

   如果有設定自訂識別碼，傳回自訂使用者識別碼。Returns `null` if a custom identifier is not set.
預設值為 `null`。

   >[!IMPORTANT]
   >
   >如果您的應用程式升級從Experience Cloud3.x到4.x SDK，先前的ID服務(自訂或自動產生)會被擷取並儲存為自訂的使用者識別碼。這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，直到設定完成為止。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * 以下是此方法的範例程式碼:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier(WinJS：setUserIdentifier)**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的語法:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging(WinJS：getDebugLogging)**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 以下是此方法的語法:

      ```csharp
      static bool GetDebugLogging();
      ```

   * 以下是此方法的範例程式碼:

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **setDebugLogging(WinJS：setDebugLogging)**

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

* **CollectLifecycleData(WinJS：CollectLifecycleData)**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期度量](/help/universal-windows/metrics.md)。

   * 以下是此方法的語法:

      ```csharp
      static void CollectLifecycleData();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollectingLifecycleData(WinJS：PauseCollectingLifecycleData)**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停以收集時間戳記，用於判斷前一個工作階段長度。這也會設定旗標，讓生命週期正確得知應用程式並未當機。如需詳細資訊，請參閱[生命週期量度](/help/universal-windows/metrics.md)。

   * 以下是此方法的語法:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
