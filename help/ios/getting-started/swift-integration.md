---
description: 只要使用 iOS Developer Library (iOS 開發人員資料庫) 中的「Mix and Match」(混合與配對) 功能，iOS 版 Adobe Mobile SDK 便可順暢地整合到 Swift 專案中。
seo-description: 只要使用 iOS Developer Library (iOS 開發人員資料庫) 中的「Mix and Match」(混合與配對) 功能，iOS 版 Adobe Mobile SDK 便可順暢地整合到 Swift 專案中。
seo-title: Swift 整合
solution: Experience Cloud,Analytics
title: Swift 整合
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '129'
ht-degree: 100%

---


# Swift 整合 {#swift-integration}

只要使用 iOS Developer Library (iOS 開發人員資料庫) 中的「Mix and Match」(混合與配對) 功能，iOS 版 Adobe Mobile SDK 便可順暢地整合到 Swift 專案中。

如需詳細資訊，請參閱[語言互通性](https://developer.apple.com/documentation/swift#2984801.html)。

舉例來說，使用文件中所述的橋接標題方法，即可匯入 Adobe Mobile iOS SDK 標題檔案：

```
#import “ADBMobile.h”
```

若要從 Swift 檔案中的 SDK 存取方法，請使用下列格式：

```
ADBMobile.{methodname}
```

