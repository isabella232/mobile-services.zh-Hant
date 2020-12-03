---
description: 「檢視路徑」報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。
keywords: mobile
seo-description: 「檢視路徑」報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。
seo-title: 檢視路徑報表
solution: Experience Cloud,Analytics
title: 檢視路徑報表
topic: Reports,Metrics
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 100%

---


# 檢視路徑報表 {#view-paths}

**[!UICONTROL 「檢視路徑」]**&#x200B;報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。

>[!TIP]
>
>**[!UICONTROL 檢視路徑]**&#x200B;和&#x200B;**[!UICONTROL 檢視動作]**&#x200B;報表相當類似，這兩者都屬於路徑報表。**[!UICONTROL 「檢視路徑」]**&#x200B;報表可讓您查看使用者在您的應用程式中如何從一個畫面瀏覽至下一個畫面，而&#x200B;**[!UICONTROL 「檢視動作」]**&#x200B;報表則可顯示使用者在應用程式中的動作 (包括: 點擊、選取、重新調整大小等事件) 執行順序。您可以使用漏斗報表將導覽和動作結合在一個報表中。如需詳細資訊，請參閱[漏斗](/help/using/usage/reports-funnel.md)。

![檢視路徑](assets/view_paths.png)

每個節點 (形狀像方塊) 代表使用者在應用程式中通過路徑的一個狀態。例如，在上圖中，頂端節點代表啟動應用程式後接著瀏覽至主檢視頁面的使用者人數。

如要取得其他可用來修改圖表的選項，按一下節點，其他選項 (如:**[!UICONTROL 「焦點」]**&#x200B;或&#x200B;**[!UICONTROL 「展開」]**) 就會顯示。例如，如果您按一下頂端節點中的&#x200B;**[!UICONTROL 「MainView」]**&#x200B;狀態，就會顯示&#x200B;**[!UICONTROL 「焦點」]**&#x200B;和&#x200B;**[!UICONTROL 「展開」]**&#x200B;圖示。

若要展開檢視，按一下&#x200B;**[!UICONTROL 「+」]**&#x200B;圖示即可顯示進入或離開節點的其他路徑。在上圖中，狀態 1 代表正在啟動應用程式，狀態 2 代表正在檢視應用程式的主檢視頁面，而狀態 3 則包含使用者瀏覽的路徑如下：

* 瀏覽至相機膠卷
* 瀏覽至項目選取器
* 瀏覽至相機
* 瀏覽至項目資訊頁面

![](assets/view_paths_expand.png)

按一下![焦點圖示](assets/icon_focus.png)可隔離節點，只顯示進入或離開所選節點的路徑。在下圖中，使用者檢視應用程式主畫面之前先瀏覽過下列路徑：

* 項目資訊
* 項目選取器
* 相機膠卷
* 相機

![檢視路徑 (聚焦)](assets/view_paths_focus.png)

您可以聚焦或展開多個節點，詳細檢視使用者在您應用程式中選擇的路徑。例如:

![檢視路徑 (多個)](assets/view_paths_mult.png)

您可以為此報表配置下列選項:

* **[!UICONTROL 時段]**
按一下**[!UICONTROL 日曆]**&#x200B;圖示以選取自訂時段，或從下拉式清單中選擇預設時段。
* **[!UICONTROL 自訂]**
您可以透過變更**[!UICONTROL 顯示方式]**&#x200B;選項、新增量度和篩選器以及新增其他系列 (量度) 等方式來自訂報表。如需詳細資訊，請參閱[自訂報表](/help/using/usage/reports-customize/reports-customize.md)。
* **[!UICONTROL 篩選]**
按一下**[!UICONTROL 篩選]**&#x200B;可以建立跨越不同報表的篩選器，以查看某個區段在所有行動報表中的表現。嚴格篩選可讓您定義套用到所有非路徑報表的篩選器。如需詳細資訊，請參閱[新增嚴格篩選](/help/using/usage/reports-customize/t-sticky-filter.md)。
* **[!UICONTROL 下載]**
按一下 **[!UICONTROL PDF]** 或 **[!UICONTROL CSV]** 可下載或開啟文件，以及分享給無法存取 Mobile Services 的使用者，或是在簡報中使用檔案。