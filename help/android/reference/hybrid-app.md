---
description: 若您的應用程式會開啟行動網站內容，請確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。
seo-description: 若您的應用程式會開啟行動網站內容，請確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。
seo-title: 應用程式和行動網頁之間的訪客追蹤
solution: Marketing Cloud,Analytics
title: 應用程式和行動網頁之間的訪客追蹤
topic: 開發人員和實施
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

若您的應用程式會開啟行動網站內容，請確保系統不會將在原生和行動網站之間移動的訪客視為新訪客。

## 應用程式中的訪客ID

Android SDK 會在應用程式安裝後產生唯一的訪客 ID。此 ID 會儲存於行動裝置的永久性記憶體中、隨著每次點擊傳送，且只會在使用者解除安裝該應用程式後移除。

>[!TIP]
>
>應用程式訪客ID會在升級期間持續存在。

## 行動網路中的訪客ID

常見的行動網站實施會使用用於桌面網站之相同標準的 Analytics `s_code.js` 或 `AppMeasurement.js`。JavaScript 資料庫擁有其產生唯一訪客 ID 的方法，而這可能會導致您從應用程式開啟行動網站內容時，產生不同的訪客 ID。

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

若要在應用程式和行動網站中使用相同的訪客 ID，請:

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請 *參閱核心實作和生命週期中的新增SDK和設定檔至IntelliJ IDEA或Eclipse*[專案](/help/android/getting-started/dev-qs.md)。

1. 若要在用來開啟 Web 檢視的 URL 中附加訪客資訊，請呼叫 `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   從 SDK 4.16.0 版開始，您也可以叫用 `Visitor.getUrlVariablesAsync` 並產生您自己的 URL。

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

目的地網域上的 ID 服務程式碼會從 URL 提取 MID，而非傳送要求給 Adobe 索取新 ID。該程式碼會使用傳入的 MID 來追蹤訪客。

在行動網站內容的點擊中，確認 `mid` 參數存在於各個點擊中，並確認此值與應用程式程式碼所傳送的 `mid` 參數相符。

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

確認 Adobe SDK 隨附的父應用程式版本為 4.12.0 或更高版本。

**我沒有在 URL 中看見 Adobe ID。**

* 請確認下列項目:
   * `Visitor.appendToURL(urlString)` ) 產生用來開啟 Web 檢視的 URL 字串。
   * Adobe ID 經過編碼。To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### 我的 `mid` 在用於 Web 檢視的應用程式中不相同。

* 請確認下列項目:

   * `Visitor.appendToURL(urlString)` ) 產生要用來開啟 Web 檢視的 URL 字串。
   * URL 字串包含 Adobe 參數。

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * `VisitorAPI.js` 的版本為 1.7.0 或更高版本。

如果上述的疑難排解步驟皆無法解決問題，請連絡 Adobe Experience Care。

>[!IMPORTANT]
>
>若要允許Adobe驗證實作，您需要共用範例應用程式和相關網站。

