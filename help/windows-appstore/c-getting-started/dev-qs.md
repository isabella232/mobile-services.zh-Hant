---
description: 'null'
seo-description: 'null'
seo-title: 開發人員快速入門
solution: Marketing Cloud,Analytics
title: 開發人員快速入門
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 2%

---


# 開發人員快速入門 {#developer-quick-start}

您將需要Visual Studio 2013或更新版本才能建置SDK。

## 取得SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解壓縮 [SDK下載後](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)，您會針對每個支援的架構和平台組合，提供個別的資料夾。 您也會有檔 `ADBMobileConfig.json` 案，本指南稍後會說明。

## 選擇正確的版本 {#section_E53C5AA7D5474824A89BB32C003865A1}

每個 `.dll`目標平 `.winmd` 台(Windows 8.1、Windows Phone 8.1)和支援的架構(x86、x64、ARM)都提供不同的／檔案。 這些檔案根據以下內容分為資料夾結構：

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>版本不 `ADBMobile.winmd` 反映庫的版本。 文 `.winmd` 件僅包含元資料，因此，根據Microsoft的 `255.255.255.255` ，將具有可接受的行為版本號(請參見 [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode))。若要檢查您使用的程式庫版本，請檢查基礎檔案的版 `ADBMobile.dll` 本。

## 語法差異 {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 Universal App Store程式庫可用於數種程式設計語言。 本指南中的範例位於WinJS(JavaScript)中，如果您使用不同的語言，則可能需要加以修改。 請注意，當您從winJS(JavaScript)使用winmd方法時，所有方法都會自動將其第一個字母小寫。

實施之間的主要差異是用於上下文資料的資料結構。

此外，在WinJS專案中使用SDK時，請使用空字串( `""` 或 `''`)，而非空 `null` 字串值。

## 將程式庫和設定檔案新增至您的專案- C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在「解決方 **案總管**」中，以滑鼠右鍵按一下「 **[!UICONTROL 參考]** 」並選取「 **[!UIUCONTROL 新增參考」]**。

1. 選擇正確的程式庫版本，並瀏覽至相關的 `ADBMobile.winmd` 檔案。

   如需詳細資訊，請參 *閱下方的「選擇正確版本* 」一節。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 驗證是否在 `ADBMobile.winmd` 「參考管理器」( **[!UICONTROL Reference Manager]** )窗口中選 **[!UICONTROL 定，然後按一下「]**&#x200B;確定」(OK)。

   >[!NOTE]
   >
   >新增參考至Windows Phone應用程式時，若要選取， `ADBMobile.winmd`請將預設檔案篩選器從「元件檔案」 **[!UICONTROL 變更為「]** 所有檔案」 ****。

1. 在「解決方 **[!UICONTROL 案總管]**」中，以滑鼠右鍵按一下「 **[!UICONTROL 參考]** 」並選取「 **[!UICONTROL 新增參考」]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的 **Windows** 標籤中，選取「擴充功能 **[!UICONTROL 」，然後選取並新增]** Microsoft Visual C++ 2013 Runtime Package for Windows ****。

1. 將下列行添加到類中：

   ```
   using ADBMobile;
   ```

1. 以滑鼠右鍵按一下您的專案，然後選 **[!UICONTROL 取「新增]** >現 **[!UICONTROL 有項目」]**。

1. 瀏覽至您的 `ADBMobileConfig.json` 檔案，然後按一 **[!UICONTROL 下新增]**。

1. 在解決方案中 `ADBMobileConfig.json` 按一下右鍵檔案，然後選擇 **[!UICONTROL 屬性]**。

1. 將「建 **[!UICONTROL 立動作]** 」變更 **[!UICONTROL 為「內容]**」。

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在「解決 **[!UICONTROL 方案總管]**」中，以滑鼠右鍵按一下專案，然後選取「新增 **[!UICONTROL >參]** 考」 ****。

1. 選擇正確的庫版本，然後添加對關聯檔案的參 `ADBMobile.winmd` 考。

   如需詳細資訊，請參 *閱下方的「選擇正確版本* 」一節。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 在「參 **[!UICONTROL 考管理器]** 」(Reference Manager `ADBMobile.winmd` )窗口中，驗證是否已選 **[!UICONTROL 中並按一下「]**&#x200B;確定」(OK)。

   >[!TIP]
   >
   >新增參考至Windows Phone應用程式時，若要選取， `ADBMobile.winmd`請將預設檔案篩選器從「元件檔案」 **[!UICONTROL 變更為「]** 所有檔案」 ****。

1. 將下列行添加到類中：

   ```
   using namespace ADMS::Measurement;
   ```

