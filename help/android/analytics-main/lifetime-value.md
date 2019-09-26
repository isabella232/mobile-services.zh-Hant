---
description: 期限值可讓您測量每個 Android 使用者的期限值並將其設為目標。此值可用來儲存期限購買數、廣告檢視次數、視訊完成次數，社交分享，照片上傳數等等。
seo-description: 期限值可讓您測量每個 Android 使用者的期限值並將其設為目標。此值可用來儲存期限購買數、廣告檢視次數、視訊完成次數，社交分享，照片上傳數等等。
seo-title: 訪客期限值
solution: Marketing Cloud,Analytics
title: 訪客期限值
topic: 開發人員和實施
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Visitor lifetime value {#visitor-lifetime-value}

期限值可讓您測量每個 Android 使用者的期限值並將其設為目標。此值可用來儲存期限購買數、廣告檢視次數、視訊完成次數，社交分享，照片上傳數等等。

每次您以 `trackLifetimeValueIncrease` 傳送一個值時，就會將該值新增至現有值。期限值儲存在裝置上，且可透過呼叫 `lifetimeValue` 隨時擷取。

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 將[程式庫新增至您的專案並實施生命週期。

   如需詳細資訊，請 *參閱核心實作和生命週期中的新增SDK和設定檔至IntelliJ IDEA或Eclipse*[專案](/help/android/getting-started/dev-qs.md)。
1. 匯入程式庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 以要增加值的量呼叫 `trackLifetimeValueIncrease`:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了期限值之外，您還可以隨著每次追蹤動作呼叫傳送其他內容資料:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

內容資料值必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-context-ltv.png)

