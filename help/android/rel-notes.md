---
description: Experience Cloud 解決方案專用 Android SDK 4.x 的發行說明和已知問題。
solution: Experience Cloud,Analytics
title: 發行說明
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# 發行說明 {#release-notes}

以下是適用於 Experience Cloud 解決方案的 Android SDK 4.x 的發行說明、已知問題和 Hotfix 資訊：

## 2020年4月3日：4.18.2

* 應用程式內傳訊 — 基於安全考量，SDK建立的WebViews現在會將屬性`setAllowFileAccess`設為`false`。

## 2020年3月12日：4.18.1

* Target - Target工作階段ID現在會在傳送至Adobe Analytics的內部Analytics-for-Target點擊中，以內容資料參數`a.target.sessionId`的形式新增。

## 2020年1月16日：4.18.0

* 取得 - 新增 API `Analytics.processGooglePlayInstallReferrerUrl(final String url)` 以支援 Google Play Install Referrer API。

   如需 Install Referrer API 的詳細資訊，請參閱[您還在使用 InstallBroadcast 嗎？在 2020 年 3 月 1 日前切換至 Play Referrer API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)。

## 2019 年 9 月 20 日：4.17.10 版

* 一般：修正 Android API Level 21 或更新版本上某些地區的地區字串產生問題。

## 2019 年 7 月 18 日：4.17.8 版

* Adobe Target：所有要求現在都會在 URL 查詢參數中納入用戶端和 sessionId。
* 應用程式內傳訊：修正透過空白點選連結URL觸發訊息時，Android應用程式當機的問題。
* 訪客 ID 服務：`Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再將傳回的值雙重編碼。

   雙重編碼已導致這些 API 傳回的值遭某些安全性審核機制特別標記。

## 2019 年 6 月 6 日：4.17.7 版

* 一般 - 低於 20 的 Android API 層級上的網路呼叫現在將使用 TLS 1.1 或 TLS 1.2。
* Analytics - 在啟用推送通知時，將推送選擇加入狀態附加至生命週期資料。

## 2019 年 5 月 24 日：4.17.6 版

* 訪客ID服務 — `setPushIdentifier` API呼叫現在會在每次呼叫時將同步呼叫傳送至訪客ID服務。
* 訪客 ID 服務 - 將連線和讀取逾時從 2 秒增加到 5 秒。

如需詳細了解所有解決方案的最新及歷來發行說明，請參閱 [Adobe Experience Cloud 發行說明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html)。
