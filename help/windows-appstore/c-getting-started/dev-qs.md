---
description: 開發人員快速入門文章
solution: Experience Cloud,Analytics
title: 開發人員快速入門
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# 開發人員快速入門 {#developer-quick-start}

您將需要Visual Studio 2013或更新版本才能建置SDK。

## 取得SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解壓縮[SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)後，您會針對每個支援的架構和平台組合，提供個別的資料夾。 您也將擁有`ADBMobileConfig.json`檔案，本指南稍後將說明。

## 選擇正確的版本{#section_E53C5AA7D5474824A89BB32C003865A1}

每個目標平台(Windows 8.1、Windows Phone 8.1)和支援的架構(x86、x64、ARM)都提供不同的`.dll`/ `.winmd`檔案。 這些檔案根據以下內容分為資料夾結構：

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>`ADBMobile.winmd`的版本不反映庫的版本。 `.winmd`檔案僅包含元資料，因此將具有根據Microsoft接受的行為的`255.255.255.255`版本號(請參見[如何添加WinRT C++ / CX元件dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode))。要檢查您使用的庫版本，請檢查基礎`ADBMobile.dll`檔案的版本。

## 語法差異{#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 Universal App Store程式庫可用於數種程式設計語言。 本指南中的範例位於WinJS(JavaScript)中，如果您使用不同的語言，則可能需要加以修改。 請注意，當您從winJS(JavaScript)使用winmd方法時，所有方法都會自動將其第一個字母小寫。

實施之間的主要差異是用於上下文資料的資料結構。

此外，在WinJS專案中使用SDK時，請針對空字串值使用空字串（`""`或`''`），而非`null`。

## 將庫和配置檔案添加到項目- C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在&#x200B;**解決方案總管**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

1. 選擇正確的庫版本並瀏覽至關聯的`ADBMobile.winmd`檔案。

   如需詳細資訊，請參閱下方的&#x200B;*選擇正確的版本*&#x200B;一節。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 確認在&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中選擇了`ADBMobile.winmd` ，然後按一下&#x200B;**[!UICONTROL OK]**。

   >[!NOTE]
   >
   >新增對Windows Phone應用程式的參考時，若要選取`ADBMobile.winmd`，請將預設檔案篩選器從&#x200B;**[!UICONTROL 元件檔案]**&#x200B;變更為&#x200B;**所有檔案**。

1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的&#x200B;**Windows**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL 擴充功能]**，然後選擇並新增&#x200B;**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**。

1. 將下列行添加到類中：

   ```
   using ADBMobile;
   ```

1. 按一下右鍵項目，然後選擇&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 現有項目]**。

1. 瀏覽至您的`ADBMobileConfig.json`檔案，然後按一下「新增&#x200B;****」。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 將&#x200B;**[!UICONTROL 建置操作]**&#x200B;更改為&#x200B;**[!UICONTROL 內容]**。

## 將庫和配置檔案添加到項目- C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在&#x200B;**[!UICONTROL Solution Explorer]**&#x200B;中，按一下右鍵項目並選擇&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 引用]**。

1. 選擇正確的庫版本，然後添加對相關`ADBMobile.winmd`檔案的引用。

   如需詳細資訊，請參閱下方的&#x200B;*選擇正確版本*&#x200B;一節。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 在&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中，驗證是否已選擇`ADBMobile.winmd` ，然後按一下&#x200B;**[!UICONTROL OK]**。

   >[!TIP]
   >
   >新增對Windows Phone應用程式的參考時，若要選取`ADBMobile.winmd`，請將預設檔案篩選器從&#x200B;**[!UICONTROL 元件檔案]**&#x200B;變更為&#x200B;**所有檔案**。

1. 將下列行添加到類中：

   ```
   using namespace ADMS::Measurement;
   ```

1. 按一下右鍵項目，然後選擇&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 現有項目]**。

1. 瀏覽至`ADBMobileConfig.json`檔案，然後按一下「新增&#x200B;****」。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤上，將&#x200B;**[!UICONTROL Content]**&#x200B;變更為&#x200B;**[!UICONTROL Yes]**，然後按一下&#x200B;**[!UICONTROL OK]**。

## 將程式庫和設定檔案新增至您的專案- WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在&#x200B;**解決方案總管**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

   如需詳細資訊，請參閱下方的&#x200B;*選擇正確版本*&#x200B;一節。

1. 選擇正確的庫版本，然後瀏覽至關聯的`ADBMobile.winmd`檔案。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 確認&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中已選中`ADBMobile.winmd` ，然後按一下&#x200B;**[!UICONTROL OK]**。

   >[!TIP]
   >
   >新增對Windows Phone應用程式的參考時，若要選取`ADBMobile.winmd`，請將預設檔案篩選器從&#x200B;**[!UICONTROL 元件檔案]**&#x200B;變更為&#x200B;**所有檔案**。

1. 在&#x200B;**[!UICONTROL 解決方案總管]**&#x200B;中，按一下右鍵&#x200B;**[!UICONTROL 引用]**&#x200B;並選擇&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的&#x200B;**[!UICONTROL Windows]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL 擴充功能]**&#x200B;並選擇和添加&#x200B;**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**。

1. 按一下右鍵項目，然後選擇「添加&#x200B;**[!UICONTROL >**[!UICONTROL &#x200B;現有項目&#x200B;]**」。]**

1. 瀏覽至`ADBMobileConfig.json`檔案，然後按一下「新增&#x200B;****」。

1. 按一下右鍵解決方案中的`ADBMobileConfig.json]`檔案，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 在選擇&#x200B;**[!UICONTROL 檔案屬性]**&#x200B;後，確保&#x200B;**[!UICONTROL 包操作]**&#x200B;設定為&#x200B;**[!UICONTROL 內容]**。

   對於JavaScript專案，預設會將檔案設為&#x200B;**[!UICONTROL Content]**。

## 更新ADBMobileConfig.json設定檔案{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json`檔案包含全域SDK設定，在您完成&#x200B;*將程式庫和設定檔案新增至您的Project*&#x200B;區段中的步驟後，就會位於您的專案根目錄中。 如果您的`ADBMobileConfig.json`檔案未由AdobeMobile Services預先設定，您需要更新一些值才能開始使用。

以下是`ADBMobileConfig.json`檔案的範例：

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

請至少更新您所使用之解決方案的下列值：

* **Analytics**: `rsids` 和  `server`
* **Target**: `clientCode`
* **讀者管理**: `server`

如需詳細資訊，請參閱[ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md)。

## 為 {#section_3A10376A60394A15BEE483323E0CD4AA} 除錯

當您想要啟用SDK的除錯時，必須呼叫`ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JS應用程式，您必須完成下列步驟以啟用原生程式碼除錯（原生程式碼除錯是C++應用程式的預設設定）:

### C Sharp

按一下右鍵項目，選擇&#x200B;**[!UICONTROL 屬性]** > **[!UICONTROL 調試頁籤]**。 在調試器下拉式清單中，選擇&#x200B;**[!UICONTROL 僅本地]**。

### JS

按一下右鍵項目，選擇&#x200B;**[!UICONTROL 屬性]** > **[!UICONTROL 配置屬性]** > **[!UICONTROL 調試頁籤]**。 將調試器類型下拉清單更改為&#x200B;**僅本地**。

完成了！您現在已準備好在Windows 8.1 Universal App Store應用程式中實作Analytics、Target和Audience Management。
