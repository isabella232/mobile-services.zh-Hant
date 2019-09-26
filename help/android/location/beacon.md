---
description: 信標追蹤可讓您透過 iBeacon 和藍牙低功耗來測量微位置並以其為目標。
keywords: android;library;mobile;sdk
seo-description: 信標追蹤可讓您透過 iBeacon 和藍牙低功耗來測量微位置並以其為目標。
seo-title: 信標追蹤
solution: Marketing Cloud,Analytics
title: 信標追蹤
topic: 開發人員和實施
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 信標追蹤 {#beacon-tracking}

信標追蹤可讓您透過 iBeacon 和藍牙低功耗來測量微位置並以其為目標。

呼叫 `trackBeacon` 時，會傳送下列信標資料至 Analytics 和 Target:

* `a.beacon.uuid` -信標的ProximityUUID
* `a.beacon.major` – 主要信標編號 (例如商店編號)
* `a.beacon.minor` – 次要信標編號 (例如商店內的唯一編號)
* `a.beacon.prox` – 值 0 至 3 代表使用者與信標之間的距離範圍。

以下是這些值的代表涵義:

* 0 = 未知
* 1 = 極近
* 2 = 近
* 3 = 遠

此信標資料是行動解決方案變數中擷取的。

## 追蹤信標 {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請 *參閱核心實作和生命週期中的新增SDK和設定檔至IntelliJ IDEA或Eclipse*[專案](/help/android/getting-started/dev-qs.md)。

1. 匯入程式庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 收集信標位置。

   視信標的製造商而定，多個第三方資料庫皆可用來掃描藍牙 LE 信標。
1. 取得信標資訊之後，使用下列呼叫以追蹤位置:

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. 當使用者離開信標鄰近範圍時，會清除目前的信標:

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了信標資料之外，您還可以隨著每次 `trackBeacon` 呼叫傳送其他內容資料:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

上下文資料值必須對應至Adobe Mobile services中的自訂變數：

![](assets/map-variable-context-ltv.png)

