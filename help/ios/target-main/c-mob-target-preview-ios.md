---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
seo-title: 在 iOS 裝置上預覽目標
title: 在 iOS 裝置上預覽目標
uuid: d92867a4-0569-4732-a928-28f9 e2 f8 b21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 在 iOS 裝置上預覽目標{#target-preview-on-ios}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>若要使用Target Preview，您需要SDK4.14.0版或更新版本。

## 目標預覽方法

* **setPreviewRestartDeeplink**

   設定應用程式深層連結，只要在預覽模式中套用預覽選項，該深層連結就會觸發。

   * 以下是此方法的語法:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
