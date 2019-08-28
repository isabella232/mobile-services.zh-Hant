---
description: BlackBerry程式庫提供的類別和方法。
seo-description: BlackBerry程式庫提供的類別和方法。
seo-title: Adobe Mobile類別與方法參考
title: Adobe Mobile類別與方法參考
uuid: 1e42d759-be43-4bb3-ac1 a-c7 d64133 d61 c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

BlackBerry程式庫提供的類別和方法。

SDK目前擁有Adobe Analytics的支援，而方法是根據解決方案不同類別。

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * ADBMobilePrivacyStatusOptIn – 會立即傳送點擊。
   * ADBMobilePrivacyStatusOptOut – 會捨棄點擊。
   * ADBMobilePrivacyStatusUnknown – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 以下是此方法的語法:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值:

   * `ADBMobilePrivacyStatusOptIn` - 點擊會立即傳送。
   * `ADBMobilePrivacyStatusOptOut` - 點擊會被捨棄。
   * `ADBMobilePrivacyStatusUnknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   如果已設定自訂識別碼，則傳回使用者識別碼。Returns `null` if a custom identifier is not set. 預設值為 `null`。

   * 以下是此方法的語法:

      ```cpp
      static QString getUserIdentifier();
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的語法:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 以下是此方法的語法:

      ```cpp
      static bool getDebugLogging();
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   將偵錯記錄偏好設定設為 `debugLogging`。

   * 以下是此方法的語法:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/blackberry/metrics.md)。

   * 以下是此方法的語法:

      ```cpp
      static void collectLifecycleData();
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

* **trackState**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」和「購物車」等等。這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

   >[!TIP]
   >
   >這是唯一遞增頁面檢視的追蹤呼叫。

   * 以下是此方法的語法:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   追蹤應用程式中的動作。動作是發生在應用程式中而且您想測量的項目，例如「登入」、「橫幅點選」、「摘要訂閱」以及其他量度。

   * 以下是此方法的語法:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   傳送目前的 x 和 y 座標。以從訂閱者到 BPS 接收到的事件取代事件。

   * 以下是此方法的語法:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` config檔案參考 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json` 檔案必須放置在 *資產* 資料夾中。

* **rsids**

   (必要) 用來接收 Analytics 資料的一或多個報表套裝。多個報表套裝的 ID 應以逗號分隔，中間沒有空格。

   以下是此變數的程式碼範例：

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必填). Analytics 伺服器。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. 通訊協定字首會由程式庫根據 `ssl` 變數自動處理。如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用於傳送至 Analytics 之資料的字元集。字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). 預設值為 `false`。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   >[!TIP]
   >
   >如果報表套裝已啟用時間戳記，您的 `offlineEnabled` 組態屬性&#x200B;*必須*&#x200B;為 `true`. 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 false。如果此項目未正確設定，將會遺失資料。如果您不確定報表套裝是否啟用時間戳記，聯絡 [企業支援](https://helpx.adobe.com/contact/enterprise-support.ec.html)。

   如果您目前回報 AppMeasurement 資料的報表套裝也可從 JavaScript 收集資料，則必須為行動資料設定個別的報表套裝，或在使用 `s.timestamp` 變數的所有 JavaScript 點擊上加上自訂時間戳記。

   預設值為 `false`。

* **lifecycleTimeout**

   指定在兩次應用程式啟動之間需經過的時間長度 (單位為秒)，超過該秒數後，該次啟動即視同新的作業階段。這個逾時值也套用至將應用程式傳送至背景並重新啟動時。應用程式在背景花的時間，不算在作業階段長度中。

   預設值為300秒。

* **batchLimit**

   儲存在佇列中的離線點擊數量上限。預設值為(無限制)。

* **privacyDefault**

   * `optedin` - 點擊會立即傳送。
   * `optedout` - 點擊會被捨棄。
   * `optunknown` – 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入 (屆時會傳送點擊) 或選擇退出 (屆時會捨棄點擊) 為止。

      如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   此變數僅設定初始值。如果已在程式碼中設定或變更此值，即會使用新的值直到變更此值，或應用程式解除安裝並重新安裝為止。

   預設值為 `optedin`。

以下是 `ADBMobileConfig.json` 檔案的範例:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
