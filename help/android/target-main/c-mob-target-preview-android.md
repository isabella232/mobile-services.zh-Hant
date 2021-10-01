---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
title: 在 Android 裝置上預覽目標
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# 在 Android 裝置上預覽目標 {#target-preview-on-android}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

如需設定與使用目標預覽功能的詳細資訊，請前往Adobe Target使用手冊中的[目標行動裝置預覽](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

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
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
