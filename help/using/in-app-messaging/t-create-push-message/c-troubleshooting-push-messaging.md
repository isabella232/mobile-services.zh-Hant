---
description: 此資訊可協助您進行推送訊息疑難排解。
keywords: 行動
seo-description: 此資訊可協助您進行推送訊息疑難排解。
seo-title: 疑難排解推送訊息
solution: Marketing Cloud,Analytics
title: 疑難排解推送訊息
topic: 量度
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

此資訊可協助您進行推送訊息疑難排解。

## 為什麼有時候推送訊息的傳送會延遲?

下列延遲類型可能與 Mobile Services 的推送訊息有關:

* **等待Analytics點擊**

   每個報表套裝都可設定處理傳入 Analytics 點擊的時機。預設為每 1 小時。

   實際處理 Analytics 點擊最多可能需要 30 分鐘，但通常為 15 至 20 分鐘。例如，某個報表套裝每小時處理一次點擊。當您計入所需的最多 30 分鐘處理時間，傳入點擊最多可能需要 90 分鐘才可供推送訊息使用。如果使用者在早上 9:01 啟動應用程式，則點擊會在早上 10:15 到 10:30 之間，於 Mobile Services 使用者介面中顯示為新的唯一使用者。

* **等候推送服務**

   推送服務 (APNS 或 GCM) 可能不會立即送出訊息。雖然此情況並不常見，但有時需等候最多 5-10 分鐘。您可以透過查看「推送訊息」的&#x200B;**[!UICONTROL 「報表」]**&#x200B;檢視、在&#x200B;**[!UICONTROL 「訊息歷程記錄」]表格中找出訊息，並查看**「已發佈」]計數，來確認推送訊息已傳送至「推送服務」。**[!UICONTROL **

   >[!TIP]
   >
   >此計數是成功傳送至推送服務的數目。 推送服務無法保證訊息一定會傳送出去。

   有關服務可靠性的詳細資訊，請參閱：

   * [服務品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [訊息的期限](https://developers.google.com/cloud-messaging/concept-options#lifetime)。

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

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## 為何我的 APNS 憑證無法運作?

您的 APNS 憑證無效，原因可能如下:

* 您可能使用了沙箱憑證而非生產環境憑證。
* 您使用不受支援的新生產環境/Sandbox 憑證。
* You are using `.p8` file instead of a `.p12` file.

## 解決推送訊息問題

**範例**

下列範例將說明您可如何解決使用 VRS 時發生的推送問題。

下列客戶擁有兩個 iOS 應用程式:

* 應用程式名稱: PhotoShop_app_iOS
   * 上層 RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID Definition Segment: `a.appid contains “PhotoShop_iOS_app_SF”`
* 應用程式名稱: PhotoShop_app_iOS
   * 上層 RSID: AllAdobe PhotoShop_apps
   * RSID:PhotoShop_iOS_app_LA
   * VRSID Definition Segment: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. 若每個應用程式&#x200B;**並未**&#x200B;具備有效憑證，則您的對象區段可能已無限期加入黑名單，且您未來可能無法傳送推送訊息給受影響的使用者。如需觀眾區隔的詳細資訊，請參閱 [觀眾：定義並設定推播訊息的對象選項](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。
