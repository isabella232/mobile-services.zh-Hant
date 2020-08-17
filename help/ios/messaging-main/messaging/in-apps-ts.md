---
description: 本文資訊可協助您排除應用程式內傳訊問題。
keywords: mobile
seo-description: 本文資訊可協助您排除應用程式內傳訊問題。
seo-title: 應用程式內傳訊疑難排解
solution: Marketing Cloud,Analytics
title: 應用程式內傳訊疑難排解
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '595'
ht-degree: 100%

---


# 應用程式內傳訊疑難排解{#troubleshooting-in-app-messaging}

本文資訊可協助您排除應用程式內傳訊問題。

如果您已滿足應用程式內傳訊的所有要求，但訊息仍未顯示，請檢查下列項目：

## 應用程式是否使用最新設定和最新 SDK 嗎？

確認 SDK 的版本是 4.2 或更高版本，並已正確設定。確認設定 (下載的 JSON 檔案) 中有`Messages`區段或是有訊息遠端端點，以便從 Dynamic tag management 擷取訊息。

## Android 中無法顯示全螢幕訊息。我使用的 SDK 和設定皆正確，而且觸發器也符合要求。

您是否已更新資訊清單檔案，以定義全螢幕活動？

## Android 中的本機通知訊息無法運作。

請務必在資訊清單中宣告本機通知廣播接收器。如需詳細資訊，請參閱[啟用應用程式內傳訊](/help/android/messaging-main/messaging/messaging.md)中的步驟 2。

## 這是即時訊息嗎？

從「管理應用程式內傳訊」頁面上的「狀態」欄查看清單檢視，並確認是否設定為即時。

## 查看對象索引標籤中的&#x200B;*顯示一次*、*一律顯示*、*離線顯示*&#x200B;設定。

確定這些設定是依照您想要的方式。在&#x200B;**[!UICONTROL 「對象」]**&#x200B;索引標籤中，檢閱您的&#x200B;**[!UICONTROL 「觸發器」]**&#x200B;選項，該選項可供您指定顯示訊息的頻率。

## 如果是將啟動事件設為觸發器...

啟動只會發生在新的工作階段。如需工作階段開始時間的詳細資訊，請參閱 JSON 檔案設定中的 `lifecycleTimeout` 列。如需詳細資訊，請參閱 [ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)。

## 我已從遠端更新訊息，但應用程式仍顯示舊訊息。

請完成以下任一操作：

* Dynamic Tag Management 需要數分鐘時間，才能以您的新定義更新端點。

   等候一段時間，然後再試一次。

* 新啟動時才會更新設定。如果應用程式在生命週期工作階段逾時期間重新啟動，則您的新設定可能尚未下載。

   如需詳細資訊，請參閱[生命週期量度](/help/ios/metrics.md)。

## 我的影像無法完全符合範本所提供的空間。

「應用程式內傳訊」的全螢幕範本支援顯示遠端伺服器 (影像 URL) 或應用程式套裝 (套裝影像) 的影像。該影像應為標準影像格式，例如 JPG、GIF 或 PNG。

由於裝置螢幕有許多不同的尺寸，因此影像很有可能無法完全符合範本所提供的空間。該範本著重於顯示影像的中央，因此如果影像不符合空間，請裁切 (縱向) 或淡化 (橫向) 邊緣。

各方向正確放置與大小調整的規則如下：

* **縱向**：
   * 手機的高度為 195px
   * 平板電腦的高度為 529px
   * 如果影像寬度小於裝置寬度，系統會予以置中。
   * 如果影像寬度大於裝置寬度，系統會加以裁切。

* **橫向**：
   * 影像會縮放至裝置高度的 100%。
   * 寬度是裝置的 75%，右側會採淡出處理。

如果使用全螢幕範本時發生問題，可下載並使用自訂 HTML 範本。此範本能賦予影像更大的使用彈性，供您完全控制範本。

## iPhone X 的應用程式內傳訊功能不會以全螢幕模式顯示。

若要在 iPhone X 上以全螢幕模式顯示應用程式內傳訊：

1. 在中繼資料標記中新增 `viewport-fit=cover`。

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. 在 CSS 為頂層 UI 元素設定適當的內距，例如：

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   這些設定可避免 UI 元素與狀態列發生衝突。
