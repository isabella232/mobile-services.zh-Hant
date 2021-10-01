---
description: BlackBerry程式庫提供的類別和方法。
title: Adobe Mobile 類別與方法參考
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
exl-id: ad73ec1d-d082-4237-b7cb-b8ec2f7595a3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 59%

---

# Adobe Mobile 類別與方法參考 {#adobe-mobile-class-and-method-reference}

BlackBerry程式庫提供的類別和方法。

SDK目前支援Adobe Analytics，而方法則根據解決方案位於不同的類別中。

## SDK設定 {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   傳回目前使用者之隱私權狀態的列舉表示法。

   * ADBMobilePrivacyStatusOptIn — 會立即傳送點擊。
   * ADBMobilePrivacyStatusOptOut — 會捨棄點擊。
   * ADBMobilePrivacyStatusUnknown — 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入（屆時會傳送點擊）或選擇退出（屆時會捨棄點擊）為止。 如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

      預設值設定在 `ADBMobileConfig.json` 檔案中。

   * 此方法的語法如下：

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   將目前使用者的隱私權狀態設為 `status`。設定為下列其中一值：

   * `ADBMobilePrivacyStatusOptIn` – 會立即傳送點擊。
   * `ADBMobilePrivacyStatusOptOut` – 會捨棄點擊。
   * `ADBMobilePrivacyStatusUnknown`  — 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入（屆時會傳送點擊）或選擇退出（屆時會捨棄點擊）為止。如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。

   * 此方法的語法如下：

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   如果已設定自訂識別碼，則傳回使用者識別碼。如果未設定自訂識別碼，則傳回`null`。 預設值為 `null`。

   * 此方法的語法如下：

      ```cpp
      static QString getUserIdentifier();
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   將使用者識別碼設為 `identifier`。

   * 此方法的語法如下：

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 此方法的範例程式碼如下：

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   傳回目前的偵錯記錄偏好設定。預設值為 `false`。

   * 此方法的語法如下：

      ```cpp
      static bool getDebugLogging();
      ```

   * 此方法的程式碼範例如下：

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   將偵錯記錄偏好設定設為 `debugLogging`。

   * 此方法的語法如下：

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 此方法的程式碼範例如下：

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   向 SDK 指出應在 SDK 的所有解決方案中收集、使用其生命週期資料。如需詳細資訊，請參閱[生命週期量度](/help/blackberry/metrics.md)。

   * 此方法的語法如下：

      ```cpp
      static void collectLifecycleData();
      ```

   * 此方法的程式碼範例如下：

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics 方法  {#section_91F4AD0A045D4E4E8F9A93450503E49E}

上述各方法將用來傳送資料至您的 Adobe Analytics 報表套裝。

* **trackState**

   使用可選內容資料來追蹤應用程式。狀態為應用程式中可用的檢視，例如「首頁儀表板」、「應用程式設定」、「購物車」等。 這些狀態類似於網站上的頁面，且 `trackState` 呼叫會遞增頁面檢視。

   >[!TIP]
   >
   >這是唯一會遞增頁面檢視的追蹤呼叫。

   * 此方法的語法如下：

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 此方法的程式碼範例如下：

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   追蹤應用程式中的動作。動作是發生在應用程式中且您想測量的項目，例如「登入」、「橫幅點選」、「摘要訂閱」和其他量度。

   * 此方法的語法如下：

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 此方法的程式碼範例如下：

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   傳送目前的 x 和 y 座標。將事件替換為從訂閱者接收到的BPS事件。

   * 此方法的語法如下：

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 此方法的程式碼範例如下：

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 設定檔案參考 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json`檔案必須放置在&#x200B;*assets*&#x200B;資料夾中。

* **rsids**

   （必要）要接收Analytics資料的一或多個報表套裝。 多個報表套裝 ID 應以逗號分隔，且中間不應有空格。

   以下是此變數的范常式式碼：

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必填). Analytics伺服器。 應該以伺服器網域填入此變數，不含 `https://` 或 `https://` 通訊協定前置詞。通訊協定前置詞會由程式庫根據`ssl`變數自動處理。 如果 `ssl` 為 `true`，會對此伺服器進行安全連線。如果 `ssl` 為 `false`，會對此伺服器進行非安全連線。

* **charset**

   定義您用於傳送至Analytics之資料的字元集。 字元集可用來將傳入的資料轉換成 UTF-8 以供儲存和報告。

* **ssl**

   啟用(`true`)或停用(`false`)透過SSL(HTTPS)傳送測量資料。 預設值為 `false`。

* **offlineEnabled**

   啟用(`true`)時，點擊會在裝置離線時排入佇列，並在稍後裝置上線時傳送。 您的報表套裝必須啟用時間戳記才能使用離線追蹤功能。

   >[!TIP]
   >
   >如果報表套裝已啟用時間戳記，您的 `offlineEnabled` 組態屬性&#x200B;*必須*&#x200B;為 `true`. 如果報表套裝未啟用時間戳記，您的 `offlineEnabled` 設定屬性&#x200B;*必須*&#x200B;為 false。若未正確設定，資料將會遺失。如果您不確定報表套裝是否啟用時間戳記，請聯絡[企業支援](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)。

   如果您目前回報AppMeasurement資料的報表套裝也可從JavaScript收集資料，則可能需要為行動資料設定個別的報表套裝，或在使用`s.timestamp`變數的所有JavaScript點擊上加上自訂時間戳記。

   預設值為 `false`。

* **lifecycleTimeout**

   指定應用程式啟動後，直至系統將該次啟動視為新工作階段之間須經過的時間長度 (以秒為單位)。您的應用程式傳送至背景並重新啟動時，此逾時也適用。應用程式在背景執行的時間不會計入工作階段中。

   預設值為300秒。

* **batchLimit**

   儲存在佇列中的離線點擊數上限。 預設值為0（無限制）。

* **privacyDefault**

   * `optedin` – 會立即傳送點擊。
   * `optedout` – 會捨棄點擊。
   * `optunknown`  — 如果您的報表套裝已啟用時間戳記，會儲存點擊直到隱私權狀態變更為選擇加入（屆時會傳送點擊）或選擇退出（屆時會捨棄點擊）為止。

      如果您的報表套裝沒有啟用時間戳記，則會捨棄點擊，直到隱私權狀態變更為選擇加入為止。
   此變數只會設定初始值。 如果在程式碼中設定或變更此值，則會繼續使用新值，直到變更，或應用程式解除安裝並重新安裝為止。

   預設值為 `optedin`。

以下是`ADBMobileConfig.json`檔案的範例：

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
