---
description: 本主題提供如何疑難排解贏取測試期間可能遇到的問題的資訊。
keywords: android;library;mobile;sdk
seo-description: 本主題提供如何疑難排解贏取測試期間可能遇到的問題的資訊。
seo-title: 疑難排解贏取測試
solution: Marketing Cloud,Analytics
title: 疑難排解贏取測試
topic: 開發人員和實施
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 疑難排解贏取測試 {#troubleshoot-acquisition-testing}

本主題提供如何疑難排解贏取測試期間可能遇到的問題的資訊。

* 若未指定，ADBMobileConfig.json檔案應放置在資料夾 `assets` 中。

   名稱區分大小寫，因此請勿使用大寫或小寫字母。

* 請確定 `Config.setContext(this.getApplicationContext())` 是從您的主要活動呼叫。

   如需詳細資訊，請參 [閱設定方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 請確定檔案中有Mobile SDK的必要權限 `AndroidManifest.xml` :

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果 `referrerTimeout` 在ADMobileConfig.json檔案中設為5，您必須在應用程式第一次安裝並啟動後的5秒時間範圍內傳送安裝意圖，才能查看附加至安裝點擊的反向連結資訊。

   For manual testing, we recommend that you increase the  to 10-15 seconds, so that you have sufficient time to send the referrer information before the install hit is processed.`referrerTimeout`

* 執行測試 [Marketing link贏取中的所有步驟](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) ，並確定您先 `adb shell` 執行命令，然後執行下列：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>若要正確處理反向連結意圖，您必須獨立執行這兩個命令。 Otherwise  will double escape the referrer information and the data received by the broadcast receiver will be incomplete.`adb`

