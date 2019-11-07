---
description: 此資訊可協助您進行推送訊息疑難排解。
keywords: 行動
seo-description: 此資訊可協助您進行推送訊息疑難排解。
seo-title: 疑難排解推送訊息
solution: Marketing Cloud,Analytics
title: 疑難排解推送訊息
topic: 量度
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# 疑難排解推送訊息{#troubleshooting-push-messaging}

此資訊可協助您進行推送訊息疑難排解。

## 為什麼有時候推送訊息的傳送會延遲?

下列延遲類型可能與 Mobile Services 的推送訊息有關:

* **等候 Analytics 點擊**

   每個報表套裝都可設定處理傳入 Analytics 點擊的時機。預設為每 1 小時。

   實際處理 Analytics 點擊最多可能需要 30 分鐘，但通常為 15 至 20 分鐘。例如，某個報表套裝每小時處理一次點擊。當您計入所需的最多 30 分鐘處理時間，傳入點擊最多可能需要 90 分鐘才可供推送訊息使用。如果使用者在早上 9:01 啟動應用程式，則點擊會在早上 10:15 到 10:30 之間，於 Mobile Services 使用者介面中顯示為新的唯一使用者。

* **等候推送服務**

   推送服務 (APNS 或 GCM) 可能不會立即送出訊息。雖然此情況並不常見，但有時需等候最多 5-10 分鐘。您可以透過查看「推送訊息」的&#x200B;**[!UICONTROL 「報表」]**&#x200B;檢視、在&#x200B;**[!UICONTROL 「訊息歷程記錄」]表格中找出訊息，並查看**「已發佈」]計數，來確認推送訊息已傳送至「推送服務」。**[!UICONTROL **

   >[!TIP]
   >
   >此計數為成功傳送至「推送服務」的數量。推送服務無法保證訊息一定會傳送出去。

   有關服務可靠性的詳細資訊，請參閱:

   * [服務品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [訊息的生命週期](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## 為什麼我的 Android GCM API 密鑰無效?

* **API 密鑰無效**

   您的 API 密鑰無效，原因可能如下:

   * 您提供的 API 密鑰並非具備正確 GCM API 密鑰值的伺服器密鑰。
   * 伺服器密鑰已將 IP 加入白名單，並阻止 Adobe 伺服器傳送推送訊息。

* **判斷 API 密鑰的有效性**

   如需判斷 API 密鑰的有效性，請執行下列命令:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   傳回 401 HTTP 狀態代碼表示您的 API 密鑰為有效。否則，您會看到類似下列的項目:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   您也可以使用代號來取代 `"ABC"` 以檢查註冊代號的有效性。

## 為何我的 APNS 憑證無法運作?

您的 APNS 憑證無效，原因可能如下:

* 您可能使用了沙箱憑證而非生產環境憑證。
* 您使用不受支援的新生產環境/Sandbox 憑證。
* 您使用 `.p8` 檔案而非 `.p12` 檔案。

## 解決推送訊息問題

**範例**

下列範例將說明您可如何解決使用 VRS 時發生的推送問題。

下列客戶擁有兩個 iOS 應用程式:

* 應用程式名稱: PhotoShop_app_iOS
   * 上層 RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID 定義區段: `a.appid contains “PhotoShop_iOS_app_SF”`
* 應用程式名稱: PhotoShop_app_iOS
   * 上層 RSID: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID 定義區段: `a.os contains “iOS”`

在此範例中，若 Photoshop 員工傳送推送至 *PhotoShop_iOS_app_SF* 應用程式，則所有 *PhotoShop_iOS_app_SF* 應用程式使用者都會如預期收到推送訊息。但是，若員工傳送訊息至 *PhotoShop_app_LA* 應用程式，由於其 VRSID 定義區段不正確 (`iOS` 而非 `a.os contains "PhotoShop_iOS_app_LA"`)，因此訊息會傳送給 *AllAdobe PhotoShop_apps* 中的&#x200B;**所有** iOS 使用者。儘管訊息仍會傳送給 *PhotoShop_iOS_app_LA* 使用者，但訊息也會將 *PhotoShop_iOS_app_SF* 使用者的推送 ID 加入黑名單，因為 *PhotoShop_iOS_app_SF* 應用程式包含不同憑證。若區段定義為 `a.os contains “PhotoShop_iOS_app_LA”`，則推送訊息原本只會傳送給 *PhotoShop_iOS_app_LA* 使用者。

若透過 *PhotoShop_IOS_app_LA* 推送憑證傳送，*PhotoShop_iOS_app_SF* 的推送識別碼將傳回為 `invalid`。

>[!CAUTION]
>
>在您針對使用 VRS 的應用程式建立推送訊息，並按一下&#x200B;**[!UICONTROL 儲存並傳送]**&#x200B;之後，系統會顯示警示以提醒您確保所列出的每個應用程式&#x200B;**必須**&#x200B;具備有效憑證。若每個應用程式&#x200B;**並未**&#x200B;具備有效憑證，則您的對象區段可能已無限期加入黑名單，且您未來可能無法傳送推送訊息給受影響的使用者。如需對象區段的詳細資訊，請參閱[對象: 定義並設定推送訊息的對象區段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。
