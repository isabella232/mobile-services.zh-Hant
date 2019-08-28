---
description: 'null'
seo-description: 'null'
seo-title: 開發人員快速入門
solution: Marketing Cloud、Analytics
title: 開發人員快速入門
topic: 開發人員和實施
uuid: 11c06fcf-d5 e4-4858-9a4 e-3bc66 cdd2 a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

以下是如何實作Universal Windows Platform程式庫的一些資訊。

>[!IMPORTANT]
>
>若要實作SDK，您需要Visual Studio2013或更新版本。

## 取得 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. 您也會有 `ADBMobileConfig.json` 檔案。如需此檔案的詳細資訊，請參閱 [ADBMobileConfig. json config檔案](/help/universal-windows/c-configuration/c.json.md)。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` 此檔案僅包含中繼資料，且版本號碼為 `255.255.255.255`Microsoft根據Microsoft接受的行為。如需詳細資訊，請參閱 [如何新增WinRT C++/CX元件dll的組件資訊？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 語法差別 {#section_A02DE120B6D240F5AFFE7509755C4F14}

可在多種程式語言中使用的通用 Windows 平台程式庫。如果您使用不同語言，本指南中的範例(JavaScript)可能需要修改。當您從WinJS使用winmd方法時，所有方法都會自動將其第一個字母設為小寫。

實施間的主要差別，是上下文資料使用的資料結構。Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動 Visual Studio 並開啟您的方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. 選取正確版本的程式庫，然後瀏覽至關聯的ADBMobile. winmd檔案。

   如需詳細資訊，請參閱 *此頁面上的選取正確版本* 區段。

1. 按一下「**新增**」。

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解決方案中還有C++專案，請跳過此步驟。

1. 在左側的 **[!UICONTROL 「Windows]** 」索引標籤中，選取 **[!UICONTROL 「擴充功能」]**，選取並新增 **[!UICONTROL 「Visual C++2015Runtime for Universal Windows Platform Apps]**」。

1. 將這一行新增至您的類別:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 瀏覽至 `ADBMobileConfig.json` 檔案，然後按一下 **[!UICONTROL 「新增]**」。

1. 在解決方案 `ADBMobileConfig.json` 的檔案上按一下滑鼠右鍵，然後選取 **[!UICONTROL 「屬性]**」。

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動 Visual Studio 並開啟您的方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. 選取正確版本的程式庫，並新增參考至關聯的ADBMobile. winmd檔案。

   如需詳細資訊，請參閱 *此頁面上的選取正確版本* 區段。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. 將這一行新增至您的類別:

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動 Visual Studio 並開啟您的方案。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. 選取正確版本的程式庫，然後瀏覽至關聯的ADBMobile. winmd檔案。

1. Click **[!UICONTROL Add]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解決方案中還有C++專案，請跳過此步驟。

1. 在左側的 **[!UICONTROL 「Windows]** 」索引標籤中，選取 **[!UICONTROL 「擴充功能」]** 並選取並新增 **[!UICONTROL 「Visual C++2015Runtime for Universal Windows Platform Apps]**」。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 瀏覽至 `ADBMobileConfig.json` 檔案，然後按一下 **[!UICONTROL 「新增]**」。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. 選取 **[!UICONTROL 「檔案屬性]** 」時，請確定 **[!UICONTROL 「封裝動作]** 」已設定為 **[!UICONTROL 「內容]**」。

   對於JavaScript專案，檔案預設會設為「內容」。

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` 檔案包含全域SDK設定，並在您完成 *新增程式庫和組態檔至專案* 區段中的步驟後，位於專案根目錄中。If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

以下是 `ADBMobileConfig.json` 檔案的範例:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

至少為您使用的解決方案更新下列值：

* **Adobe Analytics**： `rsids` and `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

如需詳細資訊，請參閱 [SDK方法](/help/universal-windows/c-configuration/methods.md)。

## 除錯 {#section_3A10376A60394A15BEE483323E0CD4AA}

若要啓用SDK的除錯，請呼叫 `ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JavaScript應用程式，您需要完成下列步驟，才能啓用原生程式碼除錯(原生程式碼除錯是C++應用程式的預設設定)：

### C Sharp

1. 在專案上按一下滑鼠右鍵，按一下 **[!UICONTROL 「屬性]** &gt; **[!UICONTROL 除錯」標籤]**。

1. 變更除錯工具類型下拉選單為&#x200B;**「僅限原生」**。

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

完成了！您現在已準備好在通用 Windows 平台應用程式中實施 Analytics、Target 和 Audience Management。

