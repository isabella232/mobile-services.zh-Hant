---
description: 此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。
seo-description: 此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。
seo-title: 追蹤應用程式當機
solution: Experience Cloud,Analytics
title: 追蹤應用程式當機
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 79%

---


# 追蹤應用程式當機 {#track-app-crashes}

此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。

>[!IMPORTANT]
>
>您應升級至 iOS SDK 4.8.6 版，其中包含的重大變更可避免回報錯誤當機情況。

## Adobe 何時會回報當機?

如果您的應用程式在未先進入背景執行的情況下即終止，SDK 便會在下次啟動應用程式時回報當機情況。

## 當機報告的運作方式為何?

iOS 會使用系統通知，讓開發人員能夠在應用程式生命週期中，追蹤和回應不同的狀態和事件。

Adobe Mobile iOS SDK 內含通知處理常式，可回應 `UIApplicationDidEnterBackgroundNotification` 通知。在此程式碼中，會設定一個值，指出使用者已將應用程式背景設為背景。 在後續的啟動中，如果找不到該值，則會報告當機。

## 為何 Adobe 要以此方式測量當機?

此種測量當機方式可為以下問題提供詳細解答:*「使用者是否刻意結束我的應用程式?」*

Apteligent (原為 Crittercism) 等公司所提供的當機報告資料庫皆會使用全域 `NSException` 處理常式，以提供更詳細的當機報告。您的應用程式不能有多個上述類型的處理常式。Adobe 了解客戶可能會使用其他當機報告提供者，因此決定不實施全域 `NSException` 處理常式，以避免出現建置錯誤的情況。

## 導致回報錯誤當機的原因為何?

以下情況已知會不實造成SDK報告當機：

* 如果您使用Xcode進行除錯，在應用程式在前景時再次啟動應用程式會造成當機。

   >[!TIP]
   >
   >您可以讓應用程式在背景執行，再從 Xcode 重新啟動應用程式，即可避免在此情況下出現當機。

* 如果您的應用程式於背景執行，並透過 `trackActionFromBackground`、`trackLocation` 或 `trackBeacon` 以外的呼叫傳送 Analytics 點擊，但該應用程式在背景執行的情況下遭到終止 (手動或由作業系統進行)，則下次啟動時將會出現當機情況。

   >[!TIP]
   >
   >背景活動發生時若超出 `lifecycleTimeout` 臨界值，可能也會導致其他錯誤啟動情況。

* 如果您的應用程式由於背景擷取、位置更新等原因於背景啟動，且在未曾進入前景執行的情況下即由作業系統終止，則在下次啟動 (背景或前景) 時，會導致當機。
* 如果您以程式設計方式從 `NSUserDefaults` 刪除 Adobe 的暫停標記，而應用程式同時於背景執行時，則在下次啟動或繼續執行應用程式時會造成當機情況。

## 我該如何避免收到錯誤當機報告?

下列實務可協助您避免收到錯誤當機報告:

* 在iOS SDK 4.8.6中，已新增程式碼，以更好地判斷是否需要新的生命週期工作階段。

   此程式碼可修正前一節中#2和#3錯誤當機。

* 請確定您針對非生產報表套裝執行開發，以免發生錯誤當機#1。
* 請勿刪除或修改 Adobe Mobile SDK 放入 `NSUserDefaults` 的任何值。

   如果您在 SDK 外部修改這類值，則回報的資料將會無效。

