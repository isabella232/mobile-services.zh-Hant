---
description: 此訊息可協助您疑難排解應用程式內訊息的問題。
keywords: 行動
seo-description: 此訊息可協助您疑難排解應用程式內訊息的問題。
seo-title: 應用程式內傳訊疑難排解
solution: Marketing Cloud、Analytics
title: 應用程式內傳訊疑難排解
topic: 量度
uuid: 8813e8d8-bb1 e-46ad-83cd-98e68 f73 ce6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

此訊息可協助您疑難排解應用程式內訊息的問題。

如果您已完成應用程式內傳訊的所有要求，但訊息仍無法顯示，請確認下列項目:

## 應用程式中是使用最新設定和最新 SDK 嗎?

* 確認 SDK 的版本是 4.2 或更高版本，並已正確設定。

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## 我的 Android 全螢幕訊息無法顯示。我已使用正確的 SDK 和配置，也符合觸發器條件。

您有更新資訊清單檔案、定義全螢幕活動嗎?

## 我的 Android 本機通知訊息沒有作用。

確認已在資訊清單中宣告本機通知廣播接收器。For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## 這是現時訊息嗎?

在&#x200B;**「管理應用程式內訊息」頁面的查「狀態」**&#x200B;欄，檢查清單檢視中的訊息是否使用中。

## 檢視 *顯示一次*， *一律顯示*， *顯示「對象」頁面上的離線* 設定。

檢查這些設定是否正確無誤。在「對象」頁面中，檢閱&#x200B;**「觸發器」**&#x200B;分頁標籤上的選項，該選項可讓您指定顯示訊息的頻率。

## 如果使用啟動事件做為觸發器...

啟動只會發生在新的工作階段。如需有關工作階段開始時間的資訊，請參閱`lifecycleTimeout` 在 [ADBMobile JSON設定](/help/ios/configuration/json-config/json-config.md) 檔中。

## 我已從遠端更新訊息，但應用程式仍顯示舊訊息。

完成下列其中一項作業:

* Dynamic Tag Management 需要數分鐘時間，才能以您的新定義更新端點。

   請稍後再試一次。

* 新啟動時才會更新設定。

   如果應用程式在生命週期工作階段逾時期間重新啟動，則您的新設定可能尚未下載。

## 我的影像無法完全符合範本所提供的空間。

應用程式內訊息全螢幕範本支援顯示來自遠端伺服器 (影像 URL) 或應用程式套件 (套件影像) 的影像。該影像應是標準影像格式，例如 JPG、GIF 或 PNG。

由於裝置螢幕有許多不同的尺寸，因此影像有可能無法完全依照範本的空間適當顯示。範本主要會一律顯示影像中心，但如果影像無法符合，則會裁剪 (縱向) 或淡化 (橫向) 側邊。

以下為各方向的正確放置與大小調整規則:

* **縱向:**&#x200B;影像在手機上縮放至 195 像素高、在平板電腦上縮放至 529 像素高，如果影像寬度小於裝置寬度則將影像置中，如果影像寬度大於裝置寬度則加以裁剪。

* **橫向:**&#x200B;影像縮放置裝置高度的 100%、裝置寬度的 75%，並在右側淡出。

   如果您無法順利使用全螢幕範本，可以下載並使用自訂 HTML 範本。自訂 HTML 範本可提供更大的影像靈活性，並能讓您完全控制範本。

## 我的訊息並未反映我在 UI 中所進行的變更/更新。

SDK 會擷取在生命週期啟動時新增/更新的訊息。這僅當應用程式關閉/在背景執行超過生命週期逾時值然後重新開啟時才會進行。

完成下列步驟:

1. 將您的訊息URL置於組態檔中，以確認遠端訊息已更新(例如， `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. 關閉應用程式
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. 開啟應用程式，導覽至應顯示訊息的位置，然後驗證其是否已更新。