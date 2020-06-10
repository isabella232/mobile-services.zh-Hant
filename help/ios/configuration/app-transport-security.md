---
description: 此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。
seo-description: 此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e6af295ddc5fea2a3e649b659894e6c6123a3457
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 84%

---


# App Transport Security {#app-transport-security}

此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。

Apple 自 iOS 9 開始導入 App Transport Security，這是一組符合安全連線最佳實踐應用的規範。如需詳細資訊，請參閱[資訊屬性清單索引鍵參考](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)中的 *NSAppTransportSecurity*。

若要讓 Adobe Mobile SDK 4.7 版或更新版本能夠順暢地與 ATS 搭配運作，請使用「管理應用程式設定」頁面中的「啟用 SSL」選項。如需詳細資訊，請參閱[管理應用程式設定](/help/using/c-manage-app-settings/c-manage-app-settings.md)或 [ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)。

在 Adobe Mobile Services 中，選取管理應用程式設定頁面中的&#x200B;**[!UICONTROL 使用 HTTPS]** 選項後，所有來自 Analytics、Audience Manager、Target 以及 Adobe Experience Platform Identity Services 的點擊皆會透過 HTTPS 傳送。

或者，您可以將下列伺服器置於您的「允許」清單中：

| 產品 | 說明 |
|--- |--- |
| Analytics | 若要允許您的Analytics伺服器，請將追蹤伺服器網域新增至info.plist檔案，做為ATS的例外網域。  您可以在 `ADBMobileConfig.json` 檔案的 Analytics 區段或「管理應用程式設定」頁面的 Analytics 區段中，找到追蹤伺服器網域。 |
| Audience Manager | 在 `ADBMobileConfig.json` 檔案之 audienceManager 物件的伺服器屬性中找到 Audience Manager 網域。如果您在應用程式中使用 Audience Manager，但未啟用 SSL，請在 `Info.plist` 檔案中新增此伺服器作為 ATS 的例外網域 |
| Target | 您可以將 Target 端點新增至 info.plist 檔案，作為 ATS 的例外網域。若要尋找 Target 端點，請在 `clientCodeproperty` 檔案的目標物件中找到 `ADBMobileConfig.json`。您的端點會是 `https://{clientCode}.tt.omtrdc.net`。例如，如果 `clientCodeproperty` 為 `“myCompany”`，則您的端點會是 `https://myCompany.tt.omtrdc.net`。 |
| Adobe Experience Platform Identity Service | 您可以在 `Info.plist` 檔案中新增 Experience Cloud 伺服器，作為 ATS 的例外網域。此網域為 `dpm.demdex.net`。 |
| Mobile Services: 贏取 | Allow the Acquisition server as an exception domain for ATS in your  `Info.plist` file. 此網域為 `c00.adobe.com`。 |
| Mobile Services: 應用程式內訊息 | 如果您使用應用程式內訊息，您可能需要針對您使用的每個非HTTPS URL，將項目新增至ATS的例外網域。 此清單包含託管影像和任何內嵌至自訂全螢幕訊息 HTML 的 URL。如需有關在 `info.plist` 檔案中設定例外網域的詳細資訊，請參閱&#x200B;*表 2: App Transport Security 字典主要索引鍵*&#x200B;中的 *NSExceptionDomains* 列。另請參閱[資訊屬性清單索引鍵參考](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)中的&#x200B;*表 3: 例外網域字典索引鍵*。 |

>[!TIP]
>
>上述之考量作法均會影響由 Adobe Mobile SDK 進行的連線，但不會影響由應用程式進行的 Web 檢視或其他連線。

