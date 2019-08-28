---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 對程式庫進行呼叫
solution: Marketing Cloud，開發人員
title: 對程式庫進行呼叫
uuid: 74c30379-1cdf-4318-9db8-e14 fb63 aa18 a
translation-type: tm+mt
source-git-commit: 7cb277652eaeedff7253a4f3c42208ceaf78acb7

---


# Making calls to the library{#making-calls-to-the-library}

當您想要從指令碼對外掛程式進行呼叫時，請匯入命名空間：

* **C#:** 使用 `com.adobe.mobile;`

* **JavaScript:** 匯入 `com.adobe.mobile;`

* **boo:** 匯入 `com.adobe.mobile;`

匯入命名空間後，您可以透過ADBMobile類別的靜態方法直接對外掛程式進行呼叫。
