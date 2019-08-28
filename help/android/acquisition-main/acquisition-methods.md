---
description: '以下為 Android 資料庫所提供的贏取方法 '
keywords: Android；資料庫；行動；sdk
seo-description: '以下為 Android 資料庫所提供的贏取方法 '
seo-title: 贏取方法
solution: Marketing Cloud、Analytics
title: 贏取方法
topic: 開發人員和實施
uuid: 22ec432f-e7 ae-4e89-be07-26206bbacf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

Android程式庫提供下列贏取方法：

* **campaignStartForApp**

   就像使用者已按一下連結，讓開發者得以展開應用程式贏取促銷活動。此方法有助於建立手動贏取連結，並且可由您親自將應用程式商店重新導向。

   * 以下是此方法的語法:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
