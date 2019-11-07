---
description: iBeacon 追蹤可讓您透過 iBeacon 和低功耗藍牙來測量微位置並以其為目標。
seo-description: iBeacon 追蹤可讓您透過 iBeacon 和低功耗藍牙來測量微位置並以其為目標。
seo-title: iBeacon 追蹤
solution: Marketing Cloud,Analytics
title: iBeacon 追蹤
topic: 開發人員和實施
uuid: 390883db-027e-4d12-8a16-86d514579db1
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# iBeacon 追蹤 {#ibeacon-tracking}

iBeacon 追蹤可讓您透過 iBeacon 和低功耗藍牙來測量微位置並以其為目標。

呼叫 `trackBeacon` 時，會傳送下列信標資料至 Analytics 和 Target:

* `a.beacon.uuid` – 信標的 ProximityUUID
* `a.beacon.major` – 主要信標編號，例如商店編號
* `a.beacon.minor` – 次要信標編號，例如商店內的唯一編號
* `a.beacon.prox` – 下列值代表使用者與信標之間的距離範圍:

   * `0` 為未知
   * `1` 為極近
   * `2` 為附近
   * `3` 為遠距

## 追蹤 iBeacon {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔案至您的專案*。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 當裝置位於信標的鄰近範圍內時，請呼叫 `trackBeacon`:

   ```objective-c
   [ADBMobile trackBeacon:beacon data:nil];
   ```

1. 當使用者離開信標鄰近範圍時，請清除目前的信標:

   ```objective-c
   [ADBMobile trackingClearCurrentBeacon];
   ```

## 傳送其他資料 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了計時動作名稱之外，您還可以隨著每次追蹤動作呼叫傳送其他內容資料:

```objective-c
[ADBMobile trackBeacon:beacon data:@{@"myapp.ImageLiked" : imageName}];
```

內容資料值必須對應至自訂變數:

![](assets/map-variable-context-ltv.png)

## 範例 {#section_9749238BCBC148998CB18E97D7670D19}

```objective-c
- (void)locationManager:(CLLocationManager *)manager didRangeBeacons:(NSArray *)beacons inRegion:(CLBeaconRegion *)region { 
    if (beacons.count > 0) { 
        CLBeacon *beacon = beacons[0]; 
        // Adobe - track when in range of a beacon 
        [ADBMobile trackBeacon:beacon data:@{@"sampleContextData" : @"sampleContextDataVal"}]; 
    } 
} 
 
// When the user leaves the proximity of the beacon, clear the current beacon 
[ADBMobile trackingClearCurrentBeacon];
```

