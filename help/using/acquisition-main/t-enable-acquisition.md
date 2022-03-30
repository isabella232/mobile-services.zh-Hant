---
description: 必須先在 SDK 設定中啟用贏取追蹤，才可追蹤及報告行銷連結。
keywords: 行動
solution: Experience Cloud Services,Analytics
title: 配置贏取
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# 配置贏取 {#configure-acquisition}

必須先在 SDK 設定中啟用贏取追蹤，才可追蹤及報告行銷連結。

1. 在應用程式的「管理應用程式設定」頁面中，捲動至&#x200B;**[!UICONTROL 「SDK 贏取選項」]**&#x200B;區段。
1. 完成下列作業：

   * 若要啟用贏取，請選取&#x200B;**[!UICONTROL 啟用]**&#x200B;核取方塊。

      如果選取此核取方塊，**[!UICONTROL 反向連結逾時]**&#x200B;欄位就會變成使用中，而值將從 0 變更為 5。

   * 在&#x200B;**[!UICONTROL 反向連結逾時 (秒)]**&#x200B;欄位中輸入值

      (**選擇性**) 若您啟用了&#x200B;**[!UICONTROL 啟用]**&#x200B;核取方塊，此欄位為選擇性欄位。您可以變更逾時值 (以秒為單位)。此設定會指定在傳送「首次啟動」點擊前，等候贏取資訊的時間長度。
   >[!IMPORTANT]
   >您輸入的值不得為零。如果您啟用了贏取，但將值保留為零，則該贏取連結將不會運作。建議您使用 5 秒預設值。

1. 下載並在應用程式中使用新的 SDK 設定檔案。

   您已成功配置 **iOS** 贏取選項。若要在 **Android** 上啟用贏取，請完成[追蹤行動贏取](/help/android/acquisition-main/acquisition.md)中的步驟。
