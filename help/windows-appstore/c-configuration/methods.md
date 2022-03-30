---
description: Windows 8.1通用App Store庫提供的類和方法。
solution: Experience Cloud Services,Analytics
title: SDK 方法
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 51%

---

# SDK 方法 {#sdk-methods}

Windows 8.1通用App Store庫提供的類和方法。

>[!TIP]
>
>消費時 `winmd` 來自winJS(JavaScript)的方法，所有方法的首字母都自動小寫。

* **GetVersion(winJS:getVersion)**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 此方法的程式碼範例如下：

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown`  — 如果報告套件啟用了時間戳，則會保存命中，直到隱私狀態更改為選擇加入（然後發送命中）或選擇退出（然後丟棄命中）。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值在 [ADBMobileConfig.json配置](/help/windows-appstore/c-configuration/c.json.md) 的子菜單。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * 此方法的範例程式碼如下：

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

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值：

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown`  — 如果報告套件啟用了時間戳，則會保存命中，直到隱私狀態更改為選擇加入（然後發送命中）或選擇退出（然後丟棄命中）。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 此方法的程式碼範例如下：

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

   傳回目前使用者的期限值。預設值為0。

   * 此方法的語法如下：

      ```csharp
      static float GetLifetimeValue();
      ```

   * 此方法的程式碼範例如下：

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier(winJS:getUserIdentifier)**

   如果已設定自定義標識符，則返回自定義用戶標識符。 如果未設定自定義標識符，則返回Null。 預設值為 `null`。

   >[!TIP]
   >
   >如果您的應用程式從Experience Cloud3.x升級到4.x SDK，則會檢索先前的ID（自定義或自動生成）並將其儲存為自定義用戶標識符。 這樣在 SDK 升級之後即可保留訪客資料。對於4.x SDK上的新安裝，用戶標識符為 `null` 直到設定。

   * 此方法的語法如下：

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier(winJS:setUserIdentifier)**

   將使用者識別碼設為 `identifier`。

   * 此方法的語法如下：

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging(winJS:getDebugLogging)**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 此方法的語法如下：

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging(winJS:setDebugLogging)**

   將偵錯記錄偏好設定設為 `debugLogging`。調試日誌記錄僅在使用庫的調試版本時才起作用，發行版本將忽略此設定。

   * 此方法的語法如下：

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData(winJS:收集生命週期資料)**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >在 `onResume()` 方法，如下例所示。 我們還建議將活動或服務作為上下文對象而不是全局應用程式上下文傳遞。

   * 此方法的語法如下：

      ```csharp
      static void CollectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **暫停收&#x200B;集生命週期資料(winJS:暫停收&#x200B;集生命週期資料)**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停時收集時間戳以確定上一個會話長度。 這還設定了一個標誌，這樣生命週期就能正確知道應用程式沒有崩潰。 如需詳細資訊，請參閱[生命週期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >在 `onPause()` 方法，如示例所示。 我們還建議將活動或服務作為上下文對象而不是全局應用程式上下文傳遞。

   * 此方法的語法如下：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
