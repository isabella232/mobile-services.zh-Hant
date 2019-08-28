---
description: 可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。
seo-description: 可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。
seo-title: 行動應用程式收購
solution: Marketing Cloud、Analytics
title: 行動應用程式收購
topic: 開發人員和實施
uuid: 5fece619-e4 b8-4d06-9250-dcb66 fu32 ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。

若要使用 Acquisition，您&#x200B;**必須**&#x200B;有 SDK 4.1 版或更新版本。

贏取連結必須在 Adobe Mobile Services 中建立。For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

本節中的資訊允許SDK從贏取連結傳送贏取資料。

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期中的新增SDK和設定檔案至您的專案*[](/help/ios/getting-started/dev-qs.md)。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >如果您要將資料傳送至多個報表套裝，請從報表套裝ID清單中，使用與第一個報表套裝關聯的應用程式取得設定(贏取伺服器和appid)。

   `acquisition` 這些設定由Adobe Mobile服務產生，不應變更。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

啟用這些設定後，贏取資料會在應用程式初次啟動後，自動透過初始生命週期呼叫傳送。

>[!CAUTION]
>
>`referrerTimeout` 必須設為高於0的值，才能啓用應用程式贏取。

## 啓用您的iOS應用程式(通用連結)

如果您使用應用程式中的通用連結，請將您的Adobe行銷連結網域新增至應用程式的「關聯網域」清單。

在Xcode中，將您的Adobe行銷連結網域新增至關聯網域清單：

1. 前往您的專案目標，然後按一下 **[!UICONTROL 「功能]** 」標籤。
2. 向下捲動至 **[!UICONTROL 「關聯網域]** 」區段，然後加以切換。
3. 在「行銷連結URL」中，新增「行銷連結」網域中 **[!UICONTROL 的]** 項目清單。

您的作品 `applinks:5848561889a02a6996aea62b.c00.adobe.com`看起來就像這樣。