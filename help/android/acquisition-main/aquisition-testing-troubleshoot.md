---
description: 下列資訊可協助您疑難排解贏取測試問題。
keywords: android；贏取；測試
seo-description: 下列資訊可協助您疑難排解贏取測試問題。
seo-title: 疑難排解贏取測試
solution: Marketing Cloud,Analytics
title: 疑難排解贏取測試
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# 疑難排解贏取測試 {#aquistion-testing-troubleshooting}

以下是您在測試「贏取」和一些可能的解決方案時可能會遇到的一些問題：

* 若未另行指定，ADBMobileConfig.json檔案應放在資產資料夾中。

* 名稱區分大小寫，因此請勿在小寫字母中提供名稱。

   您需要確保從主 `Config.setContext(this.getApplicationContext())` 要活動呼叫此項。 如需詳細資訊，請參 [閱設定方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 提供的AndroidManifest.xml檔案中遺失一些使用者權限，這些權限是傳送資料並記錄離線追蹤呼叫的必要條件：

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在您的設定中，如果反向連結逾時設為 `referrerTimeout: 5`，這表示您必須在應用程式第一次安裝並啟動後的5秒時間範圍內傳送安裝意圖，以查看附加至安裝點擊的反向連結資訊。

   若是手動測試，請 `referrerTimeout` 將值增加至10-15秒，如此在處理安裝點擊之前就有足夠的時間傳送反向連結資訊。

* 請務必依序執行 [Testing Marketing Link贏取中的所有步驟](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) ，並確定您先執行 `adb` shell，然後執行下列步驟：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>您必須獨立執行這兩個命令，才能正確處理反向連結意圖。  否則， `adb` 重複逸出反向連結資訊，廣播接收器所接收的資料將不完整。
