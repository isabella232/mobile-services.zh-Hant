---
description: 可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 App Store 下載並執行應用程式後，SDK 就會自動收集贏取資料，並傳送至 Adobe Mobile Services。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 行動應用程式贏取
topic-fix: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
exl-id: 266f0266-38f5-410b-ae14-92874fb0e7ce
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 100%

---

# 行動應用程式贏取  {#mobile-app-acquisition}

可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 App Store 下載並執行應用程式後，SDK 就會自動收集贏取資料，並傳送至 Adobe Mobile Services。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>若要使用 Acquisition，您&#x200B;**必須**&#x200B;有 SDK 4.1 版或更新版本。

贏取連結必須在 Adobe Mobile Services 中建立。如需詳細資訊，請參閱[贏取](/help/using/acquisition-main/acquisition-main.md)。

**在 SDK 4.18.0 版及更新版本中**：

自 2020 年 3 月 1 日開始，Google 將終止支援 install_referrer 意圖廣播機制。如需詳細資訊，請參閱[仍使用 InstallBroadcast 嗎？在 2020 年 3 月 1 日前切換至 Play Referrer API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)。若要繼續從 Google Play 商店收集安裝反向連結資訊，請更新您的應用程式以使用 SDK 4.18.0 版或更新版本。

隨著支援終止，您必須從新的 Google API 收集安裝反向連結 URL，並將產生的 URL 傳遞至 SDK，而不是建立 `BroadcastReceiver`。

1. 將 Google Play Install Referrer 套件新增至您的 Gradle 檔案的相依項目：

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. 若要從 Install Referrer API 擷取反向連結 URL，請完成[取得安裝反向連結](https://developer.android.com/google/play/installreferrer/library#install-referrer)中的步驟。

1. 將反向連結 URL 傳遞至 SDK：

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>為避免應用程式發出不必要的 API 呼叫，Google 建議您只在安裝後立即叫用 API 一次。

若要決定在應用程式中使用 Google Play Install Referrer API 的最佳方式，請參閱 Google 的文件。以下是如何將 Adobe SDK 搭配 Google Play Install Referrer API 使用的範例：

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**在 SDK 4.13.1 版及更新版本中**：

如果您無法使用在 Adobe Mobile Services 中建立的贏取連結，仍可透過 Google Play Acquisition 由 SDK 收集和傳送贏取資料。

收集來自標準 Google Play Acquisition 促銷活動的贏取資料：

* 使用標準 Google Play 商店贏取方法。

   自訂贏取資料可與標準 Google Play Acquisition 鍵值值組搭配使用。

* 當使用者因 Google Play 商店贏取而下載和執行應用程式時，系統將會收集反向連結的資料，並傳送至 Adobe Mobile Services。

   * 該資料會儲存於先前透過 SDK 註冊的 `AdobeDataCallback` 例項，以供日後使用。

      如需詳細資訊，請參閱[設定方法](/help/android/configuration/methods.md)。

   * 系統會使用 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 或 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 事件類型。

   * 屬於 Google Play 贏取資料一部分的自訂鍵值將會使用`a.acquisition.custom.`「」建立命名空間。

如果您有使用在 Adobe Mobile Services 中建立的贏取連結，請完成下列作業，新增自訂資料至贏取連結：

1. 為贏取變數加上前置詞`adb`「。

   首次啟動時，SDK 從 Adobe Mobile Services 收到的贏取資料會儲存，並可在先前向 SDK 註冊的 `AdobeDataCallback` 執行個體中使用。如需詳細資訊，請參閱[設定方法](/help/android/configuration/methods.md)。

1. 系統將會使用 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 或 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 事件類型。

1. 自訂資料索引鍵會加上前置詞「`a.acquisition.custom.`」

>[!TIP]
>
>如果您要傳送資料至多個報表套裝，請在報表套裝 ID 清單中，使用與第一個報表套裝關聯之應用程式的贏取資料。

本節中的更新可讓 SDK 透過贏取連結傳送贏取資料。

## 追蹤行動裝置贏取 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 新增資料庫至您的專案與實作生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫：

   ```java
   import com.adobe.mobile.*;
   ```

1. 針對反向連結實作 `BroadcastReceiver`：

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. 更新 `AndroidManifest.xml` 以啟用前述步驟中建立的 `BroadcastReceiver`：

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含必要的贏取設定：

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >如果您要傳送資料至多個報表套裝，請在報表套裝 ID 清單中，使用與第一個報表套裝關聯之應用程式的贏取設定 (贏取伺服器與 appid)。

   `acquisition`設定是由 Adobe Mobile Services 產生，且不可變更。如需有關如何下載自訂 `ADBMobileConfig.json` 檔案和預先設定之`acquisition`設定的詳細資訊，請參閱[開始之前](/help/android/getting-started/requirements.md)。

啟用這些設定後，贏取資料會在應用程式初次啟動後，自動透過初始生命週期呼叫傳送。

>[!CAUTION]
>
>`referrerTimeout` 值必須設定高於 0，才可啟用應用程式贏取。
