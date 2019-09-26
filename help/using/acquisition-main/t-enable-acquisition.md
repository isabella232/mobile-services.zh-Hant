---
description: 您必須在SDK設定中啟用贏取追蹤，才能追蹤並報告行銷連結。
keywords: 行動
seo-description: 您必須在SDK設定中啟用贏取追蹤，才能追蹤並報告行銷連結。
seo-title: 配置贏取
solution: Marketing Cloud,Analytics
title: 配置贏取
topic: 量度
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 配置贏取 {#configure-acquisition}

您必須在SDK設定中啟用贏取追蹤，才能追蹤並報告行銷連結。

1. 在應用程式的「管理應用程式設定」頁面中，捲動至&#x200B;**[!UICONTROL 「SDK 贏取選項」]**&#x200B;區段。
1. 完成下列作業:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * 在「反向連結逾時( **[!UICONTROL 秒)」欄位中輸入值]**

      (**Optional**) If you enabled the **[!UICONTROL Enable]** check box, this field is optional. 您可以變更逾時值 (以秒為單位)。This setting specifies the period to wait for Acquisition information before sending the First Launch hit.
   >[!IMPORTANT]
   >您必須輸入非零值。 If you enable Acquisition but leave the value as zero, Acquisition links will not function. We recommend that you use the 5-second default value.

1. 下載並在應用程式中使用新的 SDK 設定檔案。

   您已成功配置 **iOS** 贏取選項。To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
