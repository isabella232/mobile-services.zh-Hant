---
description: 自 iOS 10 開始，Apple 可讓您建立獨立延伸功能，該功能無須容納應用程式即可發佈。有了此延伸功能，您便不需要應用程式群組，因為沒有要共用資料的容納應用程式。
seo-description: 自 iOS 10 開始，Apple 可讓您建立獨立延伸功能，該功能無須容納應用程式即可發佈。有了此延伸功能，您便不需要應用程式群組，因為沒有要共用資料的容納應用程式。
seo-title: 獨立延伸功能實施
solution: Experience Cloud,Analytics
title: 獨立延伸功能實施
topic: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---


# 獨立擴充功能實施 {#stand-alone-extension-implementation}

自 iOS 10 開始，Apple 可讓您建立獨立延伸功能，該功能無須容納應用程式即可發佈。有了此延伸功能，您便不需要應用程式群組，因為沒有要共用資料的容納應用程式。

>[!IMPORTANT]
>
>若要使用獨立擴充功能，您必須有 Mobile SDK 4.13.0 版或更新版本。

## 設定獨立延伸功能與 SDK 搭配使用 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

設定獨立延伸功能:

1. 確認 `ADBMobileConfig.json` 檔案為擴充功能目標的成員。
1. 連結下列資料庫與架構:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 在延伸功能的主要檢視控制器中，為 SDK 中的 `ADBMobileAppExtensionTypeStandAlone` 設定延伸功能類型，再完成任何 SDK 相關活動。

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. 確認可建置應用程式且未發生非預期的錯誤。

## 其他附註 {#section_1C9A55E2309A44BF842310F735702B3D}

以下為部分其他資訊:

* 已新增一個額外內容資料值 `a.RunMode`，可指出資料來自容納應用程式還是延伸功能:

   * `a.RunMode = Application`

      此值表示該點擊來自容納應用程式。
   * `a.RunMode = Extension`

      此值表示該點擊來自延伸功能。

* 在 iOS 延伸功能應用程式中不會觸發任何生命週期呼叫。

