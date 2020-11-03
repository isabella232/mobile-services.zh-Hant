---
description: '以下為 Android 資料庫所提供的贏取方法 '
keywords: android;library;mobile;sdk
seo-description: '以下為 Android 資料庫所提供的贏取方法 '
seo-title: 贏取方法
solution: Experience Cloud,Analytics
title: 贏取方法
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '82'
ht-degree: 100%

---


# 贏取方法{#acquisition-methods}

以下為 Android 資料庫所提供的贏取方法:

* **campaignStartForApp**

   就像使用者已按一下連結，讓開發者得以展開應用程式贏取促銷活動。此方法有助於建立手動贏取連結，並且可由您親自將應用程式商店重新導向。

   * 以下是此方法的語法:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
