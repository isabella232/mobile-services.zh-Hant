---
description: 狀態是您的應用程式中不同的畫面或檢視。每次在您的應用程式中顯示新狀態時，例如，當使用者從首頁導覽至新聞摘要時，您應該傳送追蹤狀態呼叫。在 iOS 中，通常是使用各個檢視的 viewDidLoad 方法追蹤狀態。
seo-description: 狀態是您的應用程式中不同的畫面或檢視。每次在您的應用程式中顯示新狀態時，例如，當使用者從首頁導覽至新聞摘要時，您應該傳送追蹤狀態呼叫。在 iOS 中，通常是使用各個檢視的 viewDidLoad 方法追蹤狀態。
seo-title: 追蹤應用程式狀態
solution: Marketing Cloud,Analytics
title: 追蹤應用程式狀態
topic: 開發人員和實施
uuid: 12cca4eb-1f15-4cec-a58f-76b69eaff99d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 追蹤應用程式狀態 {#track-app-states}

狀態是您的應用程式中不同的畫面或檢視。每次在您的應用程式中顯示新狀態時，例如，當使用者從首頁導覽至新聞摘要時，您應該傳送追蹤狀態呼叫。在 iOS 中，通常是使用各個檢視的 viewDidLoad 方法追蹤狀態。

>[!TIP]
>
>To track states, make a call to `trackState`. 系統不會自動追蹤狀態。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 新增資料庫至您的專案與實施生命週期。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. 匯入程式庫.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 呼叫 `trackState` 以傳送該狀態檢視的點擊。

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In Adobe Mobile services, the **[!UICONTROL State Name]** is reported in the *`View State`* variable, and a view is recorded for each `trackState` call. 在其他 Analytics 介面中，**[!UICONTROL View State]** 會回報為 **[!UICONTROL Page Name]**，而 state views 會回報為 page views。

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

Context data values must be mapped to custom variables:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

狀態通常是透過路徑報表來檢視，所以您可以了解使用者如何導覽應用程式以及最常檢視哪些狀態。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 「檢視狀態」]報表。**&#x200B;此報表是根據使用者透過您的應用程式所採取的路徑而成。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 能夠檢視「頁面」之處皆可檢視狀態，例如:**「頁面」**&#x200B;報表、**[!UICONTROL 「頁面檢視」]**&#x200B;報表以及&#x200B;**「路徑」[!UICONTROL 報表。]** |
| Ad hoc analytics | 透過&#x200B;**「頁面」**&#x200B;維度、**[!UICONTROL 「頁面檢視」]**&#x200B;量度及&#x200B;**「路徑」[!UICONTROL 報表，就能在可以檢視「頁面」的任何地方來檢視狀態。]** |
