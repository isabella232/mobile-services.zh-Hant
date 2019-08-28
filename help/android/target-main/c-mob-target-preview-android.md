---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-title: 在 Android 裝置上預覽目標
title: 在 Android 裝置上預覽目標
uuid: f3c82d64-009c-4929-a5 e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# 在 Android 裝置上預覽目標 {#target-preview-on-android}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

如需設定與使用目標預覽功能的詳細資訊，請前往[目標行動預覽](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

>[!IMPORTANT]
>
>若要使用Target Preview，您需要SDK4.14.0版或更新版本。

* **setPreviewRestartDeeplink**

   設定應用程式深層連結，只要在預覽模式中套用預覽選項，該深層連結就會觸發。

   * 以下是此方法的語法:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

