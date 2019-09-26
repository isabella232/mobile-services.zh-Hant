---
description: 此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。
seo-description: 此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: 開發人員和實施
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

此資訊可協助您使用 iOS 9 適用之全新安全性需求組合 App Transport Security (ATS)。

Apple 自 iOS 9 開始導入 App Transport Security，這是一組符合安全連線最佳實踐應用的規範。如需詳細資訊，請參 *閱資訊屬性清* 單關鍵參考中的NSAppTransportSecurity [](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)。

若要讓 Adobe Mobile SDK 4.7 版或更新版本能夠順暢地與 ATS 搭配運作，請使用「管理應用程式設定」頁面中的「啟用 SSL」選項。如需詳細資訊，請參 [閱「管理應用程式設定](/help/using/c-manage-app-settings/c-manage-app-settings.md) 」 [或ADBMobile JSON設定](/help/ios/configuration/json-config/json-config.md)。

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

或者，您可以將下列伺服器列入白名單：

| 產品 | 說明 |
|--- |--- |
| Analytics | 若要將 Analytics 伺服器加入白名單，請將追蹤伺服器網域新增至您的 info.plist 檔案，作為 ATS 的例外網域。您可以在 `ADBMobileConfig.json` 檔案的 Analytics 區段或「管理應用程式設定」頁面的 Analytics 區段中，找到追蹤伺服器網域。 |
| Audience Manager | 在 `ADBMobileConfig.json` 檔案之 audienceManager 物件的伺服器屬性中找到 Audience Manager 網域。如果您在應用程式中使用 Audience Manager，但未啟用 SSL，請在 `Info.plist` 檔案中新增此伺服器作為 ATS 的例外網域 |
| Target | 您可以將 Target 端點新增至 info.plist 檔案，作為 ATS 的例外網域。若要尋找 Target 端點，請在 `clientCodeproperty` 檔案的目標物件中找到 `ADBMobileConfig.json`。Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | 您可以在 `Info.plist` 檔案中新增 Experience Cloud 伺服器，作為 ATS 的例外網域。This domain is `dpm.demdex.net`. |
| Mobile Services: 贏取 | 將贏取伺服器加入白名單，作為 `Info.plist` 檔案中 ATS 的例外網域。This domain is `c00.adobe.com`. |
| Mobile Services: 應用程式內訊息 | 如果您使用應用程式內訊息，便可能需要針對各個不使用 HTTPS 的 URL，新增多個項目至 ATS 的例外網域中。此清單包含託管影像和任何內嵌至自訂全螢幕訊息 HTML 的 URL。有關在檔案中設定異常域的詳細資訊，請 `info.plist` 參閱表2中 *的NSExceptionDomains* 行 *:App Transport Security字典主鍵*。 另請參 *閱資訊屬性清單鍵引用*[中的表3異常域字典鍵](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)。 |

>[!TIP]
>
>這些考量會影響Adobe Mobile SDK建立的連線，不會影響網頁檢視或應用程式建立的其他連線。

