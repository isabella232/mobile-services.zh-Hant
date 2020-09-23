---
description: 「動作路徑」報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。
keywords: mobile
seo-description: 「動作路徑」報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。
seo-title: 動作路徑報表
solution: Experience Cloud,Analytics
title: 動作路徑報表
topic: Reports,Metrics
uuid: a21e5d9e-fd57-4178-9d64-87181b7f988b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 67%

---


# 動作路徑報表{#action-paths}

「動作路徑」報表可依據路徑分析顯示路徑圖表，用來代表使用者在應用程式中從某狀態轉換到另一個狀態所採行的路徑。

**[!UICONTROL 「檢視路徑」]**&#x200B;和&#x200B;**[!UICONTROL 「動作路徑」報表都是路徑分析報表。]****[!UICONTROL 「檢視路徑」]**&#x200B;報表可讓您查看使用者在您的應用程式中如何從一個畫面瀏覽至下一個畫面。**[!UICONTROL 「檢視動作」]**&#x200B;報表則可讓您查看使用者在您應用程式中執行的動作和事件 (如: 點擊、選取、重新調整大小等等) 順序。

>[!TIP]
>
>您可以使用漏斗報表將導覽和動作結合在一個報表中。如需詳細資訊，請參閱[漏斗](/help/using/usage/reports-funnel.md)。

![](assets/action_paths.png)

每個節點（形狀如方塊）代表使用者透過應用程式的路徑狀態。 例如，在上圖中，頂端節點代表啟動應用程式並從圖庫中挑選像片的使用者人數。

若要顯示可用來修改圖表的選項，請按一下節點，然後選取&#x200B;**[!UICONTROL 焦點]**&#x200B;或&#x200B;**[!UICONTROL 展開]**。例如，按一下頂端節點中的 **[!UICONTROL PhotoPicked]** 狀態後會顯示&#x200B;**[!UICONTROL 「焦點」]**&#x200B;和&#x200B;**[!UICONTROL 「展開」]**&#x200B;圖示。

![](assets/action_paths_icons.png)

To expand, click the **[!UICONTROL +]** icon. 此選項顯示進入或退出節點的其他路徑。 在下圖中，狀態1是啟動應用程式，狀態2是挑選像片（您先前展開的項目），狀態3包含使用者採取的不同路徑：

* 選擇項目
* 新增項目
* 拖曳項目
* 縮放項目

展開狀態類似於漏斗。

![動作路徑擴展](assets/action_paths_expand.png)

若要隔離節點，並顯示進入和離開所選節點的路徑，請按一下 ![焦點圖示](assets/icon_focus.png) 圖示。在下圖中，使用者在選取像片之前 **已完成** 下列路徑：

* 旋轉項目
* 縮放項目
* 拖曳項目
* 移除項目

在選取像片的使用者中，選取像片後 **完成** :

* 選擇項目
* 新增項目
* 拖曳項目
* 縮放項目

![動作路徑焦點](assets/action_paths_focus.png)

您可以集中或展開多個節點，以取得使用者在應用程式中所採取路徑的詳細檢視。 例如:

![動作多路徑](assets/action_paths_mult.png)

您可以為此報表配置下列選項:

* **[!UICONTROL 時段]**

   按一下&#x200B;**[!UICONTROL 「日曆」]**&#x200B;圖示以選取自訂時段，或從下拉式清單中選擇預設時段。

* **[!UICONTROL 自訂]**

   您可以透過變更&#x200B;**[!UICONTROL 「顯示方式」]**&#x200B;選項、新增量度和篩選器以及新增其他系列 (量度) 等方式來自訂報表. 如需詳細資訊，請參閱[自訂報表](/help/using/usage/reports-customize/reports-customize.md)。

* **[!UICONTROL 篩選]**

   按一下&#x200B;**[!UICONTROL 「篩選」]**&#x200B;可以建立跨越不同報表的篩選器，以查看在所有行動報表中的表現情形。嚴格篩選可讓您定義套用到所有非路徑報表的篩選器。如需詳細資訊，請參閱[新增嚴格篩選](/help/using/usage/reports-customize/t-sticky-filter.md)。

* **[!UICONTROL 下載]**

   按一下 **[!UICONTROL PDF]** 或 **[!UICONTROL CSV]** 可下載或開啟文件，以及分享給無法存取 Mobile Services 的使用者，或是在簡報中使用檔案。