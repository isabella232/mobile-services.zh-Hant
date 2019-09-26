---
description: 此資訊可協助您使用 tvOS 實施 Apple TV。
seo-description: 此資訊可協助您使用 tvOS 實施 Apple TV。
seo-title: 使用 tvOS 實施 Apple TV
solution: Marketing Cloud,Analytics
title: 使用 tvOS 實施 Apple TV
topic: 開發人員和實施
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

此資訊可協助您使用 tvOS 實施 Apple TV。

## 全新Adobe Experience Platform Mobile SDK版本

正在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎? 按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們在 2018 年 9 月時發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 設定。

* 若要開始，請前往Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往[ Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

透過 Apple TV，您現在可建立應用程式在原生 tvOS 環境中執行。您可使用 iOS 提供的數個架構來建立原生應用程式，或可以使用 XML 範本和 JavaScript 來建立您的應用程式。

>[!TIP]
>
>tvOS支援從4.7.0 `AdobeMobileLibrary` 版開始提供。

## 入門 {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>我們假設您的專案有一個目標，即是針對tvOS的Apple TV應用程式。 如需詳細資訊，請參閱 [tvOS](https://developer.apple.com/tvos/documentation/)。

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

在您的 Xcode 專案中完成以下步驟:

1. 將 AdobeMobileLibrary 資料夾拖曳到專案中。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. 在 tvOS 應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

如需詳細資訊，請參閱有關 [iOS](https://developer.apple.com/ios/resources/) 的文件。

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. 將 `AdobeMobileLibrary` 資料夾拖曳到專案中。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. 在 tvOS 應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**「連結二進位檔與資料庫」]區段，然後新增下列資料庫:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. 在 `TVApplicationControllerDelegate` 類別的實施檔案中，匯入 SDK。

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Adobe SDK 需要存取應用程式的 `TVApplicationController` 以將其本身註冊至應用程式的 JSContext 中。此步驟可讓您從 JavaScript 檔案呼叫 Adobe SDK 中的原生方法。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. 在 JavaScript 檔案中，使用 `ADBMobile` 物件存取 Adobe SDK 的原生方法。

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

