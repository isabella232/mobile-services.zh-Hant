---
description: 您可以設定應用程式使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。
keywords: 行動
seo-description: 您可以設定應用程式使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。
seo-title: 設定應用程式以使用APNS或FCM
solution: Marketing Cloud、Analytics
title: 設定應用程式以使用APNS或FCM
topic: 量度
uuid: fa411f2a-ba47-4499-bbe5-1aadef6 b49 ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# 設定您的應用程式以使用APNS或FCM{#configure-app-to-use-apns-or-fcm}

您可以設定應用程式使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。

## Android 應用程式 {#section_41D304102CDF4586911EC1413AD35A10}

### 如果您的應用程式未啓用FCM

若要設定您的Android應用程式在此情況下使用FCM：

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 按一下 **[!UICONTROL 「開始」，]** 然後選取 **[!UICONTROL 「新增專案]**」。

1. 輸入專案名稱，如果選擇加入Google Analytics for Firebase資料，請按一下接受控制器控制器條款的核取方塊。

1. 按一下 **[!UICONTROL 「建立專案]** 」，等待建立專案。

1. 按一下建立的專案，然後顯示所建立專案的 **[!UICONTROL 「專案概述]** 」頁面。按一下「使用Android圖示」按鈕，將Android應用程式新增至專案。

1. 如有需要，請輸入應用程式套件名稱、應用程式命名名稱和簽署憑證。

1. 依照設定精靈所建議的其他步驟進行。透過測試與Firebase伺服器的通訊來驗證Firebase設定後，請返回 **[!UICONTROL 「專案概述]** 」頁面。

1. 按一下 **[!UICONTROL 「專案概述」]** 按鈕右邊的齒輪圖示，然後按一下 **[!UICONTROL 「專案設定]**」。

1. 按一下 **[!UICONTROL 「雲端訊息]** 」索引標籤。

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   例如:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 如果您的應用程式已啓用FCM

若要設定您的Android應用程式在此情況下使用FCM：

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 按一下 **[!UICONTROL 「開始」]**。這將開啓專案索引頁面。尋找已啓用Firebase的專案，該專案會連結至您的Android應用程式，然後按一下專案卡片。

1. 然後應該載入專案的 **** 專案概述。按一下 **[!UICONTROL 「專案概述」]** 按鈕右邊的齒輪圖示，然後按一下 **[!UICONTROL 「專案設定]**」。

1. 按一下 **[!UICONTROL 「雲端訊息]** 」索引標籤。

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   例如:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

若要設定您的 iOS 應用程式來使用 APNS:

1. 前往 [https://developer.apple.com/account](https://developer.apple.com/account) 並使用您的 [Apple Developer 帳戶](https://developer.apple.com/account)登入。
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. 如果您已設定要推送的應用程式ID，請前往步驟11。
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 輸入應用程式 ID 說明。
1. 輸入應用程式 ID 尾碼。

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. 在&#x200B;**[!UICONTROL 「應用程式服務」]**&#x200B;中，選取&#x200B;**[!UICONTROL 「推播通知」]**&#x200B;核取方塊。
1. Click **[!UICONTROL Continue]**.
1. Click **[!UICONTROL Submit]**.
1. 按一下&#x200B;**[!UICONTROL 完成]**。
1. 從清單中選取設定用來推播訊息的應用程式 ID，然後按一下&#x200B;**[!UICONTROL 「編輯」]**。
1. 如果已經建立好推送憑證，則請跳至步驟 15。
1. 向下捲動至&#x200B;**[!UICONTROL 「推播通知」]**，然後按一下正確的&#x200B;**[!UICONTROL 「建立憑證...」]**&#x200B;按鈕。

   您按下的按鈕取決於您要建立開發或生產的憑證。
1. 依照如何在Apple網站上建立CSR、上傳CSR及產生憑證的步驟進行。
1. 向下捲動至&#x200B;**[!UICONTROL 「推播通知」]**&#x200B;區段，然後下載您剛才建立的 SSL 憑證。
1. 按兩下已下載的憑證，將其新增至您的鑰匙圈。

### SSL憑證和私密金鑰

若要取得SSL憑證和私密金鑰(APNS)：

1. 開啓&#x200B;**[!UICONTROL 「鑰匙圈存取」]**。
1. Click **[!UICONTROL My Certificates]** and find the appropriate **[!UICONTROL iOS Push Services Certificate]** for your app and environment.

   您可比對套件 ID 以及其屬於「開發」或「生產」來識別正確的憑證。

1. 展開憑證，確認其包含私密金鑰。
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. 在對話方塊中輸入必要的資訊，然後儲存您的新 `.p12` 檔案。

   您無須輸入密碼。

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

