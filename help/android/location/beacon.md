---
description: 信標追蹤可讓您透過 iBeacon 和藍牙低功耗來測量微位置並以其為目標。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 信標追蹤
topic-fix: Developer and implementation
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
exl-id: b8493e9d-ed1c-4404-a218-47a18a9c8faa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 100%

---

# 信標追蹤 {#beacon-tracking}

信標追蹤可讓您透過 iBeacon 和藍牙低功耗來測量微位置並以其為目標。

呼叫 `trackBeacon` 時，會傳送下列信標資料至 Analytics 和 Target:

* `a.beacon.uuid` – 信標的 ProximityUUID
* `a.beacon.major` – 主要信標編號 (例如商店編號)
* `a.beacon.minor` – 次要信標編號 (例如商店內的唯一編號)
* `a.beacon.prox` – 值 0 至 3 代表使用者與信標之間的距離範圍。

以下是這些值的意思：

* 0 = 未知
* 1 = 旁邊
* 2 = 近
* 3 = 遠

此信標資料是行動解決方案變數中擷取的。

## 追蹤信標 {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫：

   ```java
   import com.adobe.mobile.*;
   ```

1. 收集信標位置。

   根據信標的製造商，可使用多個第三方資料庫掃描藍牙 LE 信標。
1. 取得信標資訊後，請使用以下呼叫追蹤位置：

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

## 傳送其他資料 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了信標資料之外，您還可以隨著每次 `trackBeacon` 呼叫傳送其他內容資料:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

內容資料值必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-context-ltv.png)
