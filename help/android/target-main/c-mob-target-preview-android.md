---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-title: 在 Android 裝置上預覽目標
title: 在 Android 裝置上預覽目標
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# 在 Android 裝置上預覽目標 {#target-preview-on-android}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/zh-Hant/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>如要使用 Target 預覽功能，需使用 SDK 4.14.0 或更新版本。

* **setPreviewRestartDeeplink**

   設定在「預覽」模式中套用預覽選取範圍時，會因此觸發的應用程式深層連結。

   * 此方法的語法如下：

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

