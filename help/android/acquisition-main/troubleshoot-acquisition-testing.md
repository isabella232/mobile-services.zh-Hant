---
description: 本主題提供有關如何在贏取測試期間，針對可能遇到的問題進行疑難排解的資訊。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud Services,Analytics
title: 疑難排解贏取測試
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# 疑難排解贏取測試 {#troubleshoot-acquisition-testing}

本主題提供有關如何在贏取測試期間，針對可能遇到的問題進行疑難排解的資訊。

* 若無其他規定，ADBMobileConfig.json 檔案應放置在 `assets` 資料夾中。

   名稱有大小寫之分，因此請勿使用大寫或小寫字母。

* 確認從主要活動中呼叫 `Config.setContext(this.getApplicationContext())`。

   如需詳細資訊，請參閱[設定方法](../configuration/methods.md)。

* 確認 `AndroidManifest.xml` 檔案中有 Mobile SDK 的必需權限:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果 ADMobileConfig.json 檔案中的 `referrerTimeout` 設為 5，您必須在應用程式安裝且初次啟動後，於 5 秒的時間範圍內傳送安裝目的，以查看附加至安裝點擊的反向連結資訊。

   若是手動測試，建議您將 `referrerTimeout` 增加到 10 至 15 秒，這樣您就有充足的時間在系統處理安裝點擊前傳送反向連結資訊。

* 執行[測試行銷連結贏取](t-testing-marketing-link-acquisition.md)中的所有步驟，並請務必先執行 `adb shell` 指令，然後再執行下列指令:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>若要正確處理反向連結目的，您必須個別執行這兩個指令。否則，`adb` 會雙重逸出反向連結資訊，且廣播接收器收到的資料將會不完整。
