---
description: 只要使用 iOS Developer Library (iOS 開發人員資料庫) 中的「Mix and Match」(混合與配對) 功能，iOS 版 Adobe Mobile SDK 便可順暢地整合到 Swift 專案中。
solution: Experience Cloud Services,Analytics
title: Swift 整合
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Swift 整合 {#swift-integration}

只要使用 iOS Developer Library (iOS 開發人員資料庫) 中的「Mix and Match」(混合與配對) 功能，iOS 版 Adobe Mobile SDK 便可順暢地整合到 Swift 專案中。

如需詳細資訊，請參閱[語言互通性](https://developer.apple.com/documentation/swift#2984801.html)。

舉例來說，使用文件中所述的橋接標題方法，即可匯入 Adobe Mobile iOS SDK 標題檔案：

```
#import "ADBMobile.h"
```

若要從 Swift 檔案中的 SDK 存取方法，請使用下列格式：

```
ADBMobile.{methodname}
```
