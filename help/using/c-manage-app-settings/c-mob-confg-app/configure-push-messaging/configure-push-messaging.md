---
description: 您建立新應用程式或編輯現有應用程式時，可使用這些資訊協助您設定「管理應用程式設定」頁面上的「推送服務」選項。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 設定推送訊息
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: dbe3af75010fbf5195a3f93fc43cb696aaa32b65
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# 設定推送訊息{#configure-push-messaging}

您建立新應用程式或編輯現有應用程式時，可使用這些資訊協助您設定「管理應用程式設定」頁面上的「推送服務」選項。

設定推送訊息之前，請先完成[啟用推送訊息的必要條件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)中的必要工作。

* **報表套裝考量事項**

   您可以在每個報表套裝中，為 Apple 設定一個應用程式商店應用程式，同時也為 Google 設定一個。如果您還需要其他應用程式，例如一個用於生產環境，另一個用於開發環境，那麼，請為每個環境設定新的應用程式商店應用程式和新的報表套裝。

>[!IMPORTANT]
>
>不支援將您的應用程式移動到新的報表套裝。若您移轉到新報表套裝，推送設定可能會損毀，且訊息可能無法傳送。

1. 在&#x200B;**[!UICONTROL 「推送服務」下的下列欄位中輸入資訊]**:

   * Apple

      **[!UICONTROL 私密金鑰]**

      瀏覽並選取有效的私密金鑰 (`.p12`、`.key` 或 `.pen`)。

      >[!IMPORTANT]
      >如果您為&#x200B;**[!UICONTROL 私密金鑰]**&#x200B;輸入選取的檔案同時包含憑證，則您無需指定憑證。

   * **[!UICONTROL 憑證]**

      指定有效的憑證。只有當「**[!UICONTROL 私密金鑰]**」輸入&#x200B;**不含**&#x200B;憑證時才需要此選項。如需有關取得 SSL 憑證和私密金鑰的詳細資訊，請參閱[設定應用程式以使用 APNS 或 FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

   * Google

      **[!UICONTROL API 密鑰]**

      指定有效的 API 金鑰。如需有關取得 API 金鑰的詳細資訊，請參閱[設定應用程式以使用 APNS 或 FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

2. 按一下「**[!UICONTROL 儲存]**」。
