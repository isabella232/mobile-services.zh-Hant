---
description: 'null'
seo-description: 'null'
seo-title: 開發人員快速入門
solution: Experience Cloud,Analytics
title: 開發人員快速入門
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# 開發人員快速入門{#developer-quick-start}

以下是有關如何實作通用Windows平台程式庫的一些資訊。

>[!IMPORTANT]
>
>若要實作SDK，您需要Visual Studio 2013或更新版本。

## 取得SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解壓縮[SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)檔案後，您會針對每個支援的架構和平台組合，提供個別的資料夾。 您也將擁有`ADBMobileConfig.json`檔案。 如需此檔案的詳細資訊，請參閱[ADBMobileConfig.json設定檔案](/help/universal-windows/c-configuration/c.json.md)。

## 選擇正確的版本{#section_E53C5AA7D5474824A89BB32C003865A1}

每個支援的體系結構(x86、x64、ARM)都提供不同的`.dll/.winmd`檔案。

>[!IMPORTANT]
>
>`ADBMobile.winmd`的版本不反映庫的版本。 `.winmd`檔案僅包含中繼資料，且版本號碼為`255.255.255.255`，根據Microsoft的規定，此版本為可接受的行為。 有關詳細資訊，請參見[如何為WinRT C++ / CX元件dll添加元件資訊？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)。要檢查您使用的庫版本，請檢查基礎`ADBMobile.dll`檔案的版本。

## 語法差異{#section_A02DE120B6D240F5AFFE7509755C4F14}

通用Windows平台程式庫可用於多種程式設計語言。 本指南中的範例位於WinJS(JavaScript)中，如果您使用不同的語言，則可能需要修改。 當您從winJS使用winmd方法時，所有方法都會自動將其第一個字母小寫。

實施之間的主要差異是用於上下文資料的資料結構。 此外，在WinJS專案中使用SDK時，請針對空字串值使用空字串（`""`或`''`），而非`null`。

## 將程式庫和設定檔案新增至您的專案- C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

1. 選取正確的程式庫版本，並瀏覽至相關的ADBMobile.winmd檔案。

   如需詳細資訊，請參閱本頁的&#x200B;*選擇正確的版本*&#x200B;章節。

1. 按一下&#x200B;**新增**。

1. 確認已在&#x200B;**[!UICONTROL 參考管理員]**&#x200B;視窗中勾選ADBMobile.winmd檔案，然後按一下&#x200B;**[!UICONTROL 確定]**。

1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的&#x200B;**[!UICONTROL Windows]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL 擴充功能]**，選擇並新增適用於通用Windows平台應用程式的&#x200B;**[!UICONTROL Visual C++ 2015執行階段]**。

1. 將下列行添加到類中：

   ```csharp
   using ADBMobile;
   ```

1. 按一下右鍵您的項目，然後按一下&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 現有項目]**。

1. 瀏覽至`ADBMobileConfig.json`檔案，然後按一下「新增&#x200B;****」。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 將&#x200B;**[!UICONTROL 建置操作]**&#x200B;更改為&#x200B;**[!UICONTROL 內容]**。

## 將庫和配置檔案添加到項目- C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在&#x200B;**[!UICONTROL Solution Explorer]**&#x200B;中，按一下右鍵項目並選擇&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 引用]**。

1. 選取正確的程式庫版本，並新增相關ADBMobile.winmd檔案的參考。

   如需詳細資訊，請參閱本頁的&#x200B;*選擇正確的版本*&#x200B;章節。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 確認&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中已選中`ADBMobile.winmd` ，然後按一下&#x200B;**[!UICONTROL OK]**。

1. 將下列行添加到類中：

   ```c++
   using namespace ADBMobile;
   ```

1. 按一下右鍵項目，然後選擇「添加&#x200B;**[!UICONTROL >**[!UICONTROL &#x200B;現有項目&#x200B;]**」。]**

1. 瀏覽至`ADBMobileConfig.json`檔案，然後按一下&#x200B;**[!UICONTROL 新增]**。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤上，將&#x200B;**[!UICONTROL Content]**&#x200B;變更為&#x200B;**[!UICONTROL Yes]**，然後按一下&#x200B;**[!UICONTROL OK]**。

## 將程式庫和設定檔案新增至您的專案- WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動Visual Studio並開啟您的解決方案。

1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

1. 選取正確的程式庫版本，並瀏覽至相關的ADBMobile.winmd檔案。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 確認已在&#x200B;**[!UICONTROL 參考管理員]**&#x200B;視窗中勾選ADBMobile.winmd檔案，然後按一下&#x200B;**[!UICONTROL 確定]**。

1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的&#x200B;**[!UICONTROL Windows]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL 擴充功能]**&#x200B;並選取並新增適用於通用Windows平台應用程式的&#x200B;**[!UICONTROL Visual C++ 2015 Runtime。]**

1. 按一下右鍵項目，然後選擇「添加&#x200B;**[!UICONTROL >**[!UICONTROL &#x200B;現有項目&#x200B;]**」。]**

1. 瀏覽至`ADBMobileConfig.json`檔案，然後按一下「新增&#x200B;****」。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 在選擇&#x200B;**[!UICONTROL 檔案屬性]**&#x200B;後，確保&#x200B;**[!UICONTROL 包操作]**&#x200B;設定為&#x200B;**[!UICONTROL 內容]**。

   對於JavaScript專案，預設會將檔案設為「內容」。

## 更新ADBMobileConfig.json設定檔案{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json`檔案包含全域SDK設定，在您完成&#x200B;*將程式庫和設定檔案新增至專案*&#x200B;區段中的步驟後，位於您的專案根目錄中。 如果您的`ADBMobileConfig.json`檔案未由AdobeMobile Services預先設定，您需要更新一些值才能開始使用。

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

請至少為您所使用的解決方案更新下列值：

* **Adobe Analytics**: `rsids` 和  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

如需詳細資訊，請參閱[SDK方法](/help/universal-windows/c-configuration/methods.md)。

## 為 {#section_3A10376A60394A15BEE483323E0CD4AA} 除錯

若要啟用SDK的除錯，請呼叫`ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JavaScript應用程式，您必須完成下列步驟以啟用原生程式碼除錯（原生程式碼除錯是C++應用程式的預設設定）:

### C Sharp

1. 在專案上按一下滑鼠右鍵，按一下「屬性&#x200B;**** > **[!UICONTROL 除錯標籤]**」。

1. 將調試器類型下拉清單更改為&#x200B;**僅本地**。

### JavaScript

1. 按一下右鍵項目，按一下「屬性」>「配置屬性」>「配置屬性」>「調試」頁籤&#x200B;]**。**********[!UICONTROL 

1. 將調試器類型下拉清單更改為&#x200B;**[!UICONTROL 僅本地]**。

完成了！您現在已準備好在通用Windows平台應用程式中實作Analytics、Target和Audience Management。
