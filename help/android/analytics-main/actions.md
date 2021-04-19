---
description: 動作為發生在您要測量之 Android 應用程式中的事件。
seo-description: 動作為發生在您要測量之 Android 應用程式中的事件。
seo-title: 追蹤應用程式動作
solution: Experience Cloud,Analytics
title: 追蹤應用程式動作
topic-fix: Developer and implementation
uuid: fe01c1df-f6bb-4b32-b3ef-959d2c724af6
exl-id: 495a6aa8-781d-4499-ad46-e19d57cccf40
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 100%

---

# 追蹤應用程式動作 {#track-app-actions}

動作為發生在您要測量之 Android 應用程式中的事件。

每個動作有一或多個對應量度，會隨著每次事件發生而增量。例如，您可能會針對每個新訂閱、每次檢視文章或每次完成某個層級時，傳送 `trackAction` 呼叫。應用程式不會自動追蹤動作，因次您必須在要追蹤的事件發生時呼叫 `trackAction`，然後將動作對應至自訂事件。

## 追蹤動作 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱[核心實作與生命週期](/help/android/getting-started/dev-qs.md)中的&#x200B;*新增 SDK 和設定檔至您的 IntelliJ IDEA 或 Eclipse 專案*。

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 當您要追蹤的動作在應用程式中發生時，請針對此動作呼叫 `trackAction` 以傳送點擊:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. 在 Adobe Mobile Services 使用者介面中，選取您的應用程式並按一下&#x200B;**[!UICONTROL 管理應用程式設定]**。
1. 按一下&#x200B;**[!UICONTROL 「管理變數和衡量指標」]**，然後按一下&#x200B;**[!UICONTROL 「自訂量度」]**&#x200B;標籤。

1. 將程式碼中定義的內容資料名稱 (例如，`myapp.ActionName`) 對應至某個自訂事件。

   ![](assets/map-event-context-data.png)

您也可以對應具有如&#x200B;**[!UICONTROL 自訂動作]**&#x200B;之類名稱的自訂屬性，並將值設為 `a.action`，藉此設定屬性以保留所有動作值。

![](assets/map-custom-prop.png)

## 傳送其他資料 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了動作名稱之外，您還可以隨著每次追蹤動作呼叫傳送其他內容資料:

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

內容資料值必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-context-action.png)

## 動作報表 {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| 介面 | 報表 |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 動作路徑]**&#x200B;報表。檢視動作於應用程式中發生的順序。您也可以按一下任一報表上的&#x200B;**[!UICONTROL 「自訂」]**，以檢視動作的排名、趨勢或在劃分報表中的情況，或套用篩選條件以檢視特定區段的動作。 |
| Marketing Reports &amp; Analytics | **[!UICONTROL 「自訂事件」]**&#x200B;報表。當動作對應至自訂事件後，您可以檢視與所有其他 Analytics 事件類似的行動事件。 |
| Ad hoc analytics | **[!UICONTROL 「自訂事件」]**&#x200B;報表。當動作對應至自訂事件後，您可以檢視與所有其他 Analytics 事件類似的行動事件。 |