1. 以滑鼠右鍵按一下您的專案，然後選 **[!UICONTROL 取「新增]** >現 **[!UICONTROL 有項目」]**。

1. 瀏覽至檔案 `ADBMobileConfig.json` ，然後按一下「 **[!UICONTROL 新增」]**。

1. 在解決方案中 `ADBMobileConfig.json` 按一下右鍵檔案，然後選擇 **[!UICONTROL 屬性]**。

1. 在「一 **[!UICONTROL 般]** 」標籤上，將「內容 **[!UICONTROL 」變更為「]** 是 **[!UICONTROL 」，然後單]******&#x200B;擊「確定」。

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 啟動Visual Studio並開啟您的解決方案。
1. 在「解決方 **案總管**」中，以滑鼠右鍵按一下「 **[!UICONTROL 參考]** 」並選取「 **[!UICONTROL 新增參考」]**。

   如需詳細資訊，請參 *閱下方的「選擇正確版本* 」一節。

1. 選擇正確的程式庫版本，然後瀏覽至相關的 `ADBMobile.winmd` 檔案。

1. 按一下&#x200B;**[!UICONTROL 新增]**。

1. 驗證是否 `ADBMobile.winmd` 已在「 **[!UICONTROL Reference Manager]** （參考管理器）」窗口中選中，然後按一下「 **[!UICONTROL OK（確定）]**」。

   >[!TIP]
   >
   >新增參考至Windows Phone應用程式時，若要選取， `ADBMobile.winmd`請將預設檔案篩選器從「元件檔案」 **[!UICONTROL 變更為「]** 所有檔案」 ****。

1. 在「解決方 **[!UICONTROL 案總管]**」中，以滑鼠右鍵按一下「 **[!UICONTROL 參考]** 」並選取「 **[!UICONTROL 新增參考」]**。

   如果您的解決方案中也有C++專案，請略過此步驟。

1. 在左側的 **[!UICONTROL Windows]** 標籤中，選取「擴充功能 **[!UICONTROL 」並選取並新增]** Microsoft Visual C++ 2013 Runtime Package for Windows ****。

1. 以滑鼠右鍵按一下您的專案，然後選 **[!UICONTROL 取「新增]** >現 **[!UICONTROL 有項目」]**。

1. 瀏覽至檔案 `ADBMobileConfig.json` ，然後按一下「 **[!UICONTROL 新增」]**。

1. 在解決方案中 `ADBMobileConfig.json]` 按一下右鍵檔案，然後選擇 **[!UICONTROL 屬性]**。

1. 在選 **[!UICONTROL 取「檔案屬性]** 」時，請確 **[!UICONTROL 定「封裝動作]** 」已設 **[!UICONTROL 定為Content]**。

   對於JavaScript專案，預設會將檔案設 **[!UICONTROL 定為]** Content。

## 更新ADBMobileConfig.json設定檔案 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

檔 `ADBMobileConfig.json` 案包含全域SDK設定，在您完成「將程式庫和設定檔案新增至專案」區段中的步驟後，就會位於您的專案根目錄 ** 。 如果您 `ADBMobileConfig.json` 的檔案未由Adobe Mobile Services預先設定，您必須更新一些值才能開始使用。

The following is an example of an `ADBMobileConfig.json` file:

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

* **Analytics**: `rsids` 和 `server`
* **Target**: `clientCode`
* **讀者管理**: `server`

如需詳細資訊，請 [參閱ADBMobileConfig.json設定](/help/windows-appstore/c-configuration/methods.md)。

## 除錯 {#section_3A10376A60394A15BEE483323E0CD4AA}

當您想要啟用SDK的除錯時，必須呼叫 `ADBMobile.Config.setDebugLogging(true);`。

對於C Sharp和JS應用程式，您必須完成下列步驟以啟用原生程式碼除錯（原生程式碼除錯是C++應用程式的預設設定）:

### C Sharp

在專案上按一下滑鼠右鍵，選取「 **[!UICONTROL 屬性]** >除 **[!UICONTROL 錯」標籤]**。 在除錯程式下拉式清單中，選取「僅 **[!UICONTROL 限原生]**」。

### JS

按一下右鍵項目，選擇「屬 **[!UICONTROL 性]** 」>「配 **[!UICONTROL 置屬性]** 」 **[!UICONTROL >「調]**&#x200B;試」頁籤。 將偵錯器類型下拉式清單變更為「僅 **限原生」**。

完成了！您現在已準備好在Windows 8.1 Universal App Store應用程式中實作Analytics、Target和Audience Management。
