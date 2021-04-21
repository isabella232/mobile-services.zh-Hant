---
description: 從指令碼呼叫程式庫外掛程式。
keywords: Unity
solution: Experience Cloud
title: 對程式庫進行呼叫
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
exl-id: de95edd5-3a5b-4b84-aeea-adff3362f544
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 18%

---

# 對程式庫進行呼叫{#making-calls-to-the-library}

當您想從指令碼呼叫外掛程式時，請匯入命名空間：

* **C#：使** 用  `com.adobe.mobile;`

匯入命名空間後，您可以透過ADBMobile類別的靜態方法直接對外掛程式進行呼叫。
