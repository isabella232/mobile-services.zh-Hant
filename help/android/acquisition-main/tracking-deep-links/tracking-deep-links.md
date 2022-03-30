---
description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile Android SDK 追蹤深層連結和延期的深層連結。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 追蹤深層連結
topic-fix: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
exl-id: 4f59b77d-3cac-4853-bb6b-50a403036771
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 97%

---

# 追蹤深層連結

您可以使用此資訊，在行動應用程式中利用 Adobe Mobile Android SDK 追蹤深層連結和延期的深層連結。

## 追蹤深層連結

1. 新增 SDK 至您的專案，並實作生命週期量度。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 註冊應用程式以處理 URL。

   如需詳細資訊，請參閱 [URL](https://developer.android.com/training/basics/intents/filters.html)。
1. 透過使用 `collectLifecycleData` 將搭配深層連結目的的活動傳遞至 Adobe SDK。

   追蹤深層連結的範例如下：

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

只要連結中包含附有 `a.deeplink.id` 標籤的索引鍵，以及使用者自行產生的非空對應數值，Adobe Mobile SDK 就可剖析附加至任何深層或通用連結之資料的索引鍵/值組。只要連結包含 `a.deeplink.id` 鍵值和值，所有附加至連結之資料的鍵值和值組都會經過剖析、附加至生命週期點擊，然後傳送至 Adobe Analytics。

此外，您可以將下列其中一或多組保留的索引鍵 (搭配使用者產生的值) 附加至深層或通用連結：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

這些鍵值皆為預先對應的變數，用於在 Adobe Analytics 中報告。如需對應與處理規則的詳細資訊，請參閱[處理規則和內容資料](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

## 追蹤延期的深層連結 (與行銷連結搭配使用)

透過延期的深層連結，Adobe SDK 能開啟新的目的，並以深層連結作為目的資料。系統會使用上述程式碼，以外部深層連結形式處理此程序。

## 深層連結公開資訊 {#section_1815396353614DA8A63D8D92112217E7}

### 常數

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```
