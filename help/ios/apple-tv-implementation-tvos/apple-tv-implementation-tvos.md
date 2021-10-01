---
description: 此資訊可協助您使用 tvOS 實施 Apple TV。
solution: Experience Cloud,Analytics
title: 使用 tvOS 實施 Apple TV
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# 使用 tvOS 實施 Apple TV {#apple-tv-implementation-with-tvos}

此資訊可協助您使用 tvOS 實施 Apple TV。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

透過 Apple TV，您現在可以建立應用程式以在原生 tvOS 環境中執行。在 iOS 提供的數個架構中，您可以使用任一架構來建立原生應用程式，或使用 XML 範本和 JavaScript 建立您的應用程式。

>[!TIP]
>
>tvOS 僅支援 `AdobeMobileLibrary` 4.7.0 以上版本。

## 快速入門 {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>我們會假設您的專案目標是可在 tvOS 中執行的 Apple TV 應用程式。如需詳細資訊，請參閱 [tvOS](https://developer.apple.com/tvos/documentation/)。

## 設定 tvOS 的原生應用程式 {#section_5095F19B3C4545F68E8C1E37A7E303AE}

在您的 Xcode 專案中完成以下步驟:

1. 將 AdobeMobileLibrary 資料夾拖曳到專案中。
1. 確認 `ADBMobileConfig.json` 檔案為目標的成員。
1. 在 tvOS 應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

如需詳細資訊，請參閱有關 [iOS](https://developer.apple.com/ios/resources/) 的文件。

## 設定 tvOS 的 TVML/TVJS 應用程式 {#section_AB2EC8C326654F3387658EBBD990BB12}

1. 將 `AdobeMobileLibrary` 資料夾拖曳到專案中。
1. 確認 `ADBMobileConfig.json` 檔案為目標的成員。
1. 在 tvOS 應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. 在 `TVApplicationControllerDelegate` 類別的實施檔案中，匯入 SDK。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 在 `TVApplicationControllerDelegate` 類別的 `application:didFinishLaunchWithOptions:` 方法中，使用 `installTVMLHooks:` 方法將 `TVApplicationController` 物件傳遞至 SDK。

   Adobe SDK 需要存取應用程式的 `TVApplicationController` 以將其本身註冊至應用程式的 JSContext 中。此步驟可讓您從 JavaScript 檔案呼叫 Adobe SDK 中的原生方法。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. 在 JavaScript 檔案中，使用 `ADBMobile` 物件存取 Adobe SDK 的原生方法。

   如需可用方法的完整清單，請參閱 [TVJS 方法](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md)。
