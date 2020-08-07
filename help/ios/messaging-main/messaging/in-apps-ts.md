---
description: 此資訊可協助您進行應用程式內傳訊疑難排解。
keywords: mobile
seo-description: 此資訊可協助您進行應用程式內傳訊疑難排解。
seo-title: 應用程式內傳訊疑難排解
solution: Marketing Cloud,Analytics
title: 應用程式內傳訊疑難排解
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 53%

---


# 應用程式內傳訊疑難排解{#troubleshooting-in-app-messaging}

此資訊可協助您進行應用程式內傳訊疑難排解。

如果您已完成應用程式內訊息的所有需求，但訊息未顯示，請檢查下列項目：

## 應用程式中是使用最新設定和最新 SDK 嗎?

確認SDK是4.2版或更新版本，且已正確設定。 確認設定 (下載的 JSON 檔案) 中有`Messages`區段或是有訊息遠端端點，以便從 Dynamic tag management 擷取訊息。

## 我在Android中的全螢幕訊息不會顯示。 我使用正確的SDK、設定，而且符合觸發器。

您是否更新資訊清單檔案以定義全螢幕活動？

## 我在Android中的本機通知訊息無法運作。

請務必在資訊清單中宣告本機通知廣播接收器。如需詳細資訊，請參閱[啟用應用程式內傳訊](/help/android/messaging-main/messaging/messaging.md)中的步驟 2。

## 這是現時訊息嗎?

在「狀態」欄的「管理應用程式內訊息」頁面上，檢查清單檢視，並確認其是否為即時。

## 查看對象標籤中的&#x200B;*顯示一次*、*一律顯示*、*離線顯示*&#x200B;設定。

確定這些設定是依照您想要的方式。在&#x200B;**[!UICONTROL 「對象」]**&#x200B;標籤中，檢閱您的&#x200B;**[!UICONTROL 「觸發器」]**&#x200B;選項，該選項可讓您指定顯示訊息的頻率。

## 如果使用啟動事件作為觸發器……

啟動只會發生在新的工作階段。如需工作階段開始時間的詳細資訊，請參閱 JSON 檔案設定中的 `lifecycleTimeout` 列。如需詳細資訊，請參閱 [ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)。

## 我已遠端更新訊息，但應用程式仍顯示舊訊息。

完成下列其中一項作業:

* Dynamic Tag Management 需要數分鐘時間，才能以您的新定義更新端點。

   等候一段時間，然後再試一次。

* 新啟動時才會更新設定。如果應用程式在生命週期工作階段逾時期間重新啟動，則您的新設定可能尚未下載。

   如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

## 我的影像無法完全符合範本提供的空間。

應用程式內訊息全螢幕範本支援顯示來自遠端伺服器（影像URL）或應用程式套件（套裝影像）的影像。 該影像應為標準影像格式，例如 JPG、GIF 或 PNG。

由於裝置螢幕有許多不同的尺寸，因此影像很有可能無法完全符合範本所提供的空間。該範本著重於顯示影像的中央，因此如果影像不符合空間，請裁切 (縱向) 或淡化 (橫向) 邊緣。

以下為各方向的正確放置與大小調整規則:

* **縱向**:
   * 手機的高度為 195px
   * 平板電腦的高度為 529px
   * 如果影像寬度小於裝置寬度，則置中。
   * 如果影像寬度大於裝置寬度，則會進行裁切。

* **橫向**:
   * 影像會縮放至裝置高度的100%。
   * 寬度是裝置的75%，右側會淡出。

如果您對全螢幕範本有問題，可以下載並使用自訂HTML範本。 此範本提供更大的影像彈性，並可完全控制範本。

## iPhone X上的應用程式內訊息不會以全螢幕模式顯示。

若要在iPhone X上以全螢幕模式顯示應用程式內訊息：

1. 在中繼資料標記中新增 `viewport-fit=cover`。

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. 在CSS中為頂層UI元素設定適當的填補空間，例如：

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   這些設定可防止UI元素與狀態列發生衝突。
