---
description: 期限值可讓您測量每個使用者的期限值並將其設為目標。
seo-description: 期限值可讓您測量每個使用者的期限值並將其設為目標。
seo-title: 訪客期限值
solution: Marketing Cloud、Analytics
title: 訪客期限值
topic: 開發人員和實施
uuid: d830d18b-4313-43bb-8d75-37889869d0f1d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

期限值可讓您測量每個使用者的期限值並將其設為目標。

每次您以 `trackLifetimeValueIncrease` 傳送一個值時，就會將該值新增至現有值。期限值儲存在裝置上，且可透過呼叫 `lifetimeValue` 隨時擷取。此值可用來儲存期限購買數、廣告檢視次數、視訊完成次數、社交分享和照片上傳數等等。

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期中的新增SDK和設定檔案至您的專案*[](/help/ios/getting-started/dev-qs.md)。
1. 匯入資料庫:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. 以要增加值的量呼叫 `trackLifetimeValueIncrease`:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了期限值之外，您還可以傳送隨著每次追蹤動作呼叫傳送其他內容資料:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

上下文資料值必須映射至自訂變數：

![](assets/map-variable-context-ltv.png)

