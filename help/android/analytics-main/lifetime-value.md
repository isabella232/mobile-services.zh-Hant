---
description: 期限值可讓您測量並定位每個Android使用者的期限值。 此值可用來儲存期限購買、廣告檢視、視訊完成、社交分享、像片上傳等。
seo-description: 期限值可讓您測量並定位每個Android使用者的期限值。 此值可用來儲存期限購買、廣告檢視、視訊完成、社交分享、像片上傳等。
seo-title: 訪客期限值
solution: Marketing Cloud,Analytics
title: 訪客期限值
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 52%

---


# 訪客期限值 {#visitor-lifetime-value}

期限值可讓您測量並定位每個Android使用者的期限值。 此值可用來儲存期限購買、廣告檢視、視訊完成、社交分享、像片上傳等。

每次您以 `trackLifetimeValueIncrease` 傳送一個值時，就會將該值新增至現有值。期限值儲存在裝置上，且可透過呼叫 `lifetimeValue` 隨時擷取。

## 追蹤訪客期限值 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。
1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 以要增加值的量呼叫 `trackLifetimeValueIncrease`:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## 傳送其他資料 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了期限值之外，您還可以隨著每次追蹤動作呼叫傳送其他內容資料:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

內容資料值必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-context-ltv.png)

