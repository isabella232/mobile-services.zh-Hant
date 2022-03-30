---
description: 有關如何實現通用Windows平台庫的資訊。
solution: Experience Cloud Services,Analytics
title: 開發人員快速入門
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# 開發人員快速入門{#developer-quick-start}

下面是有關如何實現通用Windows平台庫的一些資訊。

>[!IMPORTANT]
>
>要實施SDK，您需要Visual Studio 2013或更高版本。

## 獲取SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

解壓後 [SDK下載](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 檔案，您將為每個支援的體系結構和平台組合使用單獨的資料夾。 您還將 `ADBMobileConfig.json` 的子菜單。 有關此檔案的詳細資訊，請參見 [ADBMobileConfig.json配置檔案](/help/universal-windows/c-configuration/c.json.md)。

## 選擇正確的版本 {#section_E53C5AA7D5474824A89BB32C003865A1}

不同 `.dll/.winmd` 為每個支援的體系結構(x86、x64、ARM)提供檔案。

>[!IMPORTANT]
>
>版本 `ADBMobile.winmd` 不反映庫的版本。 的 `.winmd` 檔案僅包含元資料，並且具有版本號 `255.255.255.255`這是Microsoft所接受的行為。 有關詳細資訊，請參見 [如何為WinRT C++ / CX元件dll添加程式集資訊？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)。要檢查所使用庫的版本，請檢查基礎庫的版本 `ADBMobile.dll` 的子菜單。

## 語法差異 {#section_A02DE120B6D240F5AFFE7509755C4F14}

通用Windows平台庫可以用於多種寫程式語言。 本指南中的示例在WinJS(JavaScript)中，如果您使用的語言不同，可能需要修改。 使用winJS中的winmd方法時，所有方法都會自動將其第一個字母小寫。

這些實現的主要區別在於用於上下文資料的資料結構。 此外，在WinJS項目中使用SDK時，使用空字串( `""` 或 `''`) `null` 為空字串值。

## 將庫和配置檔案添加到項目 — C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動Visual Studio並開啟解決方案。
1. 在 **[!UICONTROL 解決方案瀏覽器]**，按一下右鍵 **[!UICONTROL 引用]** 選擇 **[!UICONTROL 添加引用]**。

1. 選擇庫的正確版本並瀏覽到關聯的ADBMobile.winmd檔案。

   有關詳細資訊，請參見 *選擇正確的版本* 的子菜單。

1. 按一下&#x200B;**新增**。

1. 驗證ADBMobile.winmd檔案是否已簽入 **[!UICONTROL 引用管理器]** 的 **[!UICONTROL 確定]**。

1. 在 **[!UICONTROL 解決方案瀏覽器]**，按一下右鍵 **[!UICONTROL 引用]** 選擇 **[!UICONTROL 添加引用]**。

   如果解決方案中還包含C++項目，請跳過此步驟。

1. 在 **[!UICONTROL 窗口]** 頁籤，選擇 **[!UICONTROL 擴展]**，選擇並添加 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. 將以下行添加到類：

   ```csharp
   using ADBMobile;
   ```

1. 按一下右鍵項目，然後按一下 **[!UICONTROL 添加]** > **[!UICONTROL 現有項]**。

1. 瀏覽到 `ADBMobileConfig.json` 按一下 **[!UICONTROL 添加]**。

1. 按一下右鍵 `ADBMobileConfig.json` 檔案，選擇 **[!UICONTROL 屬性]**。

1. 更改 **[!UICONTROL 生成操作]** 至 **[!UICONTROL 內容]**。

## 將庫和配置檔案添加到項目 — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動Visual Studio並開啟解決方案。
1. 在 **[!UICONTROL 解決方案瀏覽器]**，按一下右鍵項目並選擇 **[!UICONTROL 添加]** > **[!UICONTROL 引用]**。

1. 選擇庫的正確版本，並添加對關聯ADBMobile.winmd檔案的引用。

   有關詳細資訊，請參見 *選擇正確的版本* 的子菜單。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 驗證 `ADBMobile.winmd` 的 **[!UICONTROL 引用管理器]** 的 **[!UICONTROL 確定]**。

1. 將以下行添加到類：

   ```c++
   using namespace ADBMobile;
   ```

1. 按一下右鍵項目並選擇 **[!UICONTROL 添加]** > **[!UICONTROL 現有項]**。

1. 瀏覽到 `ADBMobileConfig.json` 按一下 **[!UICONTROL 添加]**。

1. 按一下右鍵 `ADBMobileConfig.json` 檔案，選擇 **[!UICONTROL 屬性]**。

1. 在 **[!UICONTROL 常規]** 頁籤，更改 **[!UICONTROL 內容]** 至 **[!UICONTROL 是]** 按一下 **[!UICONTROL 確定]**。

## 將庫和配置檔案添加到項目 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動Visual Studio並開啟解決方案。

1. 在 **[!UICONTROL 解決方案瀏覽器]**，按一下右鍵 **[!UICONTROL 引用]** 選擇 **[!UICONTROL 添加引用]**。

1. 選擇庫的正確版本並瀏覽到關聯的ADBMobile.winmd檔案。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 驗證ADBMobile.winmd檔案是否已簽入 **[!UICONTROL 引用管理器]** 的 **[!UICONTROL 確定]**。

1. 在 **[!UICONTROL 解決方案瀏覽器]**，按一下右鍵 **[!UICONTROL 引用]** 選擇 **[!UICONTROL 添加引用]**。

   如果解決方案中還包含C++項目，請跳過此步驟。

1. 在 **[!UICONTROL 窗口]** 頁籤，選擇 **[!UICONTROL 擴展]** 選擇並添加 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. 按一下右鍵項目並選擇 **[!UICONTROL 添加]** > **[!UICONTROL 現有項]**。

1. 瀏覽到 `ADBMobileConfig.json` 按一下 **[!UICONTROL 添加]**。

1. 按一下右鍵 `ADBMobileConfig.json` 檔案，選擇 **[!UICONTROL 屬性]**。

1. 與 **[!UICONTROL 檔案屬性]** 選定，確保 **[!UICONTROL 包操作]** 設定為 **[!UICONTROL 內容]**。

   對於JavaScript項目，預設情況下，檔案設定為「內容」。

## 更新ADBMobileConfig.json配置檔案 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

的 `ADBMobileConfig.json` 檔案包含全局SDK設定，在您完成以下步驟後位於項目根目錄中 *將庫和配置檔案添加到項目* 的子菜單。 如果 `ADBMobileConfig.json` 檔案未由AdobeMobile服務預配置，您需要更新幾個值才能開始。

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

至少要更新您使用的解決方案的以下值：

* **Adobe Analytics**: `rsids` 和 `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

有關詳細資訊，請參見 [SDK方法](/help/universal-windows/c-configuration/methods.md)。

## 為  除錯 {#section_3A10376A60394A15BEE483323E0CD4AA}

要啟用SDK的調試，請調用 `ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JavaScript應用，需要通過完成以下步驟（本機代碼調試是C++應用的預設設定）啟用本機代碼調試：

### C夏普

1. 按一下右鍵項目，按一下  **[!UICONTROL 屬性]** > **[!UICONTROL 「調試」頁籤]**。

1. 將調試器類型下拉更改為 **僅本機**。

### JavaScript

1. 按一下右鍵項目，按一下 **[!UICONTROL 屬性]** > **[!UICONTROL 配置屬性]** > **[!UICONTROL 「調試」頁籤]**。

1. 將調試器類型下拉更改為 **[!UICONTROL 僅本機]**。

完成了！您現在已準備好在通用Windows平台應用中實施分析、目標和受眾管理。
