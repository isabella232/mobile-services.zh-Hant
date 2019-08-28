---
description: 'null'
seo-description: 'null'
seo-title: 開發人員快速入門
solution: Marketing Cloud、Analytics
title: 開發人員快速入門
topic: 開發人員和實施
uuid: b368959b-d985-436e-8b3 e-97e355 a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

您需要 Visual Studio 2013 或更新版本以實施該 SDK。

## 取得 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

解壓縮 [SDK 下載](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)後，各支援架構和平台組合會有個別的檔案夾。也會有一個 `ADBMobileConfig.json` 檔案，將在本指南隨後的部分說明。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). 檔案根據以下資料夾結構分別存放:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` 檔案僅包含中繼資料，因此，此檔案的版本 `255.255.255.255` 號碼會根據Microsoft(請參閱 [如何新增WinRT C++/CX元件dll的組件資訊)？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode))。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

可在多種程式語言中使用的 Windows 8.1 通用應用程式商店程式庫。本指南中的範例在 WinJS (JavaScript) 中，若您使用其他語言，則可能需要加以修改。注意: 當您從 winJS (JavaScript) 使用 winmd 方法時，所有方法會自動將第一個字母設為小寫。

實施間的主要差別，是上下文資料使用的資料結構。

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動 Visual Studio 並開啟您的方案。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   如需詳細資訊，請參閱 *下列正確版本* 區段。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >新增參考至Windows `ADBMobile.winmd`Phone應用程式時，請將預設檔案篩選器從 **[!UICONTROL 「元件檔案]** 」變更為 **「所有檔案**」。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解決方案中還有C++專案，請跳過此步驟。

1. 在左側的 **「Windows** 」索引標籤中，選取 **[!UICONTROL 「擴充功能」]**，然後選取並新增 **[!UICONTROL Microsoft Visual C++2013Runtime Package for Windows]**。

1. 將這一行新增至您的類別:

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 瀏覽至您的 `ADBMobileConfig.json` 檔案，然後按一下 **[!UICONTROL 「新增]**」。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動 Visual Studio 並開啟您的方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   如需詳細資訊，請參閱下方的 *「選擇正確版本* 」一節。

1. Click **[!UICONTROL Add]**.

1. 在 **[!UICONTROL 「參考管理員]** 」視窗中，確認已選取 `ADBMobile.winmd` 並按一下 **[!UICONTROL 「確定]**」。

   >[!TIP]
   >
   >新增參考至Windows `ADBMobile.winmd`Phone應用程式時，請將預設檔案篩選器從 **[!UICONTROL 「元件檔案]** 」變更為 **「所有檔案**」。

1. 將這一行新增至您的類別:

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 瀏覽至 `ADBMobileConfig.json` 檔案，然後按一下 **[!UICONTROL 「新增]**」。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動 Visual Studio 並開啟您的方案。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   如需詳細資訊，請參閱 *下方的「選取正確版本* 」一節。

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >新增參考至Windows `ADBMobile.winmd`Phone應用程式時，請將預設檔案篩選器從 **[!UICONTROL 「元件檔案]** 」變更為 **「所有檔案**」。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解決方案中還有C++專案，請跳過此步驟。

1. 在左側的 **[!UICONTROL 「Windows]** 」索引標籤中，選取 **[!UICONTROL 「擴充功能」]** 並選取並新增 **[!UICONTROL Microsoft Visual C++2013Runtime Package for Windows]**。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 瀏覽至 `ADBMobileConfig.json` 檔案，然後按一下 **[!UICONTROL 「新增]**」。

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. 選取 **[!UICONTROL 「檔案屬性]** 」時，請確定 **[!UICONTROL 「封裝動作]** 」已設定為 **[!UICONTROL 「內容]**」。

   對於JavaScript專案，檔案預設會設 **[!UICONTROL 為「內容」]** 。

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` 檔案包含全域SDK設定，並在您完成 *「新增程式庫和設定檔案至專案* 」區段中的步驟後，位於專案根目錄中。If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

至少為您所使用的解決方案更新下列值:

* **分析**： `rsids` and `server`
* **Target**: `clientCode`
* **讀者管理**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## 除錯 {#section_3A10376A60394A15BEE483323E0CD4AA}

若要啟用 SDK 除錯，您必須呼叫 `ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JS應用程式，您必須完成下列步驟，才能啓用原生程式碼除錯(原生程式碼除錯是C++應用程式的預設設定)：

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. 在除錯程式下拉式清單中，選取 **[!UICONTROL 「僅原生」]**。

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. 變更除錯工具類型下拉選單為&#x200B;**「僅限原生」**。

完成了！現在您已準備好在 Windows 8.1 通用應用程式商店應用程式中實作 Analytics、Target 和 Audience Management。
