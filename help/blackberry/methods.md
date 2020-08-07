---
description: BlackBerry程式庫提供的類別和方法。
seo-description: BlackBerry程式庫提供的類別和方法。
seo-title: Adobe Mobile類別與方法參考
title: Adobe Mobile類別與方法參考
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 55%

---


# Adobe Mobile類別與方法參考 {#adobe-mobile-class-and-method-reference}

BlackBerry程式庫提供的類別和方法。

SDK目前支援Adobe Analytics，而方法則會根據解決方案分開使用。

## SDK設定 {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * ADBMobilePrivacyStatusOptIn —— 會立即傳送點擊。
   * ADBMobilePrivacyStatusOptOut —— 會捨棄點擊。
   * ADBMobilePrivacyStatusUnknown —— 如果您的報表套裝已啟用時間戳記，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著會捨棄點擊）為止。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 以下是此方法的語法：

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值：

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown` -如果您的報表套裝已啟用時間戳記，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著會捨棄點擊）為止。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 以下是此方法的語法：

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   如果已設定自訂識別碼，則傳回使用者識別碼。Returns `null` if a custom identifier is not set. 預設值為 `null`。

   * 以下是此方法的語法：

      ```cpp
      static QString getUserIdentifier();
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 以下是此方法的語法：

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 以下是此方法的語法：

      ```cpp
      static bool getDebugLogging();
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   將偵錯記錄偏好設定設為 `debugLogging`。

   * 以下是此方法的語法：

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/blackberry/metrics.md)。

   * 以下是此方法的語法：

      ```cpp
      static void collectLifecycleData();
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics 方法 {#section_91F4AD0A045D4E4E8F9A93450503E49E}

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

* **trackState**

   使用可選內容資料來追蹤應用程式。狀態是應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 以下是此方法的語法：

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   追蹤應用程式中的動作。動作是您要測量的應用程式中發生的事，例如「登入」、「橫幅點選」、「動態消息訂閱」和其他量度。

   * 以下是此方法的語法：

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的範例程式碼:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   傳送目前的 x 和 y 座標。將事件取代為從訂閱者接收到的BPS事件。

   * 以下是此方法的語法：

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 以下是此方法的範例程式碼：

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 設定檔案參考 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   （必要）一或多個報表套裝，用以接收Analytics資料。 多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

   以下是此變數的程式碼範例：

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必填). Analytics伺服器。 應該以伺服器網域填入此變數，不含 `https://` 或 `https://` 通訊協定前置詞。程式庫會根據變數自動處理通訊協定首 `ssl` 碼。 如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用來傳送至Analytics之資料的字元集。 字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。

* **ssl**

   啟用(`true`)或停用(`false`)透過SSL(HTTPS)傳送測量資料。 預設值為 `false`。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   >[!TIP]
   >
   >如果報表套裝已啟用時間戳記，您的 `offlineEnabled` 組態屬性&#x200B;*必須*&#x200B;為 `true`. 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 false。若未正確設定，資料將會遺失。如果您不確定報表套裝是否啟用時間戳記，請連絡企業 [支援](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)。

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   預設值為 `false`。

* **lifecycleTimeout**

   指定兩次應用程式啟動之間必須經過的時間長度（以秒為單位），之後啟動才會被視為新作業。 您的應用程式傳送至背景並重新啟動時，此逾時也適用。應用程式在背景執行的時間不會計入工作階段中。

   預設值為300秒。

* **batchLimit**

   儲存在佇列中的離線點擊數上限。 預設值為0（無限制）。

* **privacyDefault**

   * `optedin` – 會立即傳送點擊。
   * `optedout` – 會捨棄點擊。
   * `optunknown` -如果您的報表套裝已啟用時間戳記，則會儲存點擊，直到隱私權狀態變更為選擇加入（接著傳送點擊）或選擇退出（接著會捨棄點擊）為止。

      如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   此變數僅設定初始值。 如果此值在程式碼中設定或變更過，則會繼續使用新值，直到變更為止，或是解除安裝並重新安裝應用程式。

   預設值為 `optedin`。

The following is an example of an `ADBMobileConfig.json` file:

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
