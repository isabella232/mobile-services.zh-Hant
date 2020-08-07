---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-title: 在 iOS 裝置上預覽目標
title: 在 iOS 裝置上預覽目標
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 87%

---


# 在 iOS 裝置上預覽目標{#target-preview-on-ios}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

如需設定與使用 Target 預覽功能的詳細資訊，請參閱 [Target 行動裝置預覽](https://docs.adobe.com/content/help/zh-Hant/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

>[!IMPORTANT]
>
>如要使用 Target 預覽功能，需使用 SDK 4.14.0 或更新版本。

## Target 預覽方法

* **setPreviewRestartDeeplink**

   設定在「預覽」模式中套用預覽選取範圍時，將觸發的應用程式預覽。

   * 以下是此方法的語法:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 以下是此方法的範例程式碼：

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
