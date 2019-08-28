---
description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile Android SDK 追蹤深層連結和延期的深層連結。
keywords: Android；資料庫；行動；sdk
seo-description: 您可以使用此資訊，在行動應用程式中利用 Adobe Mobile Android SDK 追蹤深層連結和延期的深層連結。
seo-title: 追蹤Adobe Mobile Services中的深層連結
solution: Marketing Cloud、Analytics
title: 追蹤深層連結
topic: 開發人員和實施
uuid: ebb1c08c-a246-40b3-9ac6-4606a14 b4 c5 a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

您可以使用此資訊，在行動應用程式中利用 Adobe Mobile Android SDK 追蹤深層連結和延期的深層連結。

## 追蹤深層連結

1. 新增 SDK 至您的專案，並實施生命週期量度。

   如需詳細資訊，請參閱&#x200B;*在核心實作與生命週期中，將SDK和設定檔新增至IntelliJ* [IDEA或Eclipse專案](/help/android/getting-started/dev-qs.md)。

1. 註冊應用程式以處理 URL。

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
1. 透過使用 `collectLifecycleData` 將搭配深層連結目的的活動傳遞至 Adobe SDK。

   以下為追蹤深層連結的範例:

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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

此外，您可以附加下列一或多個保留索引鍵(使用使用者產生的值)至深層或通用連結：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

這些鍵值皆為預先對應的變數，用於在 Adobe Analytics 中報告。如需對應與處理規則的詳細資訊，請參閱[處理規則和內容資料](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

## 追蹤延遲深層連結(用於行銷連結)

在延期的深層連結中，Adobe SDK 會開啟含有深層連結的新目的，作為目的資料。會使用上述程式碼，將此程序當作外部深層連結來處理。

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### 常數

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

