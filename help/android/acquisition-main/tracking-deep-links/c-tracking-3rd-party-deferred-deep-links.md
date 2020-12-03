---
description: 使用 Android SDK 來實施對第三方延期的深層連結的追蹤。
seo-description: 使用 Android SDK 來實施對第三方延期的深層連結的追蹤。
seo-title: 追蹤協力廠商延遲的深層連結
title: 追蹤協力廠商延遲的深層連結
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 80%

---


# 追蹤第三方延期的深層連結{#tracking-third-party-deferred-deep-links}

使用 Android SDK 來實施對第三方延期的深層連結的追蹤。

## 傳統 Adobe Mobile SDK 深層連結 {#section_D114FA1EB9664EAA82E036A990694B26}

Adobe Mobile SDK 目前支援的深層連結，可讓應用程式開發人員使用深層連結活動的 `collectLifecycleData` SDK API。SDK 會從深層連結 URL 參數中附加深層連結資料。如需深入連結在Adobe Mobile SDK中運作的詳細資訊，請參閱追蹤 [深入連結](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md)。

## Facebook 深層連結 {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

廣告創作者可以在 Facebook 中刊登廣告作為深層連結。當使用者按一下廣告時，會直接在應用程式中前往感興趣的資訊。深層連結&#x200B;**並非**&#x200B;指紋識別器 URL。然而，在廣告設定期間，您可以選擇提供協力廠商深層連結 URL。若應用程式開發人員使用 Adobe Mobile SDK 與服務，應在此欄位中輸入 Adobe Mobile Services 設定的指紋識別器 URL。如果所有項目皆已正確設定，則 Facebook SDK 會在應用程式安裝或啟動後，將此 URL 傳遞至應用程式。

## 設定SDK {#section_834CD3109175432B8173ECB6EA7DE315}

若要使用 Adobe Mobile SDK 準備新增 Facebook 深層連結支援，應用程式開發人員會完成下列作業:

* Android SDK 新手指南

   如需詳細資訊，請參閱 [Android SDK 新手指南](https://developers.facebook.com/docs/android/getting-started)。

* 設定深層連結

   如需詳細資訊，請參閱[深層連結設定](https://developers.facebook.com/docs/app-ads/deep-linking#os)。

如果應用程式已正確設定，則 `trackAdobeDeepLink()` API 應可從 Facebook 贏取促銷活動中收集深層連結資訊，並將其傳送至 Adobe Mobile Service。如果安裝點擊尚未在首次啟動時傳送至Adobe Mobile Service，則此資訊將新增至生命週期點擊。 否則，會以Adobe深層連結點擊的形式傳送。

>[!TIP]
>
>請確認深層連結 URL 擁有名稱為 `a.deeplink.id` 的索引鍵。如果該 URL 缺少深層連結 ID 參數，則 URL 參數將不會附加至內容資料。

如果該連結可歸屬於贏取，則 Adobe Mobile SDK 將會儲存 Facebook 深層連結的贏取資料 (原用於呼叫 `trackAdobeDeepLink()`。Adobe Mobile SDK日後推出時，將會提供此資料。 如果已註冊回呼，Adobe回呼也會用來將資料傳回用戶端。

## 在 Android 應用程式中啟用深層連結 {#section_64C15E269E89424B8E3D029F88094620}

1. 註冊應用程式以處理深層連結。

   如需詳細資訊，請參閱[允許其他應用程式啟動您的活動](https://developer.android.com/training/basics/intents/filters.html)。

1. 連結 Facebook SDK。

   若要在應用程式中新增 Facebook Gradle 相依性，請完成 [Android SDK 快速入門](https://developers.facebook.com/docs/android/getting-started)中的步驟。

1. 若要初始化 Facebook SDK，請完成 *Android Studio 設定*&#x200B;章節中的指示。
1. 從主要活動中呼叫 `trackAdobeDeepLink()`。

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

