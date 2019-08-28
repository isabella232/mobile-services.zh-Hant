---
description: 狀態是您的應用程式中不同的畫面或檢視。
seo-description: 狀態是您的應用程式中不同的畫面或檢視。
seo-title: 追蹤應用程式狀態
solution: Marketing Cloud、Analytics
title: 追蹤應用程式狀態
topic: 開發人員和實施
uuid: 69c99d05-5816-4c86-97c5-d218 dc26 c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 追蹤應用程式狀態 {#track-app-states}

狀態是您的應用程式中不同的畫面或檢視。

每次在您的應用程式中顯示新狀態時 (例如，當使用者從首頁導覽至新聞摘要時)，都會傳送 `trackState` 呼叫。在 Android 中，通常每次載入新活動時都會呼叫 `trackState`。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 新增資料庫至您的專案與實施生命週期。

   如需詳細資訊，請參閱 *核心實作與生命週期* 中 [的新增SDK和設定檔案至IntelliJ IDEA或Eclipse專案](/help/android/getting-started/dev-qs.md)。

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 從 `onCreate` 函式中，呼叫 `trackState` 以傳送該狀態檢視的點擊。

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces, `View State` is reported as `Page Name`, and `state views` is reported as `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

內容資料值必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

狀態通常是透過路徑報表來檢視，所以您可以了解使用者如何導覽應用程式以及最常檢視哪些狀態。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 「檢視狀態」]報表。**&#x200B;此報表是根據使用者透過您的應用程式所採取的路徑而成。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 能夠檢視「頁面」之處皆可檢視狀態，例如:**「頁面」**&#x200B;報表、**[!UICONTROL 「頁面檢視」]**&#x200B;報表以及&#x200B;**「路徑」[!UICONTROL 報表。]** |
| Ad hoc analytics | 透過&#x200B;**「頁面」**&#x200B;維度、**[!UICONTROL 「頁面檢視」]**&#x200B;量度及&#x200B;**「路徑」[!UICONTROL 報表，就能在可以檢視「頁面」的任何地方來檢視狀態。]** |


