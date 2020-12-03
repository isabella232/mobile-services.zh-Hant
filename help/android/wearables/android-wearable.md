---
description: 從 Android SDK 4.5 版開始，已新增新的 Android 延伸功能，可讓您透過 Android 穿戴式應用程式中收集資料。
seo-description: 從 Android SDK 4.5 版開始，已新增新的 Android 延伸功能，可讓您透過 Android 穿戴式應用程式中收集資料。
seo-title: Android 穿戴式裝置快速入門
solution: Experience Cloud,Analytics
title: Android 穿戴式裝置快速入門
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---


# Android 穿戴式裝置: 快速入門{#android-wearables-getting-started}

從 Android SDK 4.5 版開始，已新增新的 Android 延伸功能，可讓您透過 Android 穿戴式應用程式中收集資料。

## 設定手持式應用程式的 SDK (Android Studio) {#section_262237484EC44C58953891B105F0D000}

如需有關將 SDK 匯入專案的詳細資訊，請參閱[核心實施與生命週期](/help/android/getting-started/dev-qs.md)。

1. 將 `ADBMobileConfig.json` 檔案新增至專案的資產資料夾。
1. 將 `adobeMobileLibrary-*.jar` 檔案新增至 libs 資料夾，或確認該檔案已由專案參照。

   >[!TIP]
   >
   >新增 `.jar` 檔案後，您可能需要同步 Gradle 專案。

1. 在 `onCreate` 方法中，允許 SDK 透過 `Config.setContext` 存取應用程式內容:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. 將下列程式碼新增至 `AndroidManifest.xml` 檔案:

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 確認您的專案包含 Google play-services 資料庫。
1. 實施 `WearableListenerService` 或將對應的程式碼新增至 `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. 將 `WearListenerService` 新增至 `AndroidManifest.xml` 檔案:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## 設定穿戴式應用程式的 SDK (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. 完成下列其中一項作業:

   * 將相同的 `ADBMobileConfig.json` 檔案新增至穿戴式裝置專案的資產資料夾。
   * 變更 Gradle 設定以使用手持式應用程式資產資料夾中的 `ADBMobileConfig.json`:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. 將 `adobeMobileLibrary-*.jar` 檔案新增至 libs 資料夾，或確認其已由專案參照。

   新增 .jar 檔案後，您可能需要同步 Gradle 專案。

1. 在 `onCreate` 方法中，允許 SDK 透過 `Config.setContext` 存取應用程式內容:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. 將下列程式碼新增至 `AndroidManifest.xml`:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 確認您的專案包含 Google play-services 資料庫。
1. 實施 `WearableListenerService` 或將對應的程式碼新增至 `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. 將 `WearListenerService` 新增至 `AndroidManifest.xml` 檔案:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

