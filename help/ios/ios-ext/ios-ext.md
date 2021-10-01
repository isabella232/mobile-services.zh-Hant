---
description: 您可以使用 iOS 延伸功能，以便從 Apple Watch 應用程式 (WatchOS 1)、Today 介面工具集、照片編輯介面工具集及其他 iOS 延伸功能應用程式收集使用資料。
solution: Experience Cloud,Analytics
title: iOS 延伸功能實施
topic-fix: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
exl-id: 741b0cd5-6245-480a-b5bf-a33a1f82a425
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 100%

---

# iOS 延伸功能實施 {#ios-extension-implementation}

您可以使用 iOS 延伸功能，以便從 Apple Watch 應用程式 (WatchOS 1)、Today 介面工具集、照片編輯介面工具集及其他 iOS 延伸功能應用程式收集使用資料。

## 新版 Adobe Experience Platform Mobile SDK

在尋找 Adobe Experience Platform Mobile SDK 的相關資訊和文件嗎？按一下[這裡](https://aep-sdks.gitbook.io/docs/)以取得最新文件。

我們於 2018 年 9 月發行了全新的 SDK 主要版本。這些新的 Adobe Experience Platform Mobile SDK 可透過 [Experience Platform Launch](https://www.adobe.com/tw/experience-platform/launch.html) 設定。

* 若要開始使用，請前往 Adobe Experience Platform Launch。
* 若要查看 Experience Platform SDK 的儲存庫內容，請前往 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 對於使用 iOS SDK 而非自有包裝函式的建議 {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>我們強烈建議您使用 iOS SDK，而非您自己的包裝函式。

Apple 提供了一組 API，可讓 Watch 應用程式將要求傳送至容納應用程式並接收其回應，藉以與容納應用程式通訊。雖然您可以將追蹤資料以字典的形式從 Watch 應用程式傳送至容納應用程式，並且容納應用程式呼叫任何追蹤方法以傳送資料，但此解決方案有其限制。

在大部分的情況下，當使用者使用 Watch 應用程式時，容納應用程式會在背景執行，此時唯有呼叫 `TrackActionInBackground`、`TrackLocation` 及 `TrackBeacon` 是安全的。呼叫其他追蹤方法會干擾生命週期資料，所以若要從 Watch 應用程式傳送資料，您應該只使用這三個方法。

即使這三個追蹤方法已能滿足您的需求，仍應使用 iOS SDK，因為適用於 Watch 應用程式的 SDK 包含應用程式內傳訊之外的所有 Mobile 功能。

## 快速入門 {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>確保您擁有至少具備以下目標的專案:
>
>* 一個要包含應用程式的目標。
>* 一個擴充功能目標。

>


如果您使用 WatchKit 應用程式，則應該有第三個目標。如需 Apple Watch 開發的詳細資訊，請參閱 [Apple Watch 開發](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)。

## 設定容納應用程式 {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

在您的 Xcode 專案中完成以下步驟:

1. 將 AdobeMobileLibrary 資料夾拖曳到專案中。
1. 確認 `ADBMobileConfig.json` 檔案為容納應用程式目標的成員。
1. 在容納應用程式目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 開啟容納應用程式目標的&#x200B;**[!UICONTROL 功能]**&#x200B;標籤，啟用&#x200B;**[!UICONTROL 應用程式群組]**，然後新增應用程式群組 (例如 `group.com.adobe.testAp`)。

1. 在與 Adobe Mobile 資料庫所有互動前，請在應用程式委派的 `application:didFinishLaunchingWithOptions` 中設定應用程式群組:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 確認可建置應用程式且未發生非預期的錯誤。

## 設定擴充功能 {#section_28C994B7892340AC8D1F07AF26FF3946}

1. 確認 `ADBMobileConfig.json` 檔案為擴充功能目標的成員。
1. 在延伸功能目標的&#x200B;**[!UICONTROL 「建立階段」]**&#x200B;標籤中，展開&#x200B;**[!UICONTROL 「連結二進位檔與資料庫」]**&#x200B;區段，然後新增下列資料庫:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 開啟擴充功能目標的&#x200B;**[!UICONTROL 功能]**&#x200B;標籤，啟用&#x200B;**[!UICONTROL 應用程式群組]**，然後選取您在上述&#x200B;*設定容納應用程式*&#x200B;的步驟 4 中新增的應用程式群組。

1. 在與 Adobe Mobile 資料庫有所互動前，請在 InterfaceController 的 `awakeWithContext:` 中設定應用程式群組:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 確認可建置應用程式且未發生非預期的錯誤。

## 其他附註 {#section_21497E81231549CB9F164DEECFF5BA0D}

以下是一些要記住的資訊:

* 已新增一個額外內容資料值 `a.RunMode`，可指出資料來自容納應用程式還是延伸功能:

   * `a.RunMode = Application`

      此值表示該點擊來自容納應用程式。
   * `a.RunMode = Extension`

      此值表示該點擊來自延伸功能。

* 如果您從舊版的 SDK 升級，在啟動容納應用程式時，Adobe 會自動將所有使用者預設值和快取檔案從容納應用程式的資料夾移轉至應用程式群組的共用資料夾。
* 如果未曾啟動容納應用程式，則會捨棄擴充功能的點擊。
* 您的容納應用程式和擴充功能應用程式之間的版本號碼和組建號碼必須相同。
* 在 iOS 延伸功能應用程式中不會觸發任何生命週期呼叫。
