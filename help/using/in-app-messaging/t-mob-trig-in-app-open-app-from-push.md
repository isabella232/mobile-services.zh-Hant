---
description: 您可以將應用程式內訊息觸發器設為使用者從推送訊息開啟應用程式時系統傳送的推送訊息 ID。
title: 從推送訊息開啟應用程式時觸發應用程式內訊息
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
exl-id: 4496222f-b6f0-4fa1-86c6-149b590244d3
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 58%

---

# 從推送訊息開啟應用程式時觸發應用程式內訊息{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

{#eol}

您可以將應用程式內訊息觸發器設為使用者從推送訊息開啟應用程式時系統傳送的推送訊息 ID。

1. 取得推送訊息的推送訊息 ID，系統會將該 ID 傳送給使用者。

   您可以在訊息建立工作流程期間的URL中找到推送訊息ID。

   其範例如下:

   ![](assets/brandon_task1.png)

1. 使用下列觸發器儲存並啟動應用程式內訊息:

   `"a.push.payloadID" =`

   >[!TIP]
   >
   >推送訊息 ID 是您在步驟 1 找到的 ID。

   由於&#x200B;**[!UICONTROL 觸發器]**&#x200B;下拉式清單沒有此觸發器，因此您必須手動新增。

   ![](assets/brandon_task2.png)

1. 儲存並傳送推送訊息，該訊息具有您在步驟 1 找到的推送 ID。
1. 點進推送訊息以開啟應用程式，並確認應用程式會在開啟時顯示應用程式內訊息。

   在測試時，請記住以下資訊：

   * 儲存應用程式內訊息後，托管的設定檔案需要約45秒才會以新訊息更新。
   * 當有 **new** 啟動，因此您必須確保在按一下推送訊息時，應用程式會觸發新的啟動。
   這通常表示您必須確保已發生工作階段逾時。 預設逾時為5分鐘。
