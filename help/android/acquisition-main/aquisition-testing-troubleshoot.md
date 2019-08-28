---
description: 下列資訊可協助您疑難排解贏取測試問題。
keywords: Android；收購；測試
seo-description: 下列資訊可協助您疑難排解贏取測試問題。
seo-title: 疑難排解贏取測試
solution: Marketing Cloud、Analytics
title: 疑難排解贏取測試
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# 疑難排解贏取測試 {#aquistion-testing-troubleshooting}

以下是測試「贏取」和一些可能解決方案時可能遇到的問題：

* 如果未另行指定，則ADBMobileConfig. json檔案應放置在資產資料夾中。

* 名稱區分大小寫，因此不提供小寫字母。

   您必須確保從 `Config.setContext(this.getApplicationContext())` 主要活動中呼叫。如需詳細資訊，請參閱 [設定方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 提供的Social檔案中缺少一些使用者權限，因此傳送資料和記錄離線追蹤呼叫時需要這些功能：

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在您的組態中，如果反向連結逾時設定為 `referrerTimeout: 5`，表示您必須在應用程式安裝並首次啓動後，於秒內傳送安裝意圖，才會看到附加至安裝點擊的反向連結資訊。

   若要手動測試，請將 `referrerTimeout` 至10-15秒的時間增加，如此在安裝點擊前，就有足夠的時間傳送反向連結資訊。

* 請務必在 [「測試行銷連結」贏取中](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 執行所有步驟，並確定您執行 `adb` 殼層後再執行下列動作：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>您必須單獨執行這兩個命令，才能正確處理反向連結意圖。否則，會 `adb` 使反向連結資訊逸出，而廣播接收器收到的資料將不完整。
