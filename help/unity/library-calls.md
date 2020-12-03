---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 對程式庫進行呼叫
solution: Experience Cloud
title: 對程式庫進行呼叫
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 30%

---


# 對程式庫進行呼叫{#making-calls-to-the-library}

當您想從指令碼呼叫外掛程式時，請匯入命名空間：

* **C#:** 使用 `com.adobe.mobile;`

匯入命名空間後，您可以透過ADBMobile類別的靜態方法直接對外掛程式進行呼叫。
