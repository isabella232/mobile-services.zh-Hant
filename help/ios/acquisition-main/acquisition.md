---
description: 可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。
seo-description: 可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。
seo-title: '行動應用程式贏取 '
solution: Experience Cloud,Analytics
title: '行動應用程式贏取 '
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 100%

---

# 行動應用程式贏取 {#mobile-app-acquisition}

可以在 Adobe Mobile Services 中產生具備獨特追蹤代碼的贏取連結。當使用者按一下產生的連結，從 Apple App Store 下載並執行應用程式後，SDK 就會自動收集並傳送贏取資料至 Adobe Mobile Services。

若要使用 Acquisition，您&#x200B;**必須**&#x200B;有 SDK 4.1 版或更新版本。

贏取連結必須在 Adobe Mobile Services 中建立。如需詳細資訊，請參閱[贏取](/help/using/acquisition-main/acquisition-main.md)。

本節中的資訊可讓 SDK 透過贏取連結傳送贏取資料。

## 追蹤行動應用程式贏取 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的專案*。
1. 匯入資料庫:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 確認 `ADBMobileConfig.json` 檔案包含必要的贏取設定:

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
   >如果您要傳送資料至多個報表套裝，請在報表套裝 ID 清單中，使用與第一個報表套裝關聯之應用程式的贏取設定 (贏取伺服器與 appid)。

   `acquisition`設定是由 Adobe Mobile Services 產生，且不可變更。如需有關如何下載自訂 `ADBMobileConfig.json` 檔案和預先設定之`acquisition`設定的詳細資訊，請參閱[開始之前](/help/ios/getting-started/requirements.md)。

啟用這些設定後，贏取資料會在應用程式初次啟動後，自動透過初始生命週期呼叫傳送。

>[!CAUTION]
>
>`referrerTimeout` 值必須設定高於 0，才可啟用應用程式贏取。

## 為通用連結啟用 iOS 應用程式

如果您在應用程式中使用通用連結，請將 Adobe 行銷連結網域新增至應用程式的關聯網域清單。

在 Xcode 中，若要將 Adobe 行銷連結網域新增至關聯網域清單:

1. 前往您的專案目標，然後按一下&#x200B;**[!UICONTROL 功能]**&#x200B;標籤。
2. 向下捲動至&#x200B;**[!UICONTROL 關聯網域]**&#x200B;區段，並將其切換為開啟。
3. 在來自您的行銷連結 URL 之行銷連結網域的&#x200B;**[!UICONTROL 網域]**&#x200B;清單中新增項目。

您的項目看起來會類似 `applinks:5848561889a02a6996aea62b.c00.adobe.com`。
