---
description: 地理位置可協助您透過經緯度和 Android 應用程式中預先定義的地標來測量位置資料。
seo-description: 地理位置可協助您透過經緯度和 Android 應用程式中預先定義的地標來測量位置資料。
seo-title: 地理位置與地標
solution: Experience Cloud,Analytics
title: 地理位置與地標
topic: Developer and implementation
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 83%

---


# 地理位置與地標 {#geo-location-and-points-of-interest}

地理位置可協助您透過經緯度和 Android 應用程式中預先定義的地標來測量位置資料。

各 `trackLocation` 呼叫均會傳送以下資訊:

* 在 Adobe Mobile Services 使用者介面中定義之地標 (POI) 的經緯度和位置。

   這項資訊會傳遞至行動解決方案變數，以進行自動報告。

* 與中心的距離和作為上下文資料傳遞的精確度。

   系統不會自動擷取上述變數。您必須透過以下&#x200B;*傳送其他資料*&#x200B;一節中的指示，對應此類內容資料變數。

## 動態 POI 更新 {#section_3747B310DD5147E2AAE915E762997712}

自 4.2 版開始，POI 皆會在 Adobe Mobile 使用者介面中定義，並會動態同步至應用程式設定檔案。此同步作業須使用 [ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)中的 `analytics.poi` 設定:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

如果尚未設定此項目，您必須下載更新版本的 `ADBMobile.json` 檔案，並將其新增至您的應用程式。如需詳細資訊，請參閱[下載 SDK 和測試工具](/help/android/getting-started/requirements.md)。

## 追蹤地理位置和 POI {#section_B1616E400A7548F9A672F97FEC75AE27}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 呼叫 `trackLocation` 以追蹤目前位置:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >您可以隨時呼叫 `trackLocation`。

   您可以依照定位策略一文所述，判斷傳遞至 `trackLocation` 呼叫的位置。如需詳細資訊，請參閱 [Android 定位策略](https://developer.android.com/guide/topics/location/strategies.html)。

此外，如果該位置經判斷位於定義的 POI 半徑範圍內，則 `a.loc.poi` 內容資料變數將會與 `trackLocation` 點擊一併傳入，並會在&#x200B;****「位置劃分」報表中報告為 POI。`a.loc.dist` 內容變數也會以公尺為單位傳送來自定義座標的距離。

## 傳送其他資料 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了位置資料之外，您還可以隨著每次追蹤位置呼叫傳送其他內容資料:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

內容資料值必須對應至 Adobe Mobile Services 使用者介面中的自訂變數:

![](assets/map-location-context-data.png)

## 位置內容資料 {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

緯度和經度是使用三個不同的上下文資料參數來傳送的，每個參數代表不同的精確度等級，總共有六個上下文資料參數。

例如，坐標lat = 40.93231, long = -111.93152表示精度為1 m的位置。 此位置會依下列變數的精確度等級分割：

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111.9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

視目前位置準確度而定，部分精準度可能會顯示為 `00`。例如，如果該位置目前準確程度至 100 公尺，則 `a.loc.lat.c` 和 `a.loc.lon.c` 將會填入 `00`。

請記住以下資訊:

* `trackLocation` 要求會在 `trackAction` 呼叫的同等項中傳送。

* 系統不會在一般 `trackAction` 和 `trackState` 呼叫過程中傳遞 POI，因此您必須使用 `trackLocation` 呼叫來追蹤 POI。

* 必要時，您應經常呼叫 `trackLocation` 以追蹤位置和 POI。

   建議您視應用程式需求，在應用程式啟動時呼叫 `trackLocation`，並在隨後視需要再次進行。

* POI 只有在已於應用程式設定檔案中完成定義後，才會填入。

   POI 不會套用至先前已傳送的歷史 `trackLocation` 呼叫。
* `trackLocation` 呼叫支援傳送與 `trackAction` 呼叫類似的其他內容資料。

* 當兩個 POI 的直徑範圍重疊時，會使用包含目前位置的第一個 POI。

   如果您的POI重疊，您應依最細至最細的順序列出POI，以確保報告最細的POI。

