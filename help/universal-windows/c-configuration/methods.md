---
description: 通用Windows平台程式庫提供的類別和方法。
seo-description: 通用Windows平台程式庫提供的類別和方法。
seo-title: SDK 方法
solution: Experience Cloud,Analytics
title: SDK 方法
topic-fix: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
exl-id: 0aac477c-074d-457c-b117-bb205119c475
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 62%

---

# SDK 方法 {#sdk-methods}

通用Windows平台程式庫提供的類別和方法。

>[!TIP]
>
>當您從winJS(JavaScript)使用`winmd`方法時，所有方法都會自動將其第一個字母小寫。

* **GetVersion(winJS:getVersion)**

   傳回 Adobe Mobile 程式庫的目前版本。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * `ADBMobilePrivacyStatusOptIn` -會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` -會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值設定在`ADBMobileConfig.json`設定檔案中。 如需詳細資訊，請參閱[ADBMobileConfig.json設定檔案](/help/universal-windows/c-configuration/c.json.md)。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * 此方法的範例程式碼如下：

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

* **SetPrivacyStatus(winJS:setPrivacyStatus)**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值：
   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `DBMobilePrivacyStatusUnknown` -如果您的報表套裝已啟用時間戳記，則會儲存點擊，直到隱私權狀態變更為選擇加入（傳送點擊）或選擇退出（捨棄點擊）為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      * 此方法的語法如下：

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * 此方法的範例程式碼如下：

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

* **GetLifetimeValue(winJS:getLifetimeValue)**

   傳回目前使用者的期限值。預設值為 `0`。

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

   如果已設定自訂識別碼，則傳回自訂使用者識別碼。 如果未設定自訂識別碼，則傳回`null`。
預設值為 `null`。

   >[!IMPORTANT]
   >
   >如果您的應用程式從Experience Cloud3.x升級至4.x SDK，則會擷取先前的ID服務（自訂或自動產生）並儲存為自訂使用者識別碼。 這樣在 SDK 升級之後即可保留訪客資料。若為全新安裝的 4.x SDK，則使用者識別碼為 `null`，直到設定完成為止。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * 此方法的程式碼範例如下：

      ```csharp
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

      ```javascript
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

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging(winJS:setDebugLogging)**

   將偵錯記錄偏好設定設為 `debugLogging`。除錯記錄僅在使用程式庫的除錯版本時運作，發行版本會忽略此設定。

   * 此方法的語法如下：

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData(winJS:collectLifecycleData)**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/universal-windows/metrics.md)。

   * 此方法的語法如下：

      ```csharp
      static void CollectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData(winJS:pauseCollecting &#x200B; LifecycleData)**

   向 SDK 指出您的應用程式已暫停，以便正確計算生命週期量度。例如，暫停時會收集時間戳記，以判斷先前的作業長度。 這也會設定旗標，讓生命週期正確知道應用程式未當機。 如需詳細資訊，請參閱[生命週期量度](/help/universal-windows/metrics.md)。

   * 此方法的語法如下：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
