---
description: 若您的應用程式會開啟行動網站內容，您必須確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。
seo-description: 若您的應用程式會開啟行動網站內容，您必須確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。
seo-title: 應用程式和行動網站間的訪客追蹤
solution: Experience Cloud,Analytics
title: 應用程式和行動網站間的訪客追蹤
topic: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 87%

---


# 應用程式和行動網站間的訪客追蹤  {#visitor-tracking-between-an-app-and-mobile-web}

若您的應用程式會開啟行動網站內容，您必須確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。

## 應用程式中的訪客 ID

iOS SDK會在安裝應用程式時產生唯一訪客ID。 此ID會儲存在行動裝置上的永久記憶體中，並隨每次點擊而傳送。 此ID只會在使用者解除安裝應用程式時移除。

>[!TIP]
>
>應用程式訪客 ID 在升級後仍會保留。

## 行動網站中的訪客 ID

常見的行動網站實施會使用用於桌面網站之相同標準的 Analytics `s_code.js` 或 `AppMeasurement.js`。JavaScript 資料庫擁有其產生唯一訪客 ID 的方法，而這可能會導致您從應用程式開啟行動網站內容時，產生不同的訪客 ID。

若要在應用程式和行動網站中使用相同的訪客 ID，並將應用程式訪客 ID 傳遞至 URL 中的行動網站:

## 實施應用程式和行動網站間的訪客追蹤 {#section_EDC91D6C67AD43999227707C2769C65D}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔案至您的專案*。
1. 若要在用來開啟 Web 檢視的 URL 中附加訪客資訊，請呼叫 `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   從 SDK 4.16.0 版開始，您也可以叫用 `visitorGetUrlVariablesAsync:` 並產生您自己的 URL。

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

目標網域上的ID服務程式碼會從URL擷取MID，而非傳送要求給Adobe以取得新ID。 目的地頁面上的 ID 服務程式碼會使用傳入的 MID 追蹤訪客。

在行動網站內容的點擊中，確認 `mid` 參數顯示在各個點擊上，並確認此值與應用程式程式碼所傳送的 `mid` 相符。

## 疑難排解訪客追蹤 {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### 我沒有看見 `[ADBMobile visitorAppendToURL:]`。

確認 Adobe SDK 隨附的父應用程式版本為 4.12.0 或更高版本。

### 我沒有在 URL 中看見 Adobe ID。

請確認下列項目:

* `[ADBMobile visitorAppendToURL:]` 產生用來開啟 Web 檢視的 URL 字串

* Adobe ID 經過編碼。

   若要確認 ID 已附加至即將開啟的 URL 中，請尋找 `adobe_mc` 查詢參數。

### 我的「mid」在用於 Web 檢視的應用程式中不相同。*

請確認下列項目:

* `[ADBMobile visitorAppendToURL:]` 產生用來開啟 Web 檢視的 URL 字串

   URL 字串包含 Adobe 參數。

   該字串應會包含 `adobe_mc="SAMPLE_ID_DATA"`，其中 `"SAMPLE_ID_DATA"` 包含在 Adobe Mobile SDK 中產生的 ID。

* `VisitorAPI.js` 的版本為 1.7.0 或更高版本。

如果上述的疑難排解步驟皆無法解決問題，請連絡 Adobe Client Care；並準備好共用範例應用程式和相關網站，使 Adobe 可驗證實施情形。
