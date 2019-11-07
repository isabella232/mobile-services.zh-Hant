---
description: 下列資訊可協助您進行贏取測試問題疑難排解。
keywords: android;贏取;測試
seo-description: 下列資訊可協助您進行贏取測試問題疑難排解。
seo-title: 疑難排解贏取測試
solution: Marketing Cloud,Analytics
title: 疑難排解贏取測試
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# 疑難排解贏取測試 {#aquistion-testing-troubleshooting}

以下是測試贏取時可能會遇到的一些問題，以及一些可能的解決方案:

* 若無其他規定，ADBMobileConfig.json 檔案應放置在資產資料夾中。

* 名稱有大小寫之分，因此請勿提供小寫字母的名稱。

   您必須確保從主要活動中呼叫 `Config.setContext(this.getApplicationContext())`。如需詳細資訊，請參閱[設定方法](https://docs.adobe.com/content/help/zh-Hant/mobile-services/android/configuration-android/methods.html)。

* 提供的 AndroidManifest.xml 檔案中有一些使用者權限遺失，這些是傳送資料和記錄離線追蹤呼叫所需的權限:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在設定中，如果反向連結逾時設為 `referrerTimeout: 5`，表示您必須在應用程式安裝且初次啟動後，於 5 秒的時間範圍內傳送安裝目的，以查看附加至安裝點擊的反向連結資訊。

   若是手動測試，請將 `referrerTimeout` 增加到 10 至 15 秒，這樣就有足夠的時間在系統處理安裝點擊前傳送反向連結資訊。

* 請務必依序執行[測試行銷連結贏取](https://docs.adobe.com/content/help/zh-Hant/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)中的所有步驟，並確認您執行 `adb` 殼層，然後執行下列指令:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>您必須個別執行這兩個指令，才能正確處理反向連結目的。否則，`adb` 會雙重逸出反向連結資訊，且廣播接收器收到的資料將會不完整。
