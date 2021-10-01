---
description: 目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。
title: 在 iOS 裝置上預覽目標
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# 在 iOS 裝置上預覽目標{#target-preview-on-ios}

目標預覽功能可協助您輕鬆執行目標活動的端對端 QA，並在裝置上預覽這些活動。

如需設定與使用目標預覽功能的詳細資訊，請參閱Adobe Target檔案中的[Target行動裝置預覽](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

>[!IMPORTANT]
>
>如要使用 Target 預覽功能，需使用 SDK 4.14.0 或更新版本。

## Target 預覽方法

* **setPreviewRestartDeeplink**

   設定在「預覽」模式中套用預覽選取範圍時，會因此觸發的應用程式深層連結。

   * 此方法的語法如下：

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
