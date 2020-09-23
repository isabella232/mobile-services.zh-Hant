---
description: 您可以將應用程式設定為使用 Apple 推送通知服務 (APNS) 或 Firebase 雲端通訊 (FCM)。
keywords: mobile
seo-description: 您可以將應用程式設定為使用 Apple 推送通知服務 (APNS) 或 Firebase 雲端通訊 (FCM)。
seo-title: 設定應用程式以使用 APNS 或 FCM
solution: Experience Cloud,Analytics
title: 設定應用程式以使用 APNS 或 FCM
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 90%

---


# 設定應用程式以使用 APNS 或 FCM{#configure-app-to-use-apns-or-fcm}

您可以將應用程式設定為使用 Apple 推送通知服務 (APNS) 或 Firebase 雲端通訊 (FCM)。

## Android 應用程式 {#section_41D304102CDF4586911EC1413AD35A10}

### 若您的應用程式並未啟用 FCM

若要設定您的 Android 應用程式以在此情境下使用 FCM:

1. 前往 [https://firebase.google.com/](https://firebase.google.com/) 並使用您的 Google Dev 憑證登入。

1. 按一下&#x200B;**[!UICONTROL 開始使用]**&#x200B;並選取&#x200B;**[!UICONTROL 新增專案]**。

1. 輸入專案名稱，如果要選擇加入 Google Analytics for Firebase 資料，請按一下接受控制器對控制器條款的核取方塊。

1. 按一下&#x200B;**[!UICONTROL 建立專案]**，然後等待專案建立。

1. 按一下已建立的專案，便會顯示該專案的&#x200B;**[!UICONTROL 專案概述]**&#x200B;頁面。按一下帶有 Android 圖示的按鈕，將 Android 應用程式新增至專案。

1. 視需要輸入應用程式封裝名稱、應用程式暱稱和簽署憑證。

1. 請遵照安裝精靈建議的其他步驟操作。在透過測試與 Firebase 伺服器的通訊來驗證 Firebase 設定後，請返回&#x200B;**[!UICONTROL 專案概述]**&#x200B;頁面。

1. 按一下&#x200B;**[!UICONTROL 專案概述]**&#x200B;按鈕右側的齒輪圖示，然後按一下&#x200B;**[!UICONTROL 專案設定]**。

1. 按一下&#x200B;**[!UICONTROL 雲端訊息]**&#x200B;分頁標籤。

1. 複製&#x200B;**[!UICONTROL 舊版伺服器密鑰]**&#x200B;和&#x200B;**[!UICONTROL 傳送者 ID]** 以供稍後使用。

   例如:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 若您的應用程式已啟用 FCM

若要設定您的 Android 應用程式以在此情境下使用 FCM:

1. 前往 [https://firebase.google.com/](https://firebase.google.com/) 並使用您的 Google Dev 憑證登入。

1. 按一下&#x200B;**[!UICONTROL 開始使用]**。此操作會開啟專案索引頁面。尋找連結至 Android 應用程式且已啟用 Firebase 的專案，然後按一下專案卡。

1. 接著應該會載入該專案的&#x200B;**[!UICONTROL 專案概述]**。按一下&#x200B;**[!UICONTROL 專案概述]**&#x200B;按鈕右側的齒輪圖示，然後按一下&#x200B;**[!UICONTROL 專案設定]**。

1. 按一下&#x200B;**[!UICONTROL 雲端訊息]**&#x200B;分頁標籤。

1. 複製&#x200B;**[!UICONTROL 舊版伺服器密鑰]**&#x200B;和&#x200B;**[!UICONTROL 傳送者 ID]** 以供稍後使用。

   例如:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS 應用程式 {#section_2031DAB485FC4D2B9027E42AD90B294D}

若要設定您的 iOS 應用程式來使用 APNS:

1. Go to [https://developer.apple.com/account](https://developer.apple.com/account) and log in to your [Apple Developer account](https://developer.apple.com/account).
1. 在 **[!UICONTROL iOS 應用程式]**&#x200B;底下選取&#x200B;**[!UICONTROL 識別碼]**。
1. 如果有設定好的應用程式 ID 可用來進行推送，請前往步驟 11。
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 輸入應用程式ID說明。
1. 輸入應用程式ID字尾。

   >[!IMPORTANT]
   >
   >若要支援推送，您必須使用&#x200B;**不**&#x200B;含萬用字元的明確應用程式 ID (例如 `- com.tester.pushSample`)。

1. 在&#x200B;**[!UICONTROL 應用程式服務]**&#x200B;中，選取&#x200B;**[!UICONTROL 推送通知]**&#x200B;核取方塊。
1. 按一下&#x200B;**[!UICONTROL 繼續]**。
1. 按一下&#x200B;**[!UICONTROL 提交]**。
1. 按一下&#x200B;**[!UICONTROL 「完成」]**。
1. 從清單中選取設定用來推送訊息的應用程式 ID，然後按一下&#x200B;**[!UICONTROL 「編輯」]**。
1. 如果已經建立好推送憑證，則請跳至步驟 15。
1. 向下捲動至&#x200B;**[!UICONTROL 推送通知]**，然後按一下正確的&#x200B;**[!UICONTROL 建立憑證...]**&#x200B;按鈕。

   您按的按鈕視您要針對「開發」還是「生產」建立憑證而定。
1. 請遵照步驟操作，在 Apple 網站上建立 CSR、上傳 CSR 及產生憑證。
1. 向下捲動至&#x200B;**[!UICONTROL 推送通知]**&#x200B;區段，然後下載您剛才建立的 SSL 憑證。
1. 按兩下憑證，將其新增至鑰匙圈。

### SSL 憑證和私密金鑰

若要取得 SSL 憑證和私密金鑰 (APNS):

1. 開啓&#x200B;**[!UICONTROL 「鑰匙圈存取」]**。
1. 按一下&#x200B;**[!UICONTROL 我的憑證]**，然後找到適合您應用程式和環境的 **[!UICONTROL iOS 推送服務憑證]**。

   您可以比對搭售ID，以及是「開發」或「生產」，以識別正確的憑證。

1. 展開憑證並驗證其是否包含私密金鑰。
1. 以滑鼠右鍵按一下私密金鑰並選取&#x200B;**[!UICONTROL 匯出&#x200B;*`<name of key>`*]**。
1. 在對話方塊中輸入必填資訊，然後儲存新的 `.p12` 檔案。

   您無須輸入密碼。

1. 在&#x200B;**[!UICONTROL 私密金鑰]**&#x200B;中，輸入 `.p12` 檔案。

