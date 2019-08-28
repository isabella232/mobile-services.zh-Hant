---
description: 本主題提供如何疑難排解贏取測試期間可能遇到問題的資訊。
keywords: Android；資料庫；行動；sdk
seo-description: 本主題提供如何疑難排解贏取測試期間可能遇到問題的資訊。
seo-title: 疑難排解贏取測試
solution: Marketing Cloud、Analytics
title: 疑難排解贏取測試
topic: 開發人員和實施
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 疑難排解贏取測試 {#troubleshoot-acquisition-testing}

本主題提供如何疑難排解贏取測試期間可能遇到問題的資訊。

* 如果未另行指定，則應將ADBMobileConfig. json檔案放置在 `assets` 資料夾中。

   名稱區分大小寫，因此請勿使用大寫字母或小寫字母。

* 確保從 `Config.setContext(this.getApplicationContext())` 主要活動中呼叫。

   如需詳細資訊，請參閱 [設定方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 請確定 `AndroidManifest.xml` 檔案中存在Mobile SDK的必要權限：

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果 `referrerTimeout` 在ADMobileConfig. json檔案中設定為5，您必須在應用程式安裝並首次啓動後，於秒內傳送安裝意圖，才會看到附加至安裝點擊的反向連結資訊。

   對於手動測試，建議您增加 `referrerTimeout` 至10-15秒，如此您就有足夠的時間來傳送反向連結資訊，以便在安裝點擊處理前傳送。

* 執行 [「測試行銷連結」贏取中的所有步驟](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) ，並確保您先執行 `adb shell` 命令，然後再執行下列動作：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>若要正確處理反向連結意圖，您必須獨立執行這兩個命令。否則 `adb` 會再次逸出反向連結資訊，而廣播接收器收到的資料將不完整。

